---
title: Organisation par tag
description: 
published: true
date: 2024-05-15T10:48:14.735Z
tags: 
editor: markdown
dateCreated: 2024-05-15T10:35:21.573Z
---

# Organisation par tag

## Régles

- ISO8601 : <https://en.wikipedia.org/wiki/ISO_8601>


- <https://karl-voit.at/managing-digital-photographs/>
	- <https://karl-voit.at/demo-filetags-intro/>

- <https://github.com/novoid/filetags/>

```txt
… filetags example demonstrating: controlled vocabulary file ~/.filetags, tagging multiple files at once, removing tags by prepending a minus character, tagging using the proposed number shortcuts, tab completion of tags via Tab, and mutually exclusive tags (switching from draft to final without removing draft).

This Python script adds or removes tags to file names in the following form:

    “file without time stamp in name -​- tag2.txt”
    “file name with several tags -​- tag1 tag2.jpeg”
    “another example file name with multiple example tags -​- fun videos kids.mpeg”
    “2013-05-09 a file name with ISO date stamp in name -​- tag1.jpg”
    “2013-05-09T16.17 file name with time stamp -​- tag3.csv”

The script accepts an arbitrary number of files (see your shell for possible length limitations).

    Target group: users who are able to use command line tools and who are using tags in file names.
    Hosted on github: https://github.com/novoid/filetags
    Note that “directories” are to “folders” what “files” are to “documents”.
```

```txt
Besides the fact that I am using ISO dates and times in file names (as shown in examples above), I am using tags with file names. To separate tags from the file name, I am using the separator “space dash dash space”.

For people familiar with Regular Expressions:

(<ISO date/time stamp>)?(?<descriptive file name>)?( -- <list of tags separated by spaces>)?.<file extension>

Tagging files this way requires a file renaming process. Adding (or removing) tag(s) to a set of file results in multiple renaming processes. Despite advanced renaming tools like vidir (from moreutils) it’s handy to have a tool that makes adding and removing tags as simple as possible.

You may like to add this tool to your image or file manager of choice. I added mine to geeqie which is my favorite image viewer on GNU/Linux.
```

- <https://redlib.freedit.eu/r/ObsidianMD/comments/18wy4ba/best_way_to_organize_tags_if_you_have_hundreds_of/>

```txt
Tags

are semantic 'attributes' of information AND you cannot recover information in a database if you do not know the attributes of that information. Besides, two different notes ---or texts or whatever--- stored in very different folders may still share the same tags. SO many notes ENTAILS having many tags but not necessarily many folders. SOOO... you can have a vertical, hierarchical classification of folders fine-tuned semantically and 'horizontally' with tags. And to be precise on fine-tuning it, you will need hundreds of tags. BUT...
TAGS SHOULD BE SYSTEMATIZED

in a CONTROLLED VOCABULARY in a Note file of its own to avoid duplication of tagging or ambiguity or errors in tagging.

Even if that implies continuously, bit by bit, building lists of synonymical 'strings' and determining their correspondent final tags. That way you do not duplicate tags.

Because of the problem of knowing how to write those tags [ if you should write in all-capitals or tittle-case or CamelCase or no capitals at all ... ] you should decide which way you will go and stick to it --- to avoid sudo-duplicates of tags (hardDisks, HardDisks, HARDDISKS, harddisks, hard_disks, hard-disks or even hard.disks...)
I use this rule:

With composed names use ALWAYS CamelCase and Decide on a strategy for Naming Gender and Number variations of the named entities.

Should be:
with proper names ALWAYS Capital Camel Case:

-- WinstonChurchill -- TomBrady -- MotherTheresa -- PopeFrancis -- SigourneyWeaver -- FederativeRepublicOfBrazil -- OlympicGames -- BlackPanthers -- MedievalHistory -- PythonFunctions
Use the 'minus' sign ( - ) to separate Acronyms inside expressions:

-- CSS-classes -- NATO-treaty -- inside-FBI-trading -- expanded-HTML
With composed common names and expressions ALWAYS small first-letter Camel Case:

-- zebra

but

-- maleZebra -- eastAfricanZebra

(Note: biological species should be written in singular form):

-- swordFish -- blueWhale -- snowTiger
But other categories should have Tags in the plural form

-- hardDisks -- penDrives -- motorcycleRaces -- weekEnds -- weekEndsAndHolidays
Also Expressions

-- whiteChristmas -- allRoadsLeadToRome -- winnerTakesAll

I hope that helps you understand we live in a profoundly Tagged Informational World today from which we cannot escape BUT that we can Tame...
```