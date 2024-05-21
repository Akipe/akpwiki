---
title: Serveur GNU/Linux
description: 
published: true
date: 2024-05-21T19:13:45.251Z
tags: 
editor: markdown
dateCreated: 2024-05-21T19:13:45.251Z
---

# Serveur GNU/Linux

## CPU

### Governor

Get description of differents governors : <https://www.kernel.org/doc/html/latest/admin-guide/pm/cpufreq.html?#generic-scaling-governors>

Get current :

```bash
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor

# For Intel Hardware P-state
cat /sys/devices/system/cpu/cpufreq/policy?/energy_performance_available_preferences
```

Watch CPU frequency live :

```bash
watch -n 0.5 "lscpu | grep MHz"
watch -n 0.5 cat /sys/devices/system/cpu/cpu[0-9]*/cpufreq/scaling_cur_freq
```

Set governor (don't save) :

```bash
echo "conservative" | tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
```

Persist setting governor :

- with crontab

```bash
crontab -e
# next write in crontab :
@reboot echo "conservative" | tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
```

#### threshold

```bash
cat /sys/devices/system/cpu/cpufreq/<governor>//{up_threshold,down_threshold}
echo -n percent > /sys/devices/system/cpu/cpufreq/<governor>/up_threshold
echo -n percent > /sys/devices/system/cpu/cpufreq/<governor>/down_threshold

cat /sys/devices/system/cpu/cpufreq/conservative/{up_threshold,down_threshold}
echo -n percent > /sys/devices/system/cpu/cpufreq/conservative/up_threshold
echo -n percent > /sys/devices/system/cpu/cpufreq/conservative/down_threshold
```

```ini
# /etc/tmpfiles.d/conservative.conf
w- /sys/devices/system/cpu/cpufreq/conservative/up_threshold - - - - 80
w- /sys/devices/system/cpu/cpufreq/conservative/down_threshold - - - - 20
```

```bash
crontab -e
# next write in crontab :
@reboot echo -n 80 | tee /sys/devices/system/cpu/cpufreq/conservative/up_threshold
@reboot echo -n 20 | tee /sys/devices/system/cpu/cpufreq/conservative/down_threshold
```

#### Sampling rate

```bash
# sampling_down_factor : 1 to 100000
cat /sys/devices/system/cpu/cpufreq/<governor>/sampling_down_factor
echo -n value > /sys/devices/system/cpu/cpufreq/<governor>/sampling_down_factor

cat /sys/devices/system/cpu/cpufreq/conservative/sampling_down_factor
echo -n value > /sys/devices/system/cpu/cpufreq/conservative/sampling_down_factor
```

```ini
# /etc/tmpfiles.d/conservative.conf
w- /sys/devices/system/cpu/cpufreq/conservative/sampling_down_factor - - - - 1
```

```bash
crontab -e
# next write in crontab :
@reboot echo -n 1 | tee /sys/devices/system/cpu/cpufreq/conservative/sampling_down_factor
```

### Clock speed & voltage

#### Ryzen
- amdctl <https://github.com/kevinlekiller/amdctl/>

vim /etc/modules-load.d/msr.conf:

```
msr
```

vim /etc/default/grub:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet msr.allow_writes=on"
```

```bash
# Get commands
./amdctl -h

# -v    Set CPU voltage id (vid).
# -d    Set the CPU divisor id (did).
# -f    Set the CPU frequency id (fid).

# Get informations
./amdctl -m -g

# Change frequence for P-State 2
./amdctl -m -p2 -f110 -v108 -d13
```

### Intel performance and energy bias hint

Check if supported :

```bash
cat /sys/devices/system/cpu/cpu[[:digit:]]*/power/energy_perf_bias
```

Values :

|EPB value | String 
|---|---
| 0 | performance
| 4 | balance-performance
| 6 | normal, default
| 8 | balance-power
| 15 | power 

Set via sysfs :

```bash
echo epb | tee /sys/devices/system/cpu/cpu[[:digit:]]/power/energy_perf_bias
echo 10 | tee /sys/devices/system/cpu/cpu[[:digit:]]/power/energy_perf_bias
echo "balance-power" | tee /sys/devices/system/cpu/cpu[[:digit:]]/power/energy_perf_bias
```

Set via contrab :

```bash
crontab -e
```

```ini
@reboot echo epb | tee /sys/devices/system/cpu/cpu[[:digit:]]/power/energy_perf_bias
@reboot echo 10 | tee /sys/devices/system/cpu/cpu[[:digit:]]/power/energy_perf_bias
```

## Watchdog

/etc/sysctl.d/disable_watchdog.conf:

```
kernel.nmi_watchdog = 0
```

## Audio

```bash
echo 1 > /sys/module/snd_hda_intel/parameters/power_save
echo Y > /sys/module/snd_hda_intel/parameters/power_save_controller
```

`/etc/modprobe.d/audio_powersave.conf` :

```ini
# Intel soundcards
options snd_hda_intel power_save=1
# ac97 soundcards
options snd_ac97_codec power_save=1
```

## Bus power management (ASPM)

Verify support :

```bash
lspci -vv | grep 'ASPM.*abled;'
```

For forcing enable ASPM, you need to enable `pcie_aspm=force` to kernel parameter :

/etc/default/grub :

```ini
GRUB_CMDLINE_LINUX_DEFAULT="quiet pcie_aspm=force"
```

```bash
grub-mkconfig -o /boot/grub/grub.cfg
```

Set parameter :

```bash
cat /sys/module/pcie_aspm/parameters/policy # Get current config
echo powersave > /sys/module/pcie_aspm/parameters/policy # Set config
```

Persist setting :

- with crontab

```bash
crontab -e
# next write in crontab :
@reboot echo "powersave" | tee /sys/module/pcie_aspm/parameters/policy 
```

## PCI Runtime Power Management

/etc/udev/rules.d/50-pci_pm.rules:

```
SUBSYSTEM=="pci", ATTR{power/control}="auto"
```

## USB autosuspend

/etc/udev/rules.d/50-usb_power_save.rules:

```
ACTION=="add", SUBSYSTEM=="usb", TEST=="power/control", ATTR{power/control}="auto"
```

## SATA Active Link Power Management

```bash
cat /sys/class/scsi_host/host*/link_power_management_policy
```

`/etc/udev/rules.d/hd_power_save.rules`:

```ini
# For Intel motherboards
ACTION=="add", SUBSYSTEM=="scsi_host", KERNEL=="host*", ATTR{link_power_management_policy}="med_power_with_dipm"
# For others
ACTION=="add", SUBSYSTEM=="scsi_host", KERNEL=="host*", ATTR{link_power_management_policy}="medium_power"
```

```bash
crontab -e
# next write in crontab :
@reboot echo "med_power_with_dipm" | tee /sys/class/scsi_host/host*/link_power_management_policy

@reboot echo "medium_power" | tee /sys/class/scsi_host/host*/link_power_management_policy
```

## Disk power management (Hdparm)

## GPU

### ATI Radeon

```bash
echo profile > /sys/class/drm/card0/device/power_method
echo low > /sys/class/drm/card0/device/power_profile
```

## Screen

Set automatic power down screen :

```bash
# After 1 minute
setterm -blank 1
```

Persist setting :

- kernel parameter

```bash
# /etc/default/grub
# consoleblank uses seconds
GRUB_CMDLINE_LINUX_DEFAULT="quiet consoleblank=60"
```

```bash
update-grub
```

```bash
setterm -powerdown 1		# Turn off the screen
setterm -blank 10           # Blank the screen in 10 minutes
setterm -powersave on       # Put the monitor into VESA power saving mode
setterm -powerdown 20       # Set the VESA powerdown to 20 minutes
```

## Tools

### TLP

### Powertop

### ThermalD

Install `thermald`.

if : `systemctl status thermald.service`

```
thermald[100523]: NO RAPL sysfs present
thermald[100523]:  Need Linux PowerCap sysfs
thermald[100523]: Unsupported cpu model or platform
```

### Throttled

### intel-undervolt

## Links

- <https://wiki.archlinux.org/title/Power_management>
- <https://wiki.archlinux.org/title/Hdparm#Power_management_configuration>