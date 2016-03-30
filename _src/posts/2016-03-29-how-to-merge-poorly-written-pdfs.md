    Title: How to merge poorly written PDFs
    Date: 2016-03-29T00:00:00
    Tags: problems, solutions, software, text

As an employee of the [Apache Software Foundation](https://apache.org) I 
obviously support the writing open source software.  But my role hasn't required
me to commit code to anything outside of work for any Apache projects yet. But 
as a community member I thought it would be a good idea to go ahead and sign the [ICLA](https://www.apache.org/dev/new-committers-guide.html)

<!-- more -->

The process goes something like this:

1. Download [PDF](https://www.apache.org/licenses/icla.pdf)
2. Edit and sign
3. Send the PDF to secretary [at] apache (dot) org

Downloading the PDF, check.  I'm a trained sysadmin so naturally I spun up a VM,
installed docker, wrote a Dockerfile to download a file, virus check it against
clamav, multiple online sites and then hash the file and put it in a shared
volume which is NFS mounted to my laptop.  Or something.

Turns out that editing PDFs on linux is pretty much a pain in the
ass but the go to seems to be GIMP.  Whether I'm bad at GIMP (this is true) or
GIMP's UI is pretty convoluted (this is also true) I could not figure out how to
edit a multipage PDF.  However, when you load the PDF it asks which pages you
want to import.  So importing each page one at a time solved this first problem.
Adding text was a simple matter of matching the font size and clicking too high
on the text entry fields.  Signing was also easy to make my signature look like
it did when I was 5.

Exporting each page as a PDF leaves me with 2 PDFs which I'll need to join.  A
cursory search found me this page from [linux.com](https://www.linux.com/news/software/applications/8229-putting-together-pdf-files).
Being from 2004 made me suspicious that it would still work; seeing it was using
Ghostscript convinced me that it would probably work.  A funny side note, I use
a bash alias `gs` for `git status` since that is a very common command in my
daliy workflow.  Forgetting that ghostscript's binary is actually named `gs`
gave me a funny error related to git!  So I replaced `gs` with `\`which gs`\` and
the command worked wonders to join my 2 single page PDFs.

`\`which gs`\` -dBATCH -dNOPAUSE -q -sDEVICE=pdfwrite -sOutputFile=icla.pdf icla-pg1.pdf icla-pg2.pdf

I'm sure I'm being dumb and there is a better tool for the job, but for putting
information into a PDF and joining a couple pages this worked pretty well.
