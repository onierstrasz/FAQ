# LaTeX FAQ

See also [http://scg.unibe.ch/wiki/faq/latex](http://scg.unibe.ch/wiki/faq/latex).

Q How do I strikethrough text?
A \usepackage[normalem]{ulem} gives you \sout{text}.
Also \uline{underlined} and \uwave{wavy}.
See also markup macros in scgPaper.tex

Q How do I control paragraph indentation?
A \setlength{\parindent}{0pt}

Q How do I rename the "References" section?
A \def\refname{Selected publications}

Q How do I add a title footnote with LNCS style?
A Use \thanks{}, not \footnote{}

Q How do I make a figure span two columns?
A Use \begin{figure*}

Q How do I make table entries span two or more columns?
A \multicolumn{2}{l}{text}

Q How do I reduce line spacing within lists?
A \setlength{\itemsep}{...} within the list

Q How do I start numbering an enumeration from a number other than 1?
A \setcounter{enumi}{5}

Q How do I set the page counter?
A \setcounter{page}{1}

Q How do I place two figures side by side?
A Make one figure environment containing two minipages, each with its own caption.
[Example: Squeak by Example, Environment chapter]

Q How do I make sure a block of text is not broken over a page break?
A \usepackage{needspace}
\Needspace{3\baselineskip}

Q How do I turn off the ugly boxes around hyperref links?
A Explicitly set the colors. You can use black too:
\usepackage[pdftex,colorlinks=true,pdfstartview=FitV,linkcolor=black,citecolor=black,urlcolor=black]{hyperref}

Q How do I print a backslash without going into math mode?
A Use \textbackslash

Q How do I turn on page numbering for ieee style?
A \pagestyle{plain}

Q How do I turn on page numbering for acm sigplan style?
A \documentclass[10pt,preprint]{sigplanconf}

Q How do I turn on page numbering for acm proceedings style? (acm_proc_article-sp)
A ???

See also:
http://scg.unibe.ch/wiki/faq/latex
