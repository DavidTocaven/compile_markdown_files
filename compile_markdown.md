# How to convert markdown file into html and pdf files using github api


On Ubuntu/Debian systems. 3 different ways: 

## Using only `pandoc` 

### Install 

`pandoc` used natively latex to compile. latex is heavy to install.

pandoc installation : 

```
sudo apt update
sudo apt install pandoc
```

### Usage 

```
pandoc some_file.md -s -o some_file.pdf
```

The result is clear but do not have the nice github style. Classic latex style is used.

It's fast and command line only.

See `compile_markdown_pandoc.pdf` file to see the result on this file.



## Using `grip` and Firefox or Chrome 
Use grip to convert the markdown file into html render and firefox or chrome to save it as pdf.

### Install

`grip` needs to be installed. it's needing an active Internet connexion to use Github API.

```
sudo apt-get update 
sudo apt-get install -y grip 
```
the html-pdf convertion needs firefox or chrome installed.

### Usage

grip is used to render the file on a local server (localhost). 
1. Start `grip` using the following command : 
```
grip some_file.md
```

Once it is running a message will appears : 
```
 * Serving Flask app 'grip.app'
 * Debug mode: off
WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
 * Running on http://localhost:XXXX

```
Where `XXXX` is a port. 


2. Open `http://localhost:XXXX` on Firefox or Chrome. Ctrl+Click to open with default navigator.

3. Ctrl+P (or Parameters>Print...) to save open the print windows. Select Save to pdf as Destination.

4. (Optional) The looks is better with *Print headers and footers* unchecked and *Print backgrounds* checked.

5. Click on Save and chose a file name and path.


This way needs to open firefox or chrome and save to pdf using graphical interface. It is the better looking way.

See `compile_markdown_grip_firefox.pdf` file to see the result on this file with Firefox and  `compile_markdown_grip_chrome.pdf` with Chrome.



## Using `grip` and  `wkhtmltopdf`


It is using `grip` to convert the markdown file into a html file.  it's needing an active Internet connexion to use Github API.
Then `wkhtmltopdf` convert it into a pdf file.

### Install


`grip` needs to be installed.

```
sudo apt-get update 
sudo apt-get install -y grip 
```

`wkhtmltopdf` needs to be installed.

```
sudo apt-get update -y	
sudo apt-get install -y wkhtmltopdf
```
### Usage 

1. `grip` is used to export the markdown file into a html file.
```
grip some_file.md --export some_file.html

```
2. `wkhtmltopdf` is used to convert the html file into a pdf file 
```
wkhtmltopdf some_file.html some_file.pdf
```

This way is a command line only process, it's looks great but needs an active Internet connexion (`grip` use github renderer).

See `compile_markdown_grip_wkhtmltopdf.pdf` file to see the result on this file.