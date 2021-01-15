---
title: "Next Steps 2: Named Entity Recognition"
teaching: 30
exercises: 15
questions:
- "What is Named Entity Recognition (NER)?"
- "How do I apply NER to catalogue data?"
- "How can I use NER to analyse catalogue data in AntConc?"
objectives:
- "Provide an introduction to NER"
- "Show how data tagged through NER process can be used in AntConc"
keypoints:
- "NER tools create tagged datasets"
- "Used creatively, AntConc can be used to analyse tagged datasets"
---

## 1. Named Entity Recognition (NER)

NER is the process which identifies and tags what we consider to be entities, such as people, placenames, organisations, time etc. By identifying and classifying entities we can start asking questions about the frequency with which they are used or how they change over time. Applied to catalogue data NER can support collection management activities, as well as improve discovery and access.

In practice, NER tools take data (e.g. a plain text file or files) and add machine readable markers - or tags - to the data to enable analysis. For example, looking for people and place related entities in a description from the *[IAMS Photos](https://github.com/CatalogueLegacies/antconc.github.io/blob/gh-pages/data/IAMS_Photographs_1850-1950_selection3_wordlist.txt)* catalogue data, would result in the following output:

>  Close view of target hanging from wooden frame, with the Lhalu Mansion in the background. See Hugh Richardson, Ceremonies of the Lhasa Year (Serindia, London, 1993), pp. 56-57.

> Close view of target hanging from wooden frame, with the Lhalu/LOCATION Mansion/LOCATION in the background. See Hugh/PERSON Richardson/PERSON, Ceremonies of the Lhasa Year (Serindia, London/LOCATION, 1993),pp. 56-57.

Note here that - using the process and technologies described below - that the entity recognition assigns a tab to each part of an entity: the given name *and* the family name, each word in the given name of [a building](https://commons.wikimedia.org/wiki/File:Lhalu_mansion_near_Lhasa.jpg).

This means that we need to be careful in our analysis (e.g. a count of all `/PERSON` tags does not equal the total number of people in a corpus), but also gives us more powerful options, such as to use other tools - like [regular expressions](https://librarycarpentry.org/lc-data-intro/) - to find all person names with 3 or more parts.

Which is to say two things:

- First, NER is the beginning rather than the outcome of analysis.
- Second, some of that analysis needs to attend to the character and quality of the NER process.

There are different NER tools depending on whether you want to use predefined categories (Spacy) or develop your own by training a classifier on your data (Stanford NER). In this episode we use Stanford NER to tag entities. For an example of how to use NER with Spacy for text analysis, see Melanie Walsh's [tutorial](https://melaniewalsh.github.io/Intro-Cultural-Analytics/Text-Analysis/Named-Entity-Recognition.html#get-named-entities).

## 2. (optional) Generating NER tags with Stanford NER and Batchner

To generate NER takes using Stanford NER, we used the [Batchner](https://github.com/collectionslab/batchner) script developed by [Brandon Locke](https://github.com/brandontlocke). To do this yourself you need to be able to run commands in a Unix shell (e.g. Terminal for Linux or MacOS) or a Unix-like shell for Windows (e.g. [Git for Windows](https://gitforwindows.org/)).

Here you have three options:

1. If you are able to use the Unix Shell, completed this section of the episode.
2. If you are unable to use the Unix Shell but want to learn, see the [Software Carpentry](http://swcarpentry.github.io/shell-novice/) or [Library Carpentry](https://librarycarpentry.org/lc-shell/) tutorials on the Unix Shell, and come back here when you are ready.
3. If you unable to use the Unix Shell and are unwilling or able to learn how it use it right now, skip to Section 3 of this episode.

For those still here, start by making a new directory called something like "NER" somewhere in your file system: e.g. `cd Documents`, `mkdir NER`. Next go to the [Stanford NER](https://nlp.stanford.edu/software/CRF-NER.shtml#Download) page, download the latest version, and unzip so that the directory `stanford-ner-4.0.0` (or more recent version) is a sub-directory of your NER folder.

Now create another sub-directory in your NER folder for the *[IAMS Photos](https://github.com/CatalogueLegacies/antconc.github.io/blob/gh-pages/data/IAMS_Photographs_1850-1950_selection3_wordlist.txt)* data (e.g. `mkdir IAMS_data`) and put a copy of `IAMS_Photographs_1850-1950_selection3_wordlist.txt` in there.

Finally, do `touch batchner_markup.sh` to create a new document called "batchner_markup.sh" in your "IAMS_data" folder, open it, and paste the script below:

```#!/bin/sh
#echo "doc,entity,entityType,count" > entities.csv
for file in *.txt
do
############################
#If you're using Windows, delete the # from the start of line 8 and add a # to the start of line 9
############################
#nertext=$(java -mx600m -cp ../stanford-ner-2018-10-16/stanford-ner.jar edu.stanford.nlp.ie.crf.CRFClassifier -loadClassifier ../stanford-ner-2018-10-16/classifiers/english.all.3class.distsim.crf.ser.gz -textFile $file)
nertext=$(../stanford-ner-4.0.0/ner.sh $file)

#echo $nertext | egrep -o "(([[:alnum:]]|\.)+/ORGANIZATION([[:space:]]|$))+" | sed 's/\/ORGANIZATION//g' | sort | uniq -c | awk -v name=${file%%.*} '{printf name ","; for (i = 2; i < NF; i++) printf $i " "; printf $NF; printf "," "organization" ","; printf $1;  print ""}' >> entities.csv
echo $nertext | egrep "(([[:alpha:]]|\.)*/PERSON([[:space:]]|$))+" | sed 's|/ORGANIZATION||g' | sed 's|/LOCATION||g' | sed 's|/O||g' >> "$(basename "$file")_people.txt"
echo $nertext | egrep "(([[:alnum:]]|\.)*/LOCATION[[:space:]](,[[:space:]])?)+" | sed 's|/ORGANIZATION||g' | sed 's|/PERSON||g' | sed 's|/O||g' >> "$(basename "$file")_places.txt"
done
```
Head to the [Batchner](https://github.com/collectionslab/batchner) page for more on how this works (thanks Brandon!), but - in short - what it does is takes input of individual .txt files in a given directory (so in our case `IAMS_Photographs_1850-1950_selection3_wordlist.txt`), invokes the NER process (`ner.sh`) and outputs two .txt files, one for people and one for places, each containing data marked up with `/PERSON` and `/LOCATION` respectively.

To run the script enter `sh batchner_markup.sh` and hit return. After a little time, the script will finish and you'll have two new files in your "IAMS_data" directory.

>## Common failures
>1. Your machine is not configured to run `.sh` files as executables. This is common error the first time you attempt to run a `.sh` file on a new machine. The fix depends on your system, but generally requires you to set the permissions to executable (e.g. for [Ubuntu](https://askubuntu.com/a/38666))
>2. The path to `ner.sh` is incorrect. The script above is written for Stanford NER Version 4.0.0 and so line 9 points to the path `../stanford-ner-4.0.0/ner.sh`. For later versions replace `stanford-ner-4.0.` with the directory name that appeared when you unzipped [Stanford NER](https://nlp.stanford.edu/software/CRF-NER.shtml#Download) into your `NER` directory.
>3. Re-running the script. Line 3 of the script (`for file in *.txt`) invokes **all** .txt files in a directory. This is so that you can run an NER process on multiple .txt files simultaneously (hence the "batch" in [Batchner](https://github.com/collectionslab/batchner)). This means that if you run the process, get outputs, and then run it again, `batchner_markup.sh` will rerun over your marked up files. We don't want this. To avoid this when re-running `batchner_markup.sh` you have three options: move outputs to another folder; rewrite Line 3 to specify target files; rewrite Line 13 to redirect outputs. Note that to differentiate outputs - say from different versions of [Stanford NER](https://nlp.stanford.edu/software/CRF-NER.shtml#Download) - you can rename the output files in Lines 12 and 13. And that if you remove the commenting out from Lines 1 and 11 (delete the leading `#` for each), you can an alternative use of [Stanford NER](https://nlp.stanford.edu/software/CRF-NER.shtml#Download): a spreadsheet of all 'organisations' (e.g. "2nd Punjab Cavalry") found by the NER process and a count of their occurences (for "2nd Punjab Cavalry", twice).
{: .callout}

## 3. Using NER tagged catalogue data in AntConc

If you decided to generate your own NER tags with Stanford NER and Batchner, you will now have two new versions of the *[IAMS Photos](https://github.com/CatalogueLegacies/antconc.github.io/blob/gh-pages/data/IAMS_Photographs_1850-1950_selection3_wordlist.txt)* dataset: `IAMS_Photographs_1850-1950_selection3.txt_people.txt` and `IAMS_Photographs_1850-1950_selection3.txt_places.txt`.

If you did not generate your own NER tags with Stanford NER and Batchner, download the files now: [people.txt](https://github.com/CatalogueLegacies/antconc.github.io/blob/gh-pages/data/IAMS_Photographs_1850-1950_selection3.txt_people.txt), [places.txt](https://github.com/CatalogueLegacies/antconc.github.io/blob/gh-pages/data/IAMS_Photographs_1850-1950_selection3.txt_places.txt).

The first is the *[IAMS Photos](https://github.com/CatalogueLegacies/antconc.github.io/blob/gh-pages/data/IAMS_Photographs_1850-1950_selection3_wordlist.txt)* with the tag `/PERSON` after each string Stanford NER defined as the name of a person. The second is the *[IAMS Photos](https://github.com/CatalogueLegacies/antconc.github.io/blob/gh-pages/data/IAMS_Photographs_1850-1950_selection3_wordlist.txt)* with the tag `/LOCATION` after each string Stanford NER defined as the name of a place.

We can use these tags to search for the contexts in which people and places - proper names that make much of the long tail of infrequent vocabulary that we observed in [Episode 5](https://cataloguelegacies.github.io/antconc.github.io/05-wordlists/index.html) - appear in the [IAMS Photos](https://github.com/CatalogueLegacies/antconc.github.io/blob/gh-pages/data/IAMS_Photographs_1850-1950_selection3_wordlist.txt)* catalogue.

To do this, first adjust your settings from [Episode 7](https://cataloguelegacies.github.io/antconc.github.io/07-collocates/index.html), so that under `Token Definition` in `Global Settings`, only `Punctuation` is unchecked.

>## Adjusting settings for the task at hand
>Keeping `Punctuation` checked would lead to the forward slash used to tag people and places being seen by AntConc as seperate from `/PERSON` and `/LOCATION` respectively. This then is a case where we adjust the AntConc settings for the task at hand. We must remain mindful, however, to carefully compare any results from this analysis with results generated from analysis using different settings.
{: .callout}

Next, clear the `Corpus Files` panel in AntConc and open `IAMS_Photographs_1850-1950_selection3.txt_people.txt` (`File`, `Open File(s)...`), go to the `Word List` tool, and hit `Start`. The `Word List` outputs should show `PERSON` as the second more frequent word type (frequency = 45,574).

Now go to the `Collocates` tool and search for `by */PERSON` with `Words` and `Case` checked, `Window Span` set to `1L` and `0`, and `Min. Collocate Frequency` set to 20. This will search for the most common words 5 places left of the string `by */PERSON`, where `*` is any text, likely a name part.

>## I tried something and I think I've broken AntConc
>Remember in Episode 5 when we asked [Is AntConc thinking or has it crashed?](https://cataloguelegacies.github.io/antconc.github.io/05-wordlists/index.html#interacting-with-a-word-list). Well, using NER tagged data in AntConc is a good example of data that can make AntConc hang. For example, search `/PERSON` in the `Collocates` tool and you may be waiting a while. With data like this, it is best to look at the data, start with complex queries likely to return a handful of results, and work up to bigger queries (or, if you want to be productive whilst waiting for AntConc, run AntConc on a second machine!). Note that we've sculpted our examples so AntConc shouldn't hang or crash, but it may do so depending on the age of your machine.
{: .callout}

The results tell us the kinds of activities for which people are given agency: they are likely agents ("probably by", "possibly by"), they are photographers ("photographed by"), and they are architects ("built by"). And most of these agents are involved in the production of the photography rather than the production of features in photographs. If we click on `taken`, we observe that all 127 concordance lines use "taken" in the context of photography. Only the 35 concordance lines associated with the phrase `built by */PERSON` refer consistency to the subjects of photographs in the *[IAMS Photos](https://github.com/CatalogueLegacies/antconc.github.io/blob/gh-pages/data/IAMS_Photographs_1850-1950_selection3_wordlist.txt)* catalogue.

>## Know Your Data
>The concordance lines for `built by */PERSON` also indicate to us that Stanford NER has successful identified many Middle Eastern and South Asian given and family names as names and in turn given them `/PERSON` tags. Whilst it tells us nothing about false-negatives (Middle Eastern and South Asian given and family names that Stanford NER has not given `/PERSON` tags), it is promising and a result we would continue to monitor as our analysis deepens. AntConc then is a useful tool for testing the results of computational processes  like NER in gradual and situated manner. So even if you hadn't planned to use corpus linguistics to understand your catalogue data, running some searches in a graphical tool like AntConc can help you get a better sense of the quality of computational processes you've run over that catalogue data.
{: .callout}

>## Task 1: Using the `Concordance` tool and `IAMS_Photographs_1850-1950_selection3.txt_people.txt`, create concordance lines for all the place names followed by the string " towards".
>* Think about how to adjust the `Kwic Sort` settings to best display your results.
>
>>## Solution
>>
>>1. Use the search term `*/LOCATION towards` with `Words` and `Case` checked, and `Kwic Sort` set to `Level 1` equals `0`, `Level 2` equals `1R`, and `Level 3` equals `2R`.
>>2. Hit `Start`. AntConc will return 154 hits.
>>>* Browsing through the results you will notice a few quirks of the Stanford NER process. First, it tags each part of multi-part location names: "Upper/LOCATION Bosphorus/LOCATION" (line 17) "Galata/LOCATION Bridge/LOCATION" (line 19),"Chatham/LOCATION Dockyard/LOCATION" (line 24). Second, it has missed some locations: "Findikli" (line 6), "Rumeli Hisari" (line 7), "Satti Chaura Ghat" (line 28), likely because - as is the case in these three cases - Stanford NER does not contain these are varient spellings of each place. Again, know your data.
>{: .solution}
{: .challenge}

>## Task 2: Using the `Concordance` tool and `IAMS_Photographs_1850-1950_selection3.txt_people.txt`, explore the presence of women in the descriptions.
>* For example, you can start with constructing queries using "Lady" for which there are 547 results in the `Word List`.
>
>>## Solution
>>
>>1. 
>>2. 
>>>* Notice how not all occurances of "Lady" have been recognised as names (as they were probably tagged as locations instead), such as "Lady Reading", "Lady Sydenham"; also the Stanford NER has not tagged names used in the possessive case: "Lady Waterford's". Another observation to be made is that the NER process tags "Lady/PERSON" when followed by a surname, "Lady/PERSON Butler/PERSON", unlike when "Lady" is followed by a first name, "Lady Alice/PERSON".  
>{: .solution}
{: .challenge}
