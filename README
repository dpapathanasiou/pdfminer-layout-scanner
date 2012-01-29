PDFMiner (http://www.unixuser.org/~euske/python/pdfminer/index.html)
is a pdf parsing library written in Python by Yusuke Shinyama.

In addition to the pdf2txt.py and dumppdf.py command line tools, there
is a way of analyzing the content tree of each page programmatically.

This is a more complete example of programming with
PDFMiner, which continues where the default documentation
(http://www.unixuser.org/~euske/python/pdfminer/programming.html#layout)
stops.

This code is still a work-in-progress, with room for improvement.

Usage: import layout_scanner and call get_toc() for a list of the table
of contents, and get_pages() for the full text.

Here are some examples using the Python shell:

>>> import layout_scanner
>>> toc=layout_scanner.get_toc('/path/to/your/pdf-file.pdf')
>>> len(toc)
  ... should return the number of elements in the pdf document's table
  of contents (or 0 if there is no TOC)
>>> toc[0]
  ... a tuple containing the ordinal sequence and the title string,
  for example:
(1, u'Introduction')
>>> pages=layout_scanner.get_pages('/path/to/your/pdf-file.pdf')
>>> len(pages)
  ... should return the number of pages in the pdf document
>>> pages[0]
  ... a string of all the text on the first page

Room for Improvement

 * Column Merging - while the fuzzy heuristic I described works well for
 the pdf files I've parsed so far, I can imagine more complex documents
 where it would break-down (perhaps this is where the analysis should be
 more sophisticated, and not ignore so many types of pdfminer.layout.LT*
 objects).

 * Image Extraction - I'd like to be able to be at least as good as
 pdftoimages, and save every file in ppm or pnm default format, but I'm
 not sure what I could be doing differently

 * Title and Heading Capitalization - this seems to be an issue with
 PDFMiner, since I get similar results in using the command line tools,
 but it is annoying to have to go back and fix all the mis-capitalizations
 manually, particularly for larger documents.

 * Title and Heading Fonts and Spacing - a related issue, though probably
 something in my own code, is that those same title and paragraph headings
 aren't distinguished from the rest of the text. In many cases, I have to
 go back and add vertical spacing and font attributes for those manually.

 * Page Number Removal - originally, I thought I could just use a regex
 for an all-numeric value on a single physical line, but each document
 does page numbering slightly differently, and it's very difficult to
 get rid of these without manually proofreading each page.

 * Footnotes - handling these where the note and the reference both appear
 on the same page is hard enough, but doing it when they span different
 (even consecutive) pages is worse.

