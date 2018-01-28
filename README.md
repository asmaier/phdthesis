# PhD thesis
This is my PhD thesis. It is written in LaTeX and converted to HTML via LaTeXML.
The HTML output can be seen at

 - https://asmaier.github.io/phdthesis/

The official PDF can be obtained from http://d-nb.info/991992733 . 

## Prerequisites
To convert the LaTeX source you need to install [LaTeXML](http://dlmf.nist.gov/LaTeXML/). On Mac OS X do

    $ brew install latexml

In addition one needs to install ImageMagick (the formula for ImageMagick from homebrew doesn't work for LaTeXML)

    $ wget https://www.imagemagick.org/download/ImageMagick.tar.gz
    $ tar zxvf ImageMagick.tar.gz
    $ cd ImageMagick

Build and compile ImageMagick from source

    $ ./configure --with-perl=/usr/bin/perl
    $ make
    $ make install
    $ make clean

Open a new terminal and check if you can use the perl package

    $ /usr/bin/perl -le 'use Image::Magick; print Image::Magick->QuantumDepth'
    16

After doing this the `latexmlpost` command should find the `Image::Magick` perl module and be able to convert images.

## Conversion
To convert the latex source file `diss.tex` to the `*.html` output files do

    $ latexml diss.tex --dest=diss.xml
    $ latexmlpost --format=html5 --splitat=chapter --javascript='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.2/MathJax.js?config=MML_CHTML' --dest=docs/index.html diss.xml

If you have github pages (https://help.github.com/articles/configuring-a-publishing-source-for-github-pages/) enabled for docs directory in the master branch
the `index.html` file will be automatically served at `http(s)://<username>.github.io/<projectname>`.
