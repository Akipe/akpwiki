---
title: LaTeX
description: 
published: true
date: 2024-05-21T18:30:20.050Z
tags: 
editor: markdown
dateCreated: 2024-05-21T18:30:20.050Z
---

# LaTeX

## Editeur

Logiciel recommandé pour rédiger en LaTeX :

- [Texmaker](https://www.xm1math.net/texmaker/) (Multi plateforme)
- [Overleaf](https://github.com/overleaf/overleaf) (service en ligne ou auto-hébergeable, collaboratif)

## Todo

### Example

```latex
\documentclass[a4paper,11pt]{article}

\usepackage[utf8]{inputenc} 
\usepackage[T1]{fontenc}
\usepackage[english,french]{babel}
\usepackage{makeidx}

\title{Un Exemple}
\author{Julien MILLETRE}

\makeindex		    %% macro qui permet de générer l'index
\bibliographystyle{prsty}	  %% le style utilisé pour créer la bibliographie

\begin{document}

\maketitle
\newpage

\tableofcontents
\newpage

\section{Debut}
Hello

\index{fonction} 
\subsection{Un premier exemple d'image}

\newpage

\section{Un exemple avec référence bibliographique}
The discovery of the Quantized Hall Effect\footnote{je sais pas ce que c'est!} was made by...

\newpage

\section{Un exemple de tableau}
\begin{tabular}{|*{2}{c|}l r|}
   \hline
   une & deux & trois & quatre \\
   case centrée & encore centrée & à gauche & à droite \\
   \hline
   six & sept & huit & neuf \\
   \hline
\end{tabular}

\newpage

\section{Conclusion}               %% un autre titre
\index{conclusion}                 %% inclure le mot conclusion dans l'index
\index{LaTeX}                      %% inclure le mot LaTeX dans l'index
En conclusion, \LaTeX\ est 
particulièrement bien adapté pour 
rédiger de longs documents.

\newpage

\section{Suite et fin}
On verra plus tard.
\newpage

\end{document}

```
```latex
\documentclass [A4,twoside,12pt]{report}
\usepackage[french]{babel}
\usepackage[OT1,T1]{fontenc}
\usepackage[left=30mm,hmarginratio=3:2,top=25mm,bottom=10mm]{geometry}
\usepackage{pstricks}
 
\begin{document}
 
\title{Réponse aux commentaires de l'expert}
\author{Jean-Marc Blanc}
\date{Mai 2008}
\maketitle
 
\cleardoublepage
```

```latex
\documentclass[a4paper,11pt]{article}

\usepackage[utf8]{inputenc} 
\usepackage[T1]{fontenc}
\usepackage[french]{babel}
\usepackage{makeidx}

\title{Un Exemple}
\author{Julien MILLETRE}

\makeindex		    %% macro qui permet de générer l'index

\begin{document}

\maketitle
\newpage

\tableofcontents
\newpage
\printindex
\newpage

\section{Debut}
Hello \index{sync}

\index{fonction} 
\subsection{Un premier exemple d'image}

\newpage

\section{Un exemple avec référence bibliographique}
The discovery of the Quantized Hall Effect\footnote{je sais pas ce que c'est!} was made by...

\newpage

\section{Un exemple de tableau}
\begin{tabular}{|*{2}{c|}l r|}
   \hline
   une & deux & trois & quatre \\
   case centrée & encore centrée & à gauche & à droite \\
   \hline
   six & sept & huit & neuf \\
   \hline
\end{tabular}

\newpage

\section{Conclusion}               %% un autre titre
En conclusion, \LaTeX\ est 
particulièrement bien adapté pour 
rédiger de longs documents.

\newpage

\section{Suite et fin}
On verra plus tard.

\newpage

\printindex

\end{document}

```

### Index

- <https://www.tuteurs.ens.fr/logiciels/latex/makeindex.html>
- <https://latex-tutorial.com/creating-index-latex/>

### Inspiration

- <https://openclassrooms.com/forum/sujet/latex-rapport-de-stage-58853>
- <https://openclassrooms.com/forum/sujet/latex-structure-rapport-de-stage>

Rapport de stage :

- <http://marin.jb.free.fr/latex/>

Page garde :

- <https://www.jujens.eu/posts/2013/Oct/20/latex-page-garde/>
- <https://borntocode.fr/page-de-garde-personnalise-latex-et-titlepage/>