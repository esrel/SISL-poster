SISL Poster
===========

version number: 0.0.1

author: Evgeny A. Stepanov

email : stepanov.evgeny.a@gmail.com


Used Packages
-------------
The style file makes use of the `tikz`, `xcolor`, `graphicx` and `times` packages; thus, it automatically loads them, i.e. no need to include them using `\usepackage{}`.


Poster Format
-------------
The style file is designed for 2-column portrait A0 posters with 2 logos in upper left and upper right corners (to the left and right of the title). Both logos are required. The default 'reading' direction of the poster is from left to right and from top to bottom.


Number of columns
-----------------
In case a landscape poster with 3 or more columns is desired, please set the column width using `\colwidth{X\textwidth}` command, where X has a value from 0 to 1. In a 2-column format, for example, column width is set to `0.49\textwidth` considering the space between columns. Thus, for 3 column format it can be set to `0.32\textwidth`.

Typesetting the Poster Header
-----------------------------
The poster header is generated automatically from the `\title{}` and `\author{}` definitions in the tex file preamble. Make sure to set date as empty (`\date{}`) to avoid it to be included into the header.

As style requires 2 logos, they are set using `\logol{}` and `\logor{}` commands for left and right logos respectively (provide path to image files). All image formats supported by graphicx package can be used.

Once all these are defined calling \makeptitle command within document environment will typeset the header.

Provided Commands and Environments
----------------------------------
The style file provides definitions of colored boxes for titles of major poster section and sub-section headings.

Both section and sub-section headings (colored boxes) are implemented as commands: `\psec` and `\psubsec`, respectively. The commands take 1 required argument -- title text. The color of the box can be provided as an optional argument.

```
\psec[color]{title}
\psubsec[color]{title}
```

For convenience, major poster sections are implemented as `psecbox` environment. The environment is a wrapper around `\psec` command and additionally provides text indentation within the box (implemented as minipage). 

Similar to `\psec` command, the environment requires title as an argument, which will be displayed in the colored box. The color of the box is shaded blue by default. Similarly, the color can be controlled by optional parameter in square brackets. All colors and color specifications supported by `xcolor` package can be used (e.g. `red`, `red!20`, `red!20!black`, etc.).

```
\begin{psecbox}[color]{Title}
\end{psecbox}
```

`\setpsecheight` and `\setpsubsecheight` commands are provided to set height of `psec` and `psubsec` boxes, respectively. They accept both relative and absolute values, such as `0.05\textwidth` and `4cm`, for instance.


How to Control Box Placement
----------------------------
Main sections of the poster are implemented using `minipage` package. Thus, it is advised to use `psecbox` environment as follows.

1. To make sections appear in the same row do not leave extra new line:

```
\begin{psecbox}{BOX 1}
something
\end{psecbox}
\begin{psecbox}{BOX 2}
something
\end{psecbox}
```

2. To start a new row of boxes simply add a new line:

```
\begin{psecbox}{BOX 2}
something
\end{psecbox}

\begin{psecbox}{BOX 3}
something
\end{psecbox}
```

3. To make the poster look _prettier_ it is advised to control the space between rows using `\vspace{}` command:

```
\begin{psecbox}{BOX 2}
something
\end{psecbox}

\vspace*{0.5cm}

\begin{psecbox}{BOX 3}
something
\end{psecbox}
```

**Note**:

If desired, `psecbox` environment can be completely ignored; and placement controlled by `minipage` environment and `\psec` command.

How to Control Font Style and Color
-----------------------------------
Even though the style file provides default fonts and styles for boxes and sub-sections, these can be controlled as desired using standard latex commands.

For example, the below command will create green title box and typeset title 'BOX 1' with Huge italic and blue-black font. By default, all section and subsection titles are `\Large` and bold. To change that you will need to modify style file, changing the `tikz` definition. Search for `font = \Large\bfseries` and comment/delete that.

```
\begin{psecbox}[green!50!black]{{\color{blue!25!black}\Huge{\textit{BOX 1}}}}
something
\end{psecbox}
```

However, the style file provides several commands to set default font styles and colors for title, author, psec and psubsec using the following commands:

```
\setptitlestyle{style}{color}
\setpauthorstyle{style}{color}
\setpsecstyle{style}{color}
\setpsubsecstyle{style}{color}
```

The color is controlled by `xcolor`.

The style, on the other hand is specified as `\fontsize\fontseries\fontshape`:

e.g. `\Large\bfseries\itshape`. Consult LaTeX manual or [wiki](https://en.wikibooks.org/wiki/LaTeX/Fonts) for desired style.


Both -- standard LaTeX commands & default style definitions via `\secXstyle` can be used together. In such cases the former takes precedence (default LaTeX behavior).

How to Set Background Color
---------------------------
The color of the poster background can be set using `pagecolor` package's `\pagecolor{color}` command. The colors are controlled by `xcolor` package.

```
\usepackage{pagecolor}

\begin{document}
\pagecolor{blue!5}
\end{document}
```


Known Restrictions & Solutions
------------------------------
1. You cannot use float environments such as `table` and `figure`. However, you can use `tabular` and `tabularx` environments, as well as `\includegraphics` and `tikzpicture`.

2. Because style file was designed for A0 portrait poster, logo sizes are set to `0.14\textwidth`. In landscape poster format, `0.14\textwidth` is wider, thus the header itself occupies more space. To reduce the space change the width specified by lines 

```
\includegraphics[width=0.98\textwidth]{\@logol}
```
and
```
\includegraphics[width=0.98\textwidth]{\@logor}
```
to a lower value as desired (e.g. `0.7\textwidth`).

3. In case title or author spans several lines, addtional spacing might be required. It can be controlled using `\vspace*{}` command directly in title and author definitions:

(e.g. `\title{Poster Template\\ \vspace*{1cm} (Check Readme File)}`)

4. In case variable size of boxes is used (e.g. via `minipage` environment), to ensure equal height of colored `psec` boxes, it is advised to set default `psec` and `psubsec` heights using `\setpsecheight` and `\setpsubsecheight` commands (to absolute values).
