<!---
{
  "id": "cdd6a16c-90a8-4192-9cc3-9a3f8c6a39eb",
  "teaches": "Managing Bibliographies and Citations with BibTeX",
  "depends_on": ["5b3eacb4-79f5-40cf-8c73-3dcbbd5f8f89"],
  "author": "Exercise Sheet Assistant",
  "first_used": "2025-06-04",
  "keywords": ["LaTeX", "bibliography", "citations", "BibTeX", "references"]
}
--->

# Managing Bibliographies and Citations with BibTeX

> In this exercise you will learn how to manage bibliographies and citations using BibTeX in LaTeX. Furthermore, you will explore how to structure your bibliography database and cite multiple types of sources correctly.

## Introduction

As your LaTeX documents grow more scientific or academic in nature, proper referencing becomes indispensable. Rather than hardcoding reference lists manually, LaTeX offers a systematic approach to citations through **BibTeX**. BibTeX uses a separate `.bib` file to store bibliographic information, allowing you to cite sources within your text using unique citation keys.

The main advantages of BibTeX are reproducibility, consistency, and scalability. Once sources are added to your bibliography database, they can be cited in multiple documents, formatted automatically according to journal or institutional standards, and updated globally if information changes.

In this exercise you will:

* Create a BibTeX database file.
* Insert different types of entries (article, book, online resource).
* Use citation commands such as `\cite{}`.
* Automatically generate and format your bibliography.
* Understand the BibTeX compilation workflow.

Most importantly, you will learn how to separate content from references, keeping your document organized and professional.

### Further Readings and Other Sources

* [Overleaf: Bibliography management with BibTeX](https://www.overleaf.com/learn/latex/Bibliography_management_with_bibtex)
* [LaTeX Wikibook: BibTeX](https://en.wikibooks.org/wiki/LaTeX/Bibliography_Management)
* [TUG.org: BibTeX documentation](https://tug.org/pracjourn/2007-1/mori/mori.pdf)
* [DOI:10.5555/1246063](https://doi.org/10.5555/1246063) — The LaTeX Companion, Chapter 13

## Tasks

### Project Setup

Continue using your previous project structure:

```
./
├── figures/
├── src/
│   └── main.tex
└── bibliography/
    └── references.bib
```

### Task 1: Create the BibTeX File

1. In `./bibliography/references.bib`, create a new file and add the following entries:

```bibtex
@article{lamport1994,
  author  = {Leslie Lamport},
  title   = {LaTeX: A Document Preparation System},
  journal = {Addison-Wesley},
  year    = {1994}
}

@book{mittelbach2004,
  author    = {Frank Mittelbach and Michel Goossens},
  title     = {The LaTeX Companion},
  publisher = {Addison-Wesley Professional},
  year      = {2004}
}

@online{overleaf,
  author  = {Overleaf},
  title   = {Bibliography management with BibTeX},
  year    = {2023},
  url     = {https://www.overleaf.com/learn/latex/Bibliography_management_with_bibtex}
}
```

### Task 2: Insert Citations in Your Main Document

1. In `./src/main.tex`, load the bibliography package:

```latex
\usepackage[backend=bibtex]{biblatex}
\addbibresource{../bibliography/references.bib}
```

2. Inside your document body, insert citations like this:

```latex
LaTeX was introduced by Lamport~\cite{lamport1994} and further expanded in The LaTeX Companion~\cite{mittelbach2004}. Online resources such as Overleaf~\cite{overleaf} offer comprehensive tutorials.
```

### Task 3: Print the Bibliography

At the end of your document, add:

```latex
\printbibliography
```

### Task 4: Compile Using BibTeX

1. From the root directory, run:

```bash
pdflatex ./src/main.tex
bibtex ./src/main.aux
pdflatex ./src/main.tex
pdflatex ./src/main.tex
```

Note that multiple runs of `pdflatex` are required to resolve all cross-references correctly.

### Task 5: Use Citation Variants

1. Replace some `\cite{}` commands with `\parencite{}` or `\textcite{}` after adding `\usepackage[style=authoryear]{biblatex}` to explore different citation styles.

## Questions

1. What happens if you omit `bibtex` from the compilation sequence?
2. Why is a `.bib` file preferred over hardcoded bibliographies?
3. What is the difference between `\cite{}` and `\parencite{}`?
4. How can BibTeX help maintain consistency across multiple documents?
5. Can you reuse `references.bib` in future projects? Why?

## Advice

Mastering BibTeX transforms your LaTeX documents into scalable and professional publications. Even for small projects, it prevents duplication and errors while enabling easy adaptation to different style requirements. Many journals, conferences, and academic institutions rely heavily on BibTeX for their submissions. You are now building the foundation for advanced academic and professional writing. Reuse your `references.bib` file across multiple projects to build your own personal citation library over time. This exercise also prepares you for future topics like citation styles, reference management software integration, and journal-specific document classes.
