# cli-csv2meta


## Installation

Clone the repo somewhere. You may want to add a symlink to your `~/bin` directory:

```bash
$ ln -s path/to/csv2meta/bin/csv2meta csv2meta
```

## Usage

Dive into your photos directory. Run `csv2meta` one or many CSV files as parameters.

```bash
$ csv2meta CSV_FILE 
```

## Meta tags

These meta tags will be written:

Image ID – `iptc:ObjectName`
Image Title – `iptc:Headline`
Image Description – `mwg:Description`
Image keywords/tags – `mwg:Keywords`

Existing keywords will be preserved. New keywords are added. Doublettes are removed.

## The CSV file

**The CSV file must be tab-delimited; strings must not be quoted. Sorry.** 
The author does not know how to handle delimiters dynamically or deal with quoted strings in bash. If someone has a proper idea, please let me know :-)

**[Example file](./examples/example.csv)** 

| inputFile    | id             | title                 | description                                    | keywords |
| ------------ | -------------- | --------------------- | ---------------------------------------------- | -------- |
| _DSC5186.NEF | artno_00981223 | Item Title for 981223 | This is an article description for item 981223 | foo,bar  |



---


## Interesting reads

**Rob Allen, 2019: [Setting title and caption with exiftool](https://akrabat.com/setting-title-and-caption-with-exiftool/)**

**Anthony Morris, 2021: [Obtaining Data From Images Using Exif: How To Automate The Process](https://hackernoon.com/obtaining-data-from-images-using-exif-how-to-automate-the-process-fzr33w3)**

**Nine Degrees Below, 2015 (2010): [ExifTool Commands for Image Organization](https://ninedegreesbelow.com/photography/exiftool-commands.html)**

**exiv2:** https://exiv2.org/

**ExifTool**: https://github.com/exiftool/exiftool
