# csv2meta-cli

**Add individual meta data to a multiple photos using CSV file** 

## Use case

If you just shot a series of different product photos, there's after importing to Lightroom no simple way to add individual meta data to each of them. **csv2meta** script takes a CSV file and assigns individual *title, description,* and *keywords* to each image file – before importing to Lightroom. The only thing you are required to know is, which RAW file shows what.

The tool is not meant to add information that have all images in common, like photographer's name and legal hints. It rather helps you with that kind of meta information that can't be assigned as batch.

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

Dive into your photos directory. Run `csv2meta` with one or many CSV files as parameters.

```bash
$ csv2meta CSV_FILE 
```

## Supported Meta tags

Existing keywords will be preserved. New keywords are added. Doublettes are removed.

| CSV column      | Image ID                   | Meta field        |
| --------------- | -------------------------- | ----------------- |
| **inputFile**   | The image file to write on |                   |
| **id**          | Object ID                  | `iptc:ObjectName` |
| **title**       | Title                      | `iptc:Headline`   |
| **description** | Description                | `mwg:Description` |
| **keywords**    | Keywords/tags              | `mwg:Keywords`    |

## Meta tags CSV file

**The CSV file must be tab-delimited; strings must not be quoted, hence no linebreaks in strings!** Sorry – I do not know how to handle delimiters dynamically with bash or deal with quoted strings in bash. If someone has a proper idea, please let me know :-)

**[Example file](./examples/example.csv)** 

| inputFile    | id             | title                 | description                                    | keywords |
| ------------ | -------------- | --------------------- | ---------------------------------------------- | -------- |
| _DSC5186.NEF | artno_00981223 | Item Title for 981223 | This is an article description for item 981223 | foo,bar  |


## Interesting reads

**Rob Allen, 2019: [Setting title and caption with exiftool](https://akrabat.com/setting-title-and-caption-with-exiftool/)**

**Anthony Morris, 2021: [Obtaining Data From Images Using Exif: How To Automate The Process](https://hackernoon.com/obtaining-data-from-images-using-exif-how-to-automate-the-process-fzr33w3)**

**Nine Degrees Below, 2015 (2010): [ExifTool Commands for Image Organization](https://ninedegreesbelow.com/photography/exiftool-commands.html)**

**exiv2: https://exiv2.org/**

