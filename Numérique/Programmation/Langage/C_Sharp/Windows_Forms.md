---
title: Windows Forms
description: 
published: true
date: 2024-05-21T14:59:40.752Z
tags: 
editor: markdown
dateCreated: 2024-05-21T14:59:40.752Z
---

## l'API

```c#
using System.Text.RegularExpressions;

namespace Correction_03_InputControl
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
			// On laisse le constructeur vide pour être sur que tout est bien initialisé
            // Il est préférable d'utilisé l'événement "Load" du formulaire : Form1_Load
        }
                private void Form1_Load(object sender, EventArgs e)
        {
            regexControl = new Regex("");
        }

        private Regex regexControl { get; set; }
    }
}
```

### Différents types de visuel

#### Data sources

```c#
lbxList = new List<string>() { "Test" };
lbxControl.DataSource = lbxList;

// Liste avec mise à jour automatique de l'UI
BindingList<string> list = new BindingList<string>;

// Mise à jour avec liste classique
maList = new List<int> { 0, 1, 2, 3, 8 };
cbxSource.DataSource = maList; // On connecte la liste à un control
maList.Add(12);// Ensuite on réalise des modifications sur la liste
// On est obliger de supprimer
// et de réajouter la relation entre la liste et le control
cbxSource.DataSource = null;
cbxSource.DataSource = maList;
```

#### Control

Tous les éléments d'une page sont des controles.

Ils partagent tous certaines propriétes comme les tags.

```c#
Control scrollBar = sender as Control;
scrollbar.Tag = "test";
```

#### Scrollbar

Pour définir le maximum : `Valeur max + LargeChange - 1`

#### SplitContainer

#### ListBox

#### Panel

#### TextBox

#### ListBox

```c#
listBox.Items // L'ensemble des éléments de la liste

//Vérifier si un élément est selectionné
if (comboBox.SelectedIndex > -1)
{
  comboBox.Items.RemoveAt(comboBox.SelectedIndex);
}
```

#### ComboBox

Vérifier si un élément est selectionné :

```c#
if (comboBox.SelectedIndex > -1)
{
  comboBox.Items.RemoveAt(comboBox.SelectedIndex);
}
```

#### MessageBox

```c#
MessageBox.Show(/* Texte de la fenêtre */, /* Titre de la fenêtre */, /* type de bouton à afficher (enumération MessageBoxButtons)*/, /* icone (enumeration MessageBoxIcon));
```

#### Gérer des groupes

- **Panel**
- **GroupBox**
- **FlowLayoutPanel** : gérer les control enfants comme sur une page web
- **TableLayoutPanel** : gére les controls enfants dans un tableau
- **SplitContainer** : divise l'espace en 2
- **TabControl** : système d'onglets avec une collection de **Tabpage**.
lors d'un changement d'onglets, voici les événements executé : *Deselecting > Deselected > Selecting > Selected*

#### Barre d'outils et d'état

- **ContextMenuStrip** Menu contextuelle
- **ToolStrip** Barre d'outils
- **MenuStrip**
- **StatusStrip**

Le menu stocke les éléments dans une collection d'Items, et les sous menu dans une collection DropDownItems.

##### Menu contextuelle *ContextMenuStrip*

- **ContextMenuStrip**, surtout en haut
```c#
private void Exemple3_MouseDown(object sender, MouseEventArgs e)
{
	contextMenuCouleur.Show(this,new Point(e.X,e.Y));}
}
```

Pour modifier facilement les sous menu : cliquer à droite du `DropDownItems`

##### Barre d'outils *TOOLSTRIP*

##### StatusStrip

- **STATUSSTRIP**, surtout en bas

### Affichier plusieurs feuille dans une application

- "Ajouter un formulaire Windows" sur l'application dans la fenêtre explorateur du projet.

Les fenêtre peuvent être modales (fenêtre qui est en avant et doit être fermé pour reprendre le controle de la feuilel mère) ou non modales (pouvant fonctionner en parallèle).
Les affichages modales sont généralement utilisées comme boite de dialogue.

Création d'une fenêtre :

```c#
public partial class Form2 : Form
{
  public Form2()
  {
      InitializeComponent();
  }
  ...
}
```

Affichage d'une fenêtre en forme modale :

```c#
private void btnOuvrir_Click(object sender, EventArgs e)
{
  Form2 frmDeux = new Form2(); // Notre fenêtre créer précédament
  frmDeux.ShowDialog();
}
```

