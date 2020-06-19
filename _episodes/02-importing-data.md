---
title: "Importing data into AntConc"
teaching: 10
exercises: 0
questions:
- "How do I get data into AntConc?"
objectives:
- "Successfully import data into AntConc"
keypoints:
- "Use the `Open` option to import data"
- "You can import individual files or a folder"
- "AntConc works only with plain text files with the file extension .txt"
- "AntConc will not read common formats like .doc, .xls, or .pdf. You will need to convert these into .txt files to use AntConc."
---

## Importing data

>## What kinds of data files can I import?
>AntConc works only with plain text files with the file extension .txt. Other types of plain text file (e.g. .csv, .tsv, .xml) can be imported into AntConc if their file extension is changed to .txt, though - depending on your use case - doing so may not enable you to use the dataset as intended.
>More commonly, catalogue data will be processed so that particular fields can be analysed in AntConc. For information on how we processed the .txt files in [BM-MDG.zip](https://github.com/CatalogueLegacies/antconc.github.io/blob/gh-pages/data/BM-MDG.zip) for use in AntConc, see [*Creation of the BMSatire Descriptions corpus*](http://doi.org/10.5281/zenodo.3245037).
{: .callout}

>## Create your first AntConc project (using provided data)
>
> To import the data for the exercise below, follow the instructions in [Setup](https://cataloguelegacies.github.io/antconc.github.io/setup.html) to download the data and run AntConc.
>
>1. Once AntConc is launched, click `File` from the navbar and select `Open Files`
>2. Navigate to where you unzipped [BM-MDG.zip](https://github.com/CatalogueLegacies/antconc.github.io/blob/gh-pages/data/BM-MDG.zip), and whilst holding `ctrl` (`cmd` for Mac) click on each of the twelve .txt files (note: holding `shift` and  hitting the `down arrow` also works here). Alternatively, the `Open Dir` option in the `File` dropdown can be used to open a whole directory.
>3. Click `Open`. The names of the twelve .txt files will now appear in the left-hand `Corpus Files` pane.
>>* Note that although this module asks you to upload twelve .txt files, they are in fact a single corpus of around 1.2 million words seperated into parts containing roughly 100,000 words each. AntConc peforms better with many smaller files than it does with one large file, so if you expect to be working with a large corpus, or notice AntConc running slowly (or even crashing!), consider dividing up your corpus to achieve performance benefits.
>
{: .checklist}

### Going Further
* Files can be added to the AntConc 'corpus' at any time during analysis, just note that your results will change depending on the files listed under `Corpus Files`.
* If at any time you want to remove a file from AntConc, highlight it in the `Corpus Files` pane, go to the navbar, click `File` and select `Close Selected File(s)`.
