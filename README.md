# iOS-BibTeX-Shortcuts
This is a collection of some iOS Shortcuts I’ve put together for managing my BibTeX library when away from my desktop.

These Shortcuts are all designed to work with my own workflow. I maintain a single master library file with all my references, as well as a master folder with all associated pdfs (named the same as their associated BibTeX key). I also use the "keywords" field for specifying topic groupings. JabRef then handles the rest (with pdfs linked via the "file" field in the .bib file).

Some of the steps in these Shortcuts (like the regular expressions for finding entries) might prove useful for your own workflow, so please feel free to use and/or modify any part to suit your own needs.

The only way to easily share iOS Shortcuts (as far as I can tell) is by iCloud link. Please feel free to use and modify these "scripts" according to your own workflow.

Please forgive the somewhat messy nature of these. The "drag-and-drop" nature of the Shortcuts scripting "language" isn't really amenable to clean coding, and I don't know what the best style practices are for this system. 

## Import a BibTeX entry based on DOI

https://www.icloud.com/shortcuts/ee4db17042884dc6acc03f6f7afb165e

This script asks for a DOI as input, then requests a BibTeX entry from dx.doi.org. It then asks for a new BibTeX key, keywords (which I use for grouping entries in JabRef), and modifies the entry appropriately. It then adds a timestamp field at the end of the entry. 

Finally, it puts the entry at the top of .bib file (dropbox file path of the bib file can be set at the top of the script). Note the script expects a .bib file formatted by JabRef. A generic .bib file may have unexpected behavior.

## Add a PDF file to an existing entry

https://www.icloud.com/shortcuts/591cc01e024f4b3db413a89e1af07ca0

This script should be set to be runnable from the "share" menu when viewing a pdf. The script will ask for BiBTeX key, and search for that entry in the .bib file (file path set at the beginning of the script). 

If the entry doesn't exist, the script will return an error. Otherwise, it will check if a linked file already exists. If so, it will ask whether or not to overwrite the previous file. If yes (or no file link existed), the script will add a file field with the appropriate path the the new file, and save the pdf to that location. (The location of pdf files must be set at the beginning of the script.)

## Possible improvements

A good chunk of this probably could have been implemented more elegantly in Python using the Pythonista app, but last I tried, it wasn't obvious if a pdf could be passed to Pythonista from a Shortcut. A hybrid Shortcut with Python handling all the editing of the bib file and Shortcuts handling the saving the pdf might have been better... 

Shortcuts also very easily handles interfacing with files in Dropbox, whereas a Python script would necessitate the extra step of getting a Dropbox API token for the app. I suppose it might be possible to have shortcuts pull the file from Dropbox, pass it to Pythonista, then have Pythonista pass the modified text back to Shortcuts for saving.


