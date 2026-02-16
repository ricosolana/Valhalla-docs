# Avledet-docs
Avledet dedicated server documentation

ricosolana.github.io/Avledet-docs/

## Windows

super simple install via pip

## Linux

Create pip venv `python3 -m venv mkdocs-venv`

Use as source for terminal `source mkdocs-venv/bin/activate`

Necessary depends: 
 - `pip install mkdocs-tooltips`
 - `pip install mkdocs-material`

Clone Avledet to ~ `git clone https://github.com/ricosolana/Valhalla-docs`

Start mkdocs server `cd Valhalla-docs $$ python -m mkdocs serve --livereload`

View server in browser `http://127.0.0.1:8000/` or whatever serve displays
