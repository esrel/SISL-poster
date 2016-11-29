================================================================================
Readme for sisl.sty for a0poster package

author: Evgeny A. Stepanov
email : stepanov.evgeny.a@gmail.com
================================================================================

--------------------------------------------------------------------------------
Used Packages
--------------------------------------------------------------------------------
The style file makes use of the tikz, xcolor, graphicx and times packages; thus,
it automatically loads them, i.e. no need to include them using \usepackage{}.

--------------------------------------------------------------------------------
Poster Format
--------------------------------------------------------------------------------
The style file is designed for 2-column portrait A0 posters with 2 logos in 
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

As style requires 2 logos, they are set using \logol{} and \logor{} commands
for left and right logos respectively (provide path to image files). 
All image formats supported by graphicx package can be used.

Once all these are defined calling \makeptitle command within document
environment will typeset the header.

--------------------------------------------------------------------------------
Provided Commands and Environments
--------------------------------------------------------------------------------
The style file provides definitions of colored boxes for major poster sections 
and colored boxes for sub-section headings.

Major poster sections are implemented as mainbox environment.
The environment requires title as an argument, which will be displayed in the
colored box. The color of the box is shaded blue by default. The color can be
controlled by optional paramenter in square brackets. All colors and color
specifications supported by xcolor package can be used
(e.g. red, red!20, red!20!black, etc.).

\begin{mainbox}[color]{Title}
\end{mainbox}

Poster sub-sections are set using \subsec[color]{title} command.
Similar to mainbox, it requires title as an argument, and its color can be
controlled using optional parameter.

--------------------------------------------------------------------------------
How to Control Box Placement
--------------------------------------------------------------------------------
Main sections of the poster are implemented using minipage package. Thus, it is
advised to use mainbox environment as follows.

(1) To make sections appear in the same row do not leave extra new line:

\begin{mainbox}{BOX 1}
something
\end{mainbox}
\begin{mainbox}{BOX 2}
something
\end{mainbox}

(2) To start a new row of boxes simply add a new line:

\begin{mainbox}{BOX 2}
something
\end{mainbox}

\begin{mainbox}{BOX 3}
something
\end{mainbox}

(3) To make the poster look 'prettier' it is advised to control the space
between rows using \vspace{} command:

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
sections, these can be controlled as desired using standard latex commands.

For example, the below command will create green title box and typeset title
'BOX 1' with Huge italic and blue-black font. By default, all section and
subsection titles are \Large and bold. To change that you will need to modify
style file, changing the tikz definition. Search for "font = \Large\bfseries"
and comment/delete that.

\begin{mainbox}[green!50!black]{{\color{blue!25!black}\Huge{\textit{BOX 1}}}}
something
\end{mainbox}

--------------------------------------------------------------------------------
Known Restrictions & Solutions
--------------------------------------------------------------------------------
(1) You cannot use float environments such as table and figure. However, you
can use tabular and tabularx environments, as well as \includegraphics and
tikzpicture.

(2) Because style file was designed for A0 portrait poster, logo sizes are set
to 0.14\textwidth. In landscape poster format, 0.14\textwidth is wider, thus
the header itself occupies more space. To reduce the space change the width
specified by lines \includegraphics[width=0.98\textwidth]{\@logol} and 
\includegraphics[width=0.98\textwidth]{\@logor} to a lower value as desired
(e.g. 0.7\textwidth).
================================================================================