Affichage d'une fenêtre en forme non modale :

```c#
public partial class Form1 : Form
{
  public Form1()
  {
  	InitializeComponent();
  }
  Form2 frmDeux;
  private void btnOuvrir_Click(object sender, EventArgs e)
  {
    frmDeux = new Form2();
    frmDeux.Show();
  }
  private void btnFermer_Click(object sender, EventArgs e)
  {
  	frmDeux.Close();
  }
}
```

### Feuilles MDI
Il y aura une feuille principale appelé *feuille MDI* et des feuilles documents ou filles, qui seront non modales.

#### Créer feuille MDI

1. Créer un projet
1. Propriété **IsMdiContainer** = true (recommandé : WindowsState à Maximized)
1. Ajouter **MenuStrip**
1. Propriété **MdiWindowListItem** du composant **MenuStrip**, le nom dy meny dans lequel Windows se chargera de gérer la liste des fenêtres actives.
1. Ajouter une nouvelle feuille dans le projet pour les enfants

#### Evenement pour ajouter une feuille fille

```c#
private void mnuNouveau_Click(object sender, System.EventArgs e)
{
  frmEnfant newfeuille = new frmEnfant();
  newfeuille.MdiParent = this;
  newfeuille.Show();
}
```

#### Methode LayoutMdi

Va gérer la disposition des feuilles enfants :

- ArrangeIcons : icones réarrangées dans l'espace parent
- Cascade : en cascade
- TileHorizontal : en bandes horizontales
- TileVertical : en bandes verticales

```c#
private void mnuCascade_Click(object sender, System.EventArgs e)
{
	this.LayoutMdi(MdiLayout.Cascade);
}
```

### Afficher une fenêtre

### Les événements (ou actions)

- `TextChange`
- `Load` (pour le form)

#### Ajouter un événement à un control

```c#
Control monControl;
// monControl.NomEvenement += MaMethodeLierAEvenement
monControl.Scroll += ColorValueChanged;
monControl.ValueChanged += ColorValueChanged;

// On peut également retirer les événements
monControl.Scroll -= ColorValueChanged;
```

### Gestion des erreurs (ErrorProvider)

```c#
public partial class Form1 : Form
{
    private ErrorProvider errorProvider;

    public Form1()
    {
        InitializeComponent();
    }

    private void Form1_Load(object sender, EventArgs e)
    {
    	// On créer notre gestionnaire d'erreur
        errorProvider = new ErrorProvider();
    }

    private void BValidate_Click(object sender, EventArgs e)
    {
        if (!IsNameValid())
        {
        	// On lance notre erreur
            errorProvider.SetError(TbName, "Le nom n'est pas valide");
        }
        else
        {
        	// On retire notre erreur
            errorProvider.SetError(TbName, String.Empty);
            MessageBox.Show("Erreur dans la saisie", "Erreur");
        }
    }
}

```

### Les raccourcies clavier

Pour attribuer un raccourcie clavier aux menus et sous menus, il faut précéder le texte du caractère **&**.

### Binding liste avec ListBox

### Gérer les Mask

<https://www.c-sharpcorner.com/uploadfile/mahesh/maskedtextbox-in-C-Sharp/>

### Gérer le focus

```c#
MonControl.Focus();
```

### Débug

```c#
using System.Diagnostics;

Debug.WriteLine("message");
```

### User control

Permet de créer des composant de control dans Winform réutilisatble.
Ils ont leur propres événements, control, et code. Lors de l'importation, on importe également tout les événement et le reste.

Add item : control

Attention : pour mettre à jour dans le form qui l'utilise, il faut rebuild l'ensemble du projet.

Dans le form qui l'utilise, lors de l'import, il dispose d'une taille défini, si on agrandit après coup notre user control, il faudra modifier sa taille également dans la form qui l'utilise.

## Timer

```c#
System.Windows.Forms.Timer myTimer = new System.Windows.Forms.Timer();
myTimer.Enabled = true;
myTimer.Tick += new EventHandler(TimerEventAction);
myTimer.Interval = 5000;
myTimer.Start();
myTimer.Stop();

private void TimerEventAction(Object sender, EventArgs e) {
  // ...
}
```

### WinForm : OpenFileDialog

- `System.Windows.Forms.OpenFileDialog` : selection de fichier
- `FolderBrowserDialog` : selection de dossier

