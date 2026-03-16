# 📝 LaTeX Recipes & Tips

> A collection of practical LaTeX recipes for scientific writing  
> *Une collection de recettes LaTeX pratiques pour la rédaction scientifique*

---

## Table of Contents

1. [Document Setup](#document-setup)
2. [Mathematics](#mathematics)
3. [Tables](#tables)
4. [Figures](#figures)
5. [References](#references)
6. [Formatting](#formatting)
7. [Common Issues](#common-issues)

---

## 📄 Document Setup

### Basic Preamble (French)

```latex
\documentclass[a4paper, 11pt]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[french]{babel}
\usepackage{lmodern}
\usepackage{amsmath, amssymb, amsthm}
\usepackage{graphicx}
\usepackage{hyperref}
```

### Basic Preamble (English)

```latex
\documentclass[a4paper, 11pt]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[english]{babel}
\usepackage{lmodern}
\usepackage{amsmath, amssymb, amsthm}
\usepackage{graphicx}
\usepackage{hyperref}
```

---

## 🧮 Mathematics

### Inline Equations

```latex
The energy is given by $E = h\nu$ where $h$ is Planck's constant.
```

### Displayed Equations

```latex
\begin{equation}
    E_n = -\frac{13.6 \text{ eV}}{n^2}
    \label{eq:hydrogen}
\end{equation}
```

### Aligned Equations

```latex
\begin{align}
    \psi(x,t) &= \frac{1}{\sqrt{2\pi}} \int \phi(k) e^{i(kx-\omega t)} dk \\
    &= \sum_n c_n \psi_n(x) e^{-iE_n t/\hbar}
    \label{eq:wavefunction}
\end{align}
```

### Matrices

```latex
\begin{equation}
    H = \begin{pmatrix}
        E_1 & 0 & 0 \\
        0 & E_2 & 0 \\
        0 & 0 & E_3
    \end{pmatrix}
\end{equation}
```

### Common Math Symbols

| Symbol | Code | Symbol | Code |
|--------|------|--------|------|
| α β γ | `\alpha \beta \gamma` | ∂ ∇ ∞ | `\partial \nabla \infty` |
| ≤ ≥ ≠ | `\le \ge \neq` | ∈ ∉ ⊂ | `\in \notin \subset` |
| ∫ ∬ ∭ | `\int \iint \iiint` | ∑ ∏ ∐ | `\sum \prod \coprod` |
| √ ∛ | `\sqrt \sqrt[3]` | ± × ÷ | `\pm \times \div` |
| → ← ↔ | `\to \leftarrow \leftrightarrow` | ⇒ ⇔ | `\Rightarrow \Leftrightarrow` |

### Fractions & Powers

```latex
% Simple fraction
$\frac{a}{b}$

% Nested fraction
$\frac{1}{1 + \frac{1}{x}}$

% Powers
$x^2 \quad x^{n+1} \quad e^{i\pi}$

% Roots
$\sqrt{x} \quad \sqrt[n]{x} \quad \sqrt{a^2 + b^2}$
```

### Brackets & Delimiters

```latex
% Automatic sizing
\left( \frac{a}{b} \right)

% Manual sizing
\big( \Big( \bigg( \Bigg(

% Different types
\left[ x \right] \quad \left\{ x \right\} \quad \left| x \right|
```

---

## 📊 Tables

### Basic Table

```latex
\begin{table}[h]
    \centering
    \caption{Example Table}
    \label{tab:example}
    \begin{tabular}{lcr}
        \hline
        \textbf{Column 1} & \textbf{Column 2} & \textbf{Column 3} \\
        \hline
        A & B & C \\
        D & E & F \\
        G & H & I \\
        \hline
    \end{tabular}
\end{table}
```

### Professional Table (booktabs)

```latex
\usepackage{booktabs}  % In preamble

\begin{table}[h]
    \centering
    \caption{Professional Table}
    \begin{tabular}{lrr}
        \toprule
        \textbf{Parameter} & \textbf{Value} & \textbf{Uncertainty} \\
        \midrule
        Wavelength & 532 & nm \\
        Power & 100 & mW \\
        Temperature & 298 & K \\
        \bottomrule
    \end{tabular}
\end{table}
```

### Colored Table

```latex
\usepackage[table]{xcolor}  % In preamble

\begin{table}[h]
    \centering
    \rowcolors{2}{gray!10}{white}
    \begin{tabular}{lcc}
        \hline
        \rowcolor{gray!30}
        \textbf{Item} & \textbf{Value} & \textbf{Unit} \\
        \hline
        Mass & 9.11 & $10^{-31}$ kg \\
        Charge & 1.60 & $10^{-19}$ C \\
        Spin & 1/2 & $\hbar$ \\
        \hline
    \end{tabular}
\end{table}
```

---

## 🖼️ Figures

### Basic Figure

```latex
\begin{figure}[h]
    \centering
    \includegraphics[width=0.8\textwidth]{image.png}
    \caption{Description of the figure}
    \label{fig:example}
\end{figure}
```

### Multiple Subfigures

```latex
\usepackage{subcaption}  % In preamble

\begin{figure}[h]
    \centering
    \begin{subfigure}{0.45\textwidth}
        \includegraphics[width=\textwidth]{image1.png}
        \caption{First image}
        \label{fig:1a}
    \end{subfigure}
    \hfill
    \begin{subfigure}{0.45\textwidth}
        \includegraphics[width=\textwidth]{image2.png}
        \caption{Second image}
        \label{fig:1b}
    \end{subfigure}
    \caption{Combined figure}
    \label{fig:combined}
\end{figure}
```

### TikZ Diagram (Simple)

```latex
\usepackage{tikz}  % In preamble

\begin{tikzpicture}
    \draw[->] (0,0) -- (5,0) node[right] {$x$};
    \draw[->] (0,0) -- (0,5) node[above] {$y$};
    \draw[blue, thick] (0,0) parabola (4,4);
    \node at (2,2) {$y = x^2$};
\end{tikzpicture}
```

---

## 📚 References

### Citations (BibTeX)

```latex
% In .bib file
@article{einstein1905,
    author = {Albert Einstein},
    title = {Zur Elektrodynamik bewegter Körper},
    journal = {Annalen der Physik},
    volume = {322},
    number = {10},
    pages = {891--921},
    year = {1905}
}

% In .tex file
\bibliographystyle{plain}
\bibliography{references}

% Cite in text
As shown by Einstein~\cite{einstein1905}, ...
```

### Cross-References

```latex
% Label sections, equations, figures
\section{Introduction}
\label{sec:intro}

% Reference them
See Section~\ref{sec:intro}
Equation~\eqref{eq:hydrogen}
Figure~\ref{fig:example}
```

---

## ✨ Formatting

### Custom Commands

```latex
% In preamble
\newcommand{\ket}[1]{\left| #1 \right\rangle}
\newcommand{\bra}[1]{\left\langle #1 \right|}
\newcommand{\braket}[2]{\left\langle #1 | #2 \right\rangle}
\newcommand{\expect}[1]{\left\langle #1 \right\rangle}

% Usage
$\ket{\psi}$, $\bra{\phi}$, $\braket{\phi}{\psi}$
```

### Theorem Environments

```latex
\usepackage{amsthm}  % In preamble

\newtheorem{theorem}{Theorem}
\newtheorem{lemma}{Lemma}
\newtheorem{corollary}{Corollary}
\newtheorem{definition}{Definition}

% Usage
\begin{theorem}[Pythagoras]
    In a right triangle: $a^2 + b^2 = c^2$
\end{theorem}

\begin{definition}[Wave Function]
    The wave function $\psi(x,t)$ describes...
\end{definition}
```

### Lists

```latex
% Itemize
\begin{itemize}
    \item First item
    \item Second item
    \begin{itemize}
        \item Nested item
    \end{itemize}
\end{itemize}

% Enumerate
\begin{enumerate}
    \item First step
    \item Second step
    \item Third step
\end{enumerate}

% Description
\begin{description}
    \item[Term] Definition
    \item[Concept] Explanation
\end{description}
```

---

## 🐛 Common Issues

### Problem: Accent Issues in French

**Solution:**
```latex
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[french]{babel}
```

### Problem: Image Not Found

**Solution:**
```latex
% Check path
\includegraphics{./figures/image.png}

% Or use graphicx path
\usepackage{graphicx}
\graphicspath{{./figures/}}
```

### Problem: References Show as ??

**Solution:**
```bash
# Compile multiple times
pdflatex document.tex
bibtex document.aux
pdflatex document.tex
pdflatex document.tex
```

### Problem: Table Too Wide

**Solution:**
```latex
% Use tabular* or resizebox
\begin{table}
    \resizebox{\textwidth}{!}{
        \begin{tabular}{...}
            ...
        \end{tabular}
    }
\end{table}
```

### Problem: Equation Too Long

**Solution:**
```latex
\begin{multline}
    f(x) = a + b + c + d + e + f + g + h \\
    + i + j + k + l + m + n
\end{multline}
```

---

## 🔧 Useful Packages

| Package | Purpose |
|---------|---------|
| `amsmath` | Advanced mathematics |
| `amssymb` | Math symbols |
| `amsthm` | Theorem environments |
| `booktabs` | Professional tables |
| `caption` | Caption customization |
| `cleveref` | Smart references |
| `geometry` | Page layout |
| `graphicx` | Include graphics |
| `hyperref` | Hyperlinks |
| `siunitx` | Units & numbers |
| `subcaption` | Subfigures |
| `tikz` | Vector graphics |
| `tcolorbox` | Colored boxes |
| `xcolor` | Colors |

---

## 📖 Additional Resources

- [Overleaf LaTeX Guide](https://www.overleaf.com/learn)
- [Detexify](http://detexify.kirelabs.org/) – Draw symbols to find LaTeX code
- [LaTeX Wikibook](https://en.wikibooks.org/wiki/LaTeX)
- [TeX Stack Exchange](https://tex.stackexchange.com/)

---

*UY1 Néo Quanticiens – LaTeX Resources Collection*
