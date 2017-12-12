# Render Page

CLI tool to render a page using Puppeteer

## Install

`npm install -g renderpage`

## Usage

```
$ renderpage -h
Options:
  --help, -h      Show help                                            [boolean]
  --version, -v   Show version number                                  [boolean]
  --url, -u       Url of the page to render                           [required]
  --ua            User agent to send to the page
         [default: "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36
                        (KHTML, like Gecko) Chrome/60.0.3112.113 Safari/537.36"]
  --wait-for, -w  A list of selectors to wait for                        [array]
  --timeout, -t   How long to wait for the page to be rendered
                                                       [number] [default: 30000]
  --script, -s    Path to a script to run on the page
  --no-sandbox    Disable the Chrome sandbox mode                      [boolean]
  --json, -j      Output a json object rather than outputting the page (the page
                  will be saved to a file)                             [boolean]
  --output, -o    Path to save the rendered page
```

## Examples

### Render Page to a file

`renderpage -u "http://example.com" -o ./output.html`

### Run a script on a page

`renderpage -u "http://example.com" -s ./script.js --json`

script.js:

`window.innerWidth;`

Result:

```
{
  "originalUrl": "http://example.com/",
  "url": "http://example.com/",
  "status_code": 200,
  "file": "/tmp/91e3e8390998ca280a46db76f82e5fb3.html",
  "script_result": 800
}
```

### Wait for elements on a page to appear

`renderpage -u "http://example.com" --wait-for h1 p`

## License

Copyright (C) 2017 [PureCars](http://purecars.com)

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License version 3, as published
by the Free Software Foundation.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranties of MERCHANTABILITY, SATISFACTORY QUALITY, or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program.  If not, see <http://www.gnu.org/licenses/>.
