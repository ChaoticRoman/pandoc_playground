# Pandoc playground

[Pandoc](https://pandoc.org/) is a markup formats converter, often called markup documents swiss knife.

Here I am interested in three usecases using Markdown (md) as a source format:

1. **Markdown to slides**
    I like markdown, let's see if I can use it for presentation preparations.
2. **Markdown to PDF**:
    The md format is great for source control and versioning, let's try to have user guides and other
    printable documents like that maintained in md.
3. **Markdown to HTML**:
    Online documentation, in-application documents and any rich text format in custom apps (HTML renderers
    are often parts of various frameworks, unlike the MD rendering).
4. **Single documentation source**:
    Bonus point as having the same source for numbers 2 and 3.

Required features would be:

* publication quality
* SVG images support
* code blocks with syntax highlighting, e.g.

```python
print("Hello world!")

def square(x):
    return x**2
```

## TODO

* verify everything
* provide sources

## Resources

* [Documentation on input/output formats](https://pandoc.org/MANUAL.html#general-options)
* [Demos][demos]

## Installation

```
sudo apt install texlive-latex-base pandoc texlive-fonts-recommended librsvg2-bin texlive-xetex
```

## Markdown to Slides

From [demos] number 8 looks nice:

```
pandoc -t beamer SLIDES -o example8.pdf
```

Some official documentation: https://pandoc.org/chunkedhtml-demo/10-slide-shows.html

## Markdown to PDF

From [demos] numbers 13 and 14 look nice:

Number 13 using this `README.md` (**TESTED**):

```
pandoc README.md --pdf-engine=xelatex -o example13.pdf
```

Number 14 untested:

```
pandoc -N --variable "geometry=margin=1.2in" --variable mainfont="Palatino" --variable sansfont="Helvetica" --variable monofont="Menlo" --variable fontsize=12pt --variable version=2.0 MANUAL.txt --include-in-header fancyheaders.tex --pdf-engine=lualatex --toc -o example14.pdf
```

## Markdown to HTML

Multiple files:

```
pandoc -t chunkedhtml source.md -o chunked.html
```

[Some other examples.][demos]

[demos]: https://pandoc.org/demos.html
