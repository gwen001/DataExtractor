<h1 align="center">DataExtractor</h1>

<h4 align="center">A Burp Suite extension to extract data from source code while browsing.</h4>

<p align="center">
    <img src="https://img.shields.io/badge/python-v3-blue" alt="python badge">
    <img src="https://img.shields.io/badge/license-MIT-green" alt="MIT license badge">
    <a href="https://twitter.com/intent/tweet?text=https%3a%2f%2fgithub.com%2fgwen001%2fDataExtractor%2f" target="_blank"><img src="https://img.shields.io/twitter/url?style=social&url=https%3A%2F%2Fgithub.com%2Fgwen001%2FDataExtractor" alt="twitter badge"></a>
</p>

<!-- <p align="center">
    <img src="https://img.shields.io/github/stars/gwen001/DataExtractor?style=social" alt="github stars badge">
    <img src="https://img.shields.io/github/watchers/gwen001/DataExtractor?style=social" alt="github watchers badge">
    <img src="https://img.shields.io/github/forks/gwen001/DataExtractor?style=social" alt="github forks badge">
</p> -->

---

## Features

- in scope parsing  
- file extensions to ignore  
- files exclusion based on regexp  
- multi tabs for multiple purpose  
- data extraction based on regexp  
- results exclusion based on regexp  
- data export  

## Install

First of all, ensure you have [Jython](https://www.jython.org/) installed and loaded and setup before the next step.

- clone this repository  
- in the Extender tab, click the button `Add`  
- set `Extension type` to `Python`  
- browse to the cloned folder and select `DataExtractor.py` as the `Extension file`  

The extension should load and is now ready to perform a passive scan.

## Help

- A single click on any `Apply changes` button will save all your settings

- Settings / Follow scope rules:
do not parse out of scope urls as defined in the target scope tab

- Settings / Remove duplicates:
remove duplicates from data tabs

- Settings / Ignore extensions:
do not parse urls with those extensions

- Settings / Ignore files:
do not parse those files (regexps allowed), JSON format: `["jquery.min.js",".png",...]`  
important: regexps here are case insentitive by design

- Custom tab / Config:
list of regexps to search, JSON format: `{"key1":"regexp1","?key2":"regexp2",...}`  
if the first character of the key is a `?` or a `*`, the key will not be printed in the data tab  
important: regexps here are NOT case sentitive, use `(?i)` as a prefix of the whole regexp to make it insentitive  
important: you should have at least 1 group configured using parenthesis `()` to be able to catch something,
`group(1)` is used as a result so to ignore a group, please use `?:` as a prefix of the group itself

- Custom tab / Remove from results:
remove those results from data tab (regexps allowed), JSON format: `["http://$","application/javacript",...]`  
important: regexps here are case insentitive by design

## Examples of regexp config

All config textareas should be valid JSON format associative arrays (key/value), so take care of every single comma and quote.
As soon as you save your settings, a check is performed so you can ensure that everything is fine in the output/errors tab of the exender tab.  
Note that all keys should be different.

Subdomains (case insensitive):
```
{
  "*dummykey1":"(?i)(([0-9a-z_\\-\\.]+)\\.github\\.com)"
}
```

AWS keys ans Slack tokens (case sensitive):
```
{
  "slack token": "(xox[pboa]-[0-9]{10,12}-[0-9]{10,12}(-[0-9]{10,12})?-[a-zA-Z0-9]{24,32})",
  "aws key": "((AKIA|A3T|AGPA|AIDA|AROA|AIPA|ANPA|ANVA|ASIA)[A-Z0-9]{12,})"
}
```

See the file [myregexp](https://github.com/gwen001/DataExtractor/blob/main/myregexp) to get all my regexps.

## Example of ignore/remove

All ignore/remove textareas should be valid JSON format arrays, so take care of every single comma and quote.
As soon as you save your settings, a check is performed so you can ensure that everything is fine in the output/errors tab of the exender tab.  

```
[
  ".png$",
  "application/javascript",
  "googleapis.com",
  "sha256.*$"
]
```

---

<img src="https://raw.githubusercontent.com/gwen001/DataExtractor/main/settings.png">
<img src="https://raw.githubusercontent.com/gwen001/DataExtractor/main/endpoints.png">
<img src="https://raw.githubusercontent.com/gwen001/DataExtractor/main/keys.png">
<img src="https://raw.githubusercontent.com/gwen001/DataExtractor/main/subdomains.png">

---

Feel free to [open an issue](/../../issues/) if you have any problem with the script.  

