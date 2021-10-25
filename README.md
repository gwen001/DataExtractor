# DataExtractor

A simple Burp Suite extension to extract datas from source code.  

# Features

- in scope parsing  
- file extensions to ignore  
- files exclusion based on regexp  
- multi tabs for multiple purpose  
- datas extraction based on regexp  
- datas exclusion based on regexp  
- datas export  

# Install

First of all, ensure you have JPython loaded and setup before installing.

- clone this repository  
- in the Extender tab, click the button "Add"  
- set "Extension type" to "Python"  
- browse to the cloned folder and select `DataExtractor.py` as the "Extension file"  

The extension should load and is now ready to perform a passive scan.

# Help

A click on any "Apply changes" button will save all your settings.

- Settings / Follow scope rules:
do not parse out of scope urls as defined in the target scope tab

- Settings / Remove duplicates:
remove duplicates from datas tabs

- Settings / Ignore extensions:
do not parse urls with those extensions

- Settings / Ignore files:
do not parse those files (regexps allowed), JSON format: ["jquery.min.js",".png",...]
important: regexps here are case insentitive by design

- Custom tab / Config:
list of regexps to search, JSON format: {"key1":"regexp1","?key2":"regexp2",...}
if the first character of the key is a '?'or a '*', the key will not be printed in the datas tab
important: regexps here are NOT case sentitive, use "(?i)" as a prefix of the whole regexp to make it insentitive
important: you should have at least 1 group configured using parenthesis "()" to be able to catch something,
group(1) is used as a result so to ignore a group, please use "?:" as a prefix of the group itself

- Custom tab / Remove from results:
remove those results from datas tab (regexps allowed), JSON format: ["http://$","application/javacript",...]
important: regexps here are case insentitive by design

# Examples

aaaa


# Screenshots

<img src="https://raw.githubusercontent.com/gwen001/DataExtractor/main/settings.png">
<img src="https://raw.githubusercontent.com/gwen001/DataExtractor/main/endpoints.png">
<img src="https://raw.githubusercontent.com/gwen001/DataExtractor/main/keys.png">
<img src="https://raw.githubusercontent.com/gwen001/DataExtractor/main/subdomains.png">
