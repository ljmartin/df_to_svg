# exporting pandas dataframes to SVG

Pandas will export to `.csv` or `.html`, but these can't always be embedded in a document in a way that renders nicely. Jupyter notebook already renders html tables quite nicely, and it would be great to be able to export this to file.

This code emulates that rendering and outputs to `.svg`, making it infinitely high resolution with small filesize. 

# results

using matplotlib you can get a close approximation (see `./code/write_svg_matplotlib.ipynb`:

![mplsvg](./code/svg_matplotlib.svg "one")

the problem here (apart from the annoying vertical white lines) is the text is written in `<path>` objects, so it can't be highlighted and the file is larger than it needs to be. it's really just made up of rectangles, lines, and text so these can be written directly, like below. It's a tenth of the filsize and looks pretty close to a jupyter notebook rendering. (see `./code/write_svg_directly.ipynb`:

![dirsvg](./code/svg_directly.svg "two")

# even better

the real trick is to not do this at all. Most times I just want to copy a dataframe of hyperparameters or results or something into a word document. SVG format doesn't explicitly have a "table" - it's just a trick. But HTML does - and if you copy paste an html table into word it will copy is as a real table. It's only a few clicks to format this into a nice looking jupyter-style table. 

see `./code/write_html.ipynb` (solution is from https://stackoverflow.com/a/62716643/3089865)