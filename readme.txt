================================================================================
Readme for sisl.sty for a0poster package

author: Evgeny A. Stepanov
email : stepanov.evgeny.a@gmail.com
================================================================================

--------------------------------------------------------------------------------
Used Packages
--------------------------------------------------------------------------------
The style file makes use of the tikz, xcolor, graphicx and times packages; thus,
it automatically loads them, i.e. no need to include using \usepackage{}.

--------------------------------------------------------------------------------
Poster Format
--------------------------------------------------------------------------------
The style file was designed for 2-column portrait A0 posters with 2 logos in 
upper left and upper right corners (to the left and right of the title). 
Both logos are required. The default 'reading' direction of the poster is from
left to right and from top to bottom. 

--------------------------------------------------------------------------------
Number of columns
--------------------------------------------------------------------------------
In case a landscape poster with 3 or more columns is desired, please set the
column width using \colwidth{X\textwidth} command, where X has a value from 0 
to 1. In a 2-column format, for example, column width is set to 0.49\textwidth
considering the space between columns. Thus, for 3 column format it can be set
to 0.32\textwidth.

--------------------------------------------------------------------------------
Typesetting the Poster Header
--------------------------------------------------------------------------------
The poster header is generated automatically from the \title{} and \author{}
definitions in the tex file preamble. Make sure to set date as empty (\date{})
to avoid it to be included into the header.

As style require 2 logos, they are set using \logol{} and \logor{} commands for
left and right logos respectively (provide path to image files). 
All image formats supported by graphicx package can be used.

Once all these are defined envoking \makeptitle command within document 
environment will typeset the header.

--------------------------------------------------------------------------------
Provided Commands and Environments
--------------------------------------------------------------------------------
The style file provides definitions of colored boxes for major poster sections 
and colored boxes for sub-section headings.

Major poster sections are implemented as mainbox environment.
The environment requires title argument, which will be displayed in the colored
box. The color of the box is shaded blue by default, and it is controlled by
optional paramenter. All colors and color specifications supported by xcolor 
can be used (e.g. red, red!20, red!20!black, etc.).

\begin{mainbox}[color]{Title}
\end{mainbox}

Poster sub-sections are triggered using \subsec[color]{title} command.
Similar to mainbox, it requires title as an argument, and its color can be
controlled using optional parameter.

--------------------------------------------------------------------------------
How to Control Box Placement
--------------------------------------------------------------------------------
Main sections of the poster are implemented using minipage package. Thus, it is
advised to use mainbox environment as follows.

To make to sections appear in the same row do not leave extra new line, e.g.

\begin{mainbox}{BOX 1}
something
\end{mainbox}
\begin{mainbox}{BOX 2}
something
\end{mainbox}

To start a new row of boxes simply add a new line, e.g.
\begin{mainbox}{BOX 2}
something
\end{mainbox}

\begin{mainbox}{BOX 3}
something
\end{mainbox}

To make the poster look 'prettier' it is advised to control the space between 
rows using \vspace{} command, as:


\begin{mainbox}{BOX 2}
something
\end{mainbox}

\vspace*{0.5cm}

\begin{mainbox}{BOX 3}
something
\end{mainbox}

--------------------------------------------------------------------------------
How to Control Font Style and Color
--------------------------------------------------------------------------------
Even though the style file provides default fonts and styles for boxes and sub-
sections, all can be controlled as desired using standard latex commands.

For example, the below command will create green title box and typeset title
'BOX1' with Huge italic and blue-black font. By default, all section and
subsection titles are \Large and in bold. To change that you will need to 
modify sty file, changing the tikz definition. Remove font definition in lines:
"font = \Large\bfseries".

\begin{mainbox}[green!50!black]{{\color{blue!25!black}\Huge{\textit{BOX 1}}}}
something
\end{mainbox}

--------------------------------------------------------------------------------
Known Restrictions
--------------------------------------------------------------------------------
1. You cannot use float environments such as table and figure. However, you
can directly use tabular and tabularx environments, as well as \includegraphics
and tikzpicture.

================================================================================

