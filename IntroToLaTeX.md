# Intro to $\LaTeX$

With a doc in `markdown` for the memes.

![latex\neq\LaTeX](<WhatsApp Image 2025-10-04 at 17.06.47_79924242.jpg>)

## What is it?

It is a *markup* language, like HTML, we use

```html
<h1>Heading</h1>
```

To define how *heading* should appear, we define how and where text should appear and $\LaTeX$ does the rest.

Every academic/research paper you see is written in $\LaTeX$, if it's not, you should stay away from it. It's used to create good looking documents with minimal effort. For example to get, $$\int_0^\pi\sin(x)dx,$$ we just need to type

```tex
\[\int_0^\pi\sin(x)dx\]
```

(Markdown with $\KaTeX$ can also render $\LaTeX$, which is why you can see the nice equations here as well. Note that this does not make $\LaTeX$ obsolete, as `markdown` is shit.)

But to quickly mention, for inline math, wrap the equation in $, like `$x=2$`, which generates $x=2$ or \$$, like `$$x=2$$` to get $$x=2.$$

## Getting started with it

You have two options.

1. Use an online IDE, such as [Overleaf](https://overleaf.com)
1. Download and run it locally

### On Overleaf

Visit [Overleaf](https://overleaf.com) and start a new blank project. We can directly start writing on the `main.tex` file, and see it's final output on the left PDF after compilation.

### Locally

To run $\LaTeX$ locally, we need to download it. The simplest way is to use [Tex Live](https://www.tug.org/texlive/). Follow the install instructions as per your operating system. (Note that the entire $\TeX$ package costs about 9 gigs, you can choose a smaller subset.)

After installation, you could get any $\TeX$ editor, visit [Wikipedia's list of TeX editors](https://en.wikipedia.org/wiki/Comparison_of_TeX_editors) to choose one, I'd recommend [TeXstudio](https://www.texstudio.org/).

If you'd like to us Visual Studio Code (which I prefer), get the [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop) extension. You could also configure neovim with the [VimTeX](https://github.com/lervag/vimtex) extension if you like.

Now, create any file ending with `.tex`, and use the `pdflatex` executable/binary to compile this $\TeX$ file into a PDF. The final command would be

```sh
pdflatex main.tex
```

Assuming you named your file `main.tex`. Note that every editor does this itself, so you need not worry about these commands.

![ms-word-best-practices](<WhatsApp Image 2025-10-05 at 16.51.32_577eeaa5.jpg>)

## $\LaTeX$

Let's finally talk about it. The minimum you need to write to get started with any document is

```tex
\documentclass[options]{article}
\begin{document}
<Everything goes inside here>
\end{document}
```

Where the `documentclass` defines how our document looks like. `article` is the most common, but you could also have `book`, `report`, and more (even custom stuff). The `options` defines some parameters such as font size (default is 10pt), paper size (letterpaper/a4paper), landscape and more.

The next most important thing is setting up your document title, authors, and date.

```tex
\documentclass{article}

\title{Intro to \LaTeX}
\author{Taraash}
\date{\today} %which is default, so could be omitted.

\begin{document}
\maketitle

Welcome to some \LaTeX-ed!

\end{document}
```

Use the `maketitle` command inside the `document` environment, and define your title, author, and date as shown above. Use the percent symbol (`%`) for comments.

### Document structure

We have `\section{}`, `\subsection{}` and `\subsubsection{}` to organize. Note that there are also starred version of these commands, like `\section*{}`, these do not number whatever section you have. `\\` is the line break. `\newpage` moves everything below to a new page.

Use the `\tableofcontents` to... get a table of contents. Starred ((sub)sub)sections are hidden.

### Text

| Command | Output | Effect |
| --- | --- | --- |
| \textbf{text} | $\textbf{text}$ | Boldface |
| \textit{text} | $\textit{text}$ | Italics |
| \textrm{text} | $\textrm{text}$ | Roman family |
| \texttt{text} | $\texttt{text}$ | Typewriter |
| \emph{text} | $\emph{text}$ | Emphasize |
| \textit{text \emph{emph}} | $\textit{text \emph{emph}}$ | Changes depending where it is |

### Math mode

Probably the most useful thing $\TeX$ is known for, its ability to handle extremely complex mathematical equations beautifully. Consider for example $$\int_0^{\int_0^1e^{-x^2}}e^{x^2}dx.$$ You would have incredible trouble getting something like this any other package, but in here, we just need `\int_0^{\int_0^1e^{-x^2}}e^{x^2}dx` to do it!

I've already described inline (use `$math$` or `\(math\)`) and display math mode (use `\[math\]` or the `equation` environment). By an *environment*  we mean

```tex
\begin{equation}
<stuff here>
\end{equation}
```

Hence `document` is also an environment, stuff inside which get's displayed in the compiled PDF. (Much like the `body` tag in HTML, everything before the `\begin{document}`, the *preamble* is the `head` tag.)

1. Subscripts: `a_1` = $a_1$, `a_12` = $a_12$, `a_{12}` = $a_{12}$
1. Superscripts: `x^2` = $x^2$, `x^2y` = $x^2y$, `x^{2y}` = $x^{2y}$
1. Fractions: `\frac{x}{y}` = $\frac{x}{y}$
1. Square roots: `\sqrt[n]{x}` = $\sqrt[n]{x}$
1. Sum: `\sum_{k=0}^{\infty}a_k` = $\sum_{k=0}^{\infty}a_k$
1. Product: `\prod_{k=0}^{\infty}a_k` = $\prod_{k=0}^{\infty}a_k$
1. Integral: `\int a_k` = $\int a_k$

Some commonly used symbols

| Symbol | Command |
| --- | --- |
| $\leq$ | \leq |
| $\neq$ | \neq |
| $\times$ | \times |
| $\wedge$ | \wedge |
| $\in$ | \in |
| $\notin$ | \notin |
| $\forall$ | \forall |
| $\exists$ | \exists |
| $\subset$ | \subset |
| $\rightarrow$ | \rightarrow |
| $\pm$ | \pm |
| $\cdots$ | \cdots |

You can find tables for these online. If you're using the LaTeX Workshop extension in VS Code, find the Symbols panel it provides. Overleaf premium also has one, but you could just search up what you need.

### More environments

![meme-3](<WhatsApp Image 2025-10-05 at 16.58.17_90e7b816.jpg>)

Ordered lists

```tex
\begin{enumerate}
\item First
\item Second
\end{enumerate}
```

 Unordered lists

```tex
\begin{itemize}
\item Banana
\item Monkey
\end{itemize}
```

Description

```tex
\begin{description}
\iten[Banana] Eaten by monkeys
\item[Monkeys] Eat banana
\item[Humans] Evolved from monkeys, similar to bananas ($\sim 99\%$ DNA match?)
\end{description}
```

Table

```tex
\begin{tabular}{|l|c|r|}
\hline
left_aligned & center_aligned & right_aligned \\
second & row & data \\
\hline %horizontal line
\end{tabular}
```

Align

```tex
\begin{align*}
x + 2 &= 7 \\
x &= 5
\end{align*}
```

$$
\begin{align*}
x + 2 &= 7 \\
x &= 5
\end{align*}
$$

The & are aligned vertically, here, keeping them before the equals to sign ensures the equals to sign are aligned vertically. Here, starring the environments gets rid of the numbering done by the unstarred environment.

$$
\begin{align}
x + 2 &= 7 \\
x &= 5
\end{align}
$$

Quote

```tex
\begin{quote}
We are made of star-stuff.
\hfill \textit{---Carl Sagan}
\end{quote}
```

To get quotes, you need \`hello' ($\text{`hello'}$) and \`\`hello'' for double ($\text{``hello"}$). DO NOT USE `"baaad"` ($\text{"baaad"}$)!

### Spacing

- `hspace{10pt}`: Adds a horizontal space of 10pt
- `vspace{10pt}`: Vertical space of 10pt
- `vfill`: Adds space to vertically fill the page
- `hfill`: Adds space to horizontally fill the page
- `newpage`: Creates a new page
- `\\[10pt]`: Adds a new line and a vertical space of 10pt

## Links

- [Overleaf's $\LaTeX$ in 30 minutes](https://www.overleaf.com/learn/latex/Learn_LaTeX_in_30_minutes)
- [The $\TeX$ for my notes for game development with Unreal Engine](https://github.com/T-Cent/Notes-for-Unreal-Engine)
- [Everything I've ever made for Évariste](https://github.com/T-Cent/evariste) (will be continuously updated, make sure to star this repo)

I'd be very happy if, because of this session you were able to use $\LaTeX$, start a discussion on our [WhatsApp](), [Telegram](), or credit/mention/share whatever you made! Thank you.
