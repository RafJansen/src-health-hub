# Manuscript Template for a polyglot project combined R and Python

This manuscript template is for a markdown-based publication with additional supporting notebook and markdown files, as well as supporting data, bibliography, and Quarto build configuration. It is based upon a new type of project in `Quarto`, Manuscripts. The final product will be rendered using `myst` for better quality

Get started with Quarto and Manuscript projects here: <https://quarto.org/docs/manuscripts/authoring/vscode.html/>.

# Project structure

## Source files

The primary source file for this template is a Quarto markdown article. This file may embed notebook cells from other sub-articles to use the output of these cells as figures. It may also reference content from other markdown sub-articles. All of these supplementary source notebooks/articles should be saved in the `notebooks/` folder. It also contains MyST blocks tagged in their metadata as `"part": "abstract"`, or `"part": "availability"` - these cells will be extracted from the document and included as the specified part in the built output.


## Data

By convention, all data should be saved in `data/` directory. There is nothing magic about this directory; references to your data from your notebook must still specify the correct relative path.

## Images

Similar to the `data/` directory, images for figures should be specified in `images/` directory.

## Bibliography

Bibliography entries may be specific in the document as described in the [Quarto documentation](https://quarto.org/docs/authoring/footnotes-and-citations.html#bibliography-files). They may be listed explicitly in BibTeX format, by convention in the file `references.bib`, and referenced by key using a `cite` MyST role. They may also be specified as inline DOI links. These do not require full bibliographic information; the data is fetched implicitly on build from the DOI.

# Configuration

## Quarto configuration

Configuration for the example is provided by the Quarto project file, `_quarto.yml`, and the YAML block (front matter) that appears with the article markdown document.

## MyST configuration

A `myst.yml` file must be provided to configure notebook metadata and exports. This includes authors, affiliations, licenses, keywords, and [much more](https://mystmd.org/guide/frontmatter). To specify which file will be added to the sidebar menu, specify in `_toc.yml`


# Best Practice to use
* Run Python code only: Go with Jupyter Notebook
* Run R code only: Go with Quarto document
* Mixed code is okay to write in Quarto, need to configure for use reticulate
* An alternative is to pass data through pyarrow
* Write the manuscript in Quarto document, with `mystmd` adjustment in order to render properly


# Step to setup

## R environment

* Run `renv::restore`
* To add new package, run `renv::install("package)`
* To update the lock fule, run `renv::snapshot()`
* Run `reticulate::use_virtualenv(here::here(".venv"))` to set the virtual environment for Reticulate


## Python environment

* Run `uv sync`
* To add new package, run `uv add package`