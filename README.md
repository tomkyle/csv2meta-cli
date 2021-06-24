# csv2meta-cli

**Add individual meta data to multiple photos using CSV file** 

## Use case

If you just shot a series of different product photos, you'll usually import the pictures into Lightroom. Although you can then immediately add meta data for *the whole series,* there's no fast way to add *individual meta data* to each imported photo. That's what **csv2meta** is made for: Before importing to Lightroom, the script assigns individual *title, description,* and *keywords* from a CSV file to each image file. The images can then be imported, together with their indiviudal meta data.

The only thing, however, you are required to know is, which RAW file shows what. — The tool is not meant to add information that all images have in common and with which Lightroom excels, like photographer's name and legal hints. **csv2meta** rather helps you with those meta data that cannot be reasonably assigned as batch.

## Requirements

This bash script requires **Phil Harveys' [ExifTool](https://github.com/exiftool/exiftool).** 

```bash
$ brew install exiftool
```

## Installation

Clone the repo somewhere:

```bash
$ gh repo clone tomkyle/csv2meta-cli
```

You may want to add a symlink to your `~/bin` directory:

```bash
$ ln -s path/to/csv2meta-cli/bin/csv2meta csv2meta
```

## Usage

Dive into your photos directory. Run `csv2meta` with one or many CSV files as parameters. Make sure you've got an update of your photo files as the script overwrites the original files.

In later versions, the possibility to add *multiple* CSV file parameters may be removed in favour of useful behaviour options.

```bash
$ csv2meta CSV_FILE 
```

## Supported Meta tags

Existing keywords will be preserved. New keywords are added (avoiding tag doublettes).

| CSV column      | Image ID                   | Meta field        |
| --------------- | -------------------------- | ----------------- |
| **inputFile**   | The image file to write on |                   |
| **id**          | Object ID                  | `iptc:ObjectName` |
| **title**       | Title                      | `iptc:Headline`   |
| **description** | Description                | `mwg:Description` |
| **keywords**    | Keywords/tags              | `mwg:Keywords`    |

## Meta tags CSV file

**The CSV file must be tab-delimited; strings must not be quoted, hence no linebreaks in strings!** Sorry – I do not know how to handle delimiters dynamically with bash or deal with quoted strings in bash. If someone has a proper idea, please let me know :-)

It is not so important that the column names have exactly the same names as in this example. It rather is the column number with which the script identifies a certain tag value.

**[Example file](./examples/example.csv)** 

| inputFile    | id             | title                 | description                                    | keywords |
| ------------ | -------------- | --------------------- | ---------------------------------------------- | -------- |
| _DSC5186.NEF | artno_00981223 | Item Title for 981223 | This is an article description for item 981223 | foo,bar  |


## Interesting reads

**Rob Allen, 2019: [Setting title and caption with exiftool](https://akrabat.com/setting-title-and-caption-with-exiftool/)** – this article inspired me. Thanks Rob!

**Anthony Morris, 2021: [Obtaining Data From Images Using Exif: How To Automate The Process](https://hackernoon.com/obtaining-data-from-images-using-exif-how-to-automate-the-process-fzr33w3)**

**Nine Degrees Below, 2015 (2010): [ExifTool Commands for Image Organization](https://ninedegreesbelow.com/photography/exiftool-commands.html)**

**exiv2: https://exiv2.org/**

---

## The MIT License

Copyright 2021 Carsten Witt <tomkyle.net>

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the  "Software"), to deal in the Software without restriction, including  without limitation the rights to use, copy, modify, merge, publish,  distribute, sublicense, and/or sell copies of the Software, and to  permit persons to whom the Software is furnished to do so, subject to  the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,  EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF  MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY  CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,  TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE  SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