```c#
OpenFileDialog monFichier = new OpenFileDialog();
monFichier.Multiselect = true; // Pour autorisé ou non la selection de plusieurs fichiers
monFichier.Filter = "Images (*.BMP;*.JPG;*.GIF)|*.BMP;*.JPG;*.GIF|" + "All files (*.*)|*.*";
DialogResult resultat = monFichier.ShowDialog();
string cheminDuFichier = monFichier.FileName;
```

```c#
FolderBrowserDialog openFolder = new FolderBrowserDialog();

if (openFolder.ShowDialog() == DialogResult.OK)
{
  string dirPath = openFolder.SelectedPath;
}
```

## Gestion multi taches

```c#
// Threads non asynchrone,
// l'interface est bloqué pendant 5 seconds
private void button1_Click(object sender, EventArgs e)
{
  txtResult.Text += "Yeah ";
  Thread.Sleep(5000);
}

private void timer1_Tick_1(object sender, EventArgs e)
{
  lblDate.Text = DateTime.Now.ToLongTimeString();
}
```

Pour accéder aux données entre processuce / threads, il faut utiliser les délégués.

```c#
// Threads non asynchrone,
private void button1_Click(object sender, EventArgs e)
{
  Thread thread = new Thread(AddText);
  thread.Start();
}
private void AddText()
{
  txtResult.Text += "Yeah ";
  Thread.Sleep(5000);
}

private void timer1_Tick_1(object sender, EventArgs e)
{
  lblDate.Text = DateTime.Now.ToLongTimeString();
}
```

```c#
// Thread dans le cas de Windows Forms
namespace AsyncCourse
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void Form1_Load(object sender, EventArgs e)
        {
            timer1.Start();
        }

        private void button1_Click(object sender, EventArgs e)
        {
            Thread thread = new Thread(AddText);
            thread.Start();

            // Si l'on veut supprimer le processus créer ci-dessus
            // thread.Join();
        }
        private void AddText()
        {
            Thread.Sleep(5000);

            // Ici on réalise des traitements dans un autre processus
            // On réalise ici le traitement lourd

            // Methode délégué
            if (this.InvokeRequired)
            {
            	this.Invoke(new MethodInvoker(() =>
            	{
                	// Ici on réalise le traitement dans le processus principal
                	// on peut accéder aux données du processus principal ici
                	txtResult.Text += "Yeah ";
            	}));
            }

            Thread.Sleep(5000);
        }

        private void timer1_Tick_1(object sender, EventArgs e)
        {
            lblDate.Text = DateTime.Now.ToLongTimeString();
        }
    }
}
```

```c#
namespace AsyncCourse
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void Form1_Load(object sender, EventArgs e)
        {
            timer1.Start();
        }

        private void button1_Click(object sender, EventArgs e)
        {
            Thread thread = new Thread(AddText);
            thread.Start();
            // Si l'on veut supprimer le processus créer ci-dessus
            // thread.Join();

            Thread thread2 = new Thread(AddText2);
            thread2.Start("Salut");
        }
        private void AddText()
        {
            Thread.Sleep(5000);

            // Ici on réalise des traitements dans un autre processus
            // On réalise ici le traitement lourd

            // Methode délégué
            if (this.InvokeRequired)
            {
              this.Invoke(new MethodInvoker(() =>
              {
                  // Ici on réalise le traitement dans le processus principal
                  // on peut accéder aux données du processus principal ici
                  txtResult.Text += "Yeah ";
              }));
            }

            Thread.Sleep(5000);
        }

        private void AddText2(object txt)
        {
            Thread.Sleep(2000);

            // Ici on réalise des traitements dans un autre processus
            // On réalise ici le traitement lourd

            // Methode délégué
            this.Invoke(new MethodInvoker(() =>
            {
                // Ici on réalise le traitement dans le processus principal
                // on peut accéder aux données du processus principal ici
                txtResult.Text += txt.ToString() + ' ';
            }));

            Thread.Sleep(2000);
        }

        private void timer1_Tick_1(object sender, EventArgs e)
        {
            lblDate.Text = DateTime.Now.ToLongTimeString();
        }
    }
}
```

## Ouvrir une autre fenêtre

Dans la fenêtre parent :

```c#
Hide();

Form showJobSeeker = new FrmAffichageDemandeurEmploi();
showJobSeeker.ShowDialog();

Close();
```

Dans la fenêtre ouverte, on peut gérer la fenêtre parent si elle a été envoyé en instance :

```c#

private void ShowWindows_FormClosing(object sender, FormClosingEventArgs e)
{
	parentForm.Close();
	parentForm.Show();
}
```