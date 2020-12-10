---
title: "Next Steps 2: Named Entity Recognition (**not yet developed**)"
teaching: 5
exercises: 15
questions:
- "What is Named Entity Recognition (NER)?"
- "How do I apply NER to catalogue data?"
- "How can I use NER to analyse catalogue data in AntConc?"
objectives:
- "FIXME"
keypoints:
- "FIXME"
---

## Named Entity Recognition (NER)

What it does: add tags to a corpus (show an e.g.). We can put tags and corpus linguistics together in interesting ways. For example, if you wanted to know the language used around all places, we can do that, as the tags give us an anchor to search around. In AntConc, we'd search for the tag and then look at the concordance.

## (optional) Generating NER tags with Stanford NER and Batchener

- need shell foobar
- mk folder NER
- unzip download in it https://nlp.stanford.edu/software/CRF-NER.shtml#Download
- put custom batchner in there (with thanks to https://github.com/collectionslab/batchner)
- put data in there
- run `sh SCRIPT`. Output 'DATASET_people.txt' and 'DATASET_places.txt'

## Using NER tagged catalogue data in AntConc

If you decided to generate your own NER tags with Stanford NER and Batchener, you will now have two new versions of the *[IAMS Photos](https://github.com/CatalogueLegacies/antconc.github.io/blob/gh-pages/data/IAMS_Photographs_1850-1950_selection3_wordlist.txt)* dataset: `IAMS_Photographs_1850-1950_selection3.txt_people.txt` and `IAMS_Photographs_1850-1950_selection3.txt_places.txt`.

If you did not generate your own NER tags with Stanford NER and Batchener, download the files now: [people.txt](https://github.com/CatalogueLegacies/antconc.github.io/blob/gh-pages/data/IAMS_Photographs_1850-1950_selection3.txt_people.txt), [places.txt](https://github.com/CatalogueLegacies/antconc.github.io/blob/gh-pages/data/IAMS_Photographs_1850-1950_selection3.txt_places.txt).

The first is the *[IAMS Photos](https://github.com/CatalogueLegacies/antconc.github.io/blob/gh-pages/data/IAMS_Photographs_1850-1950_selection3_wordlist.txt)* with the tag `/PERSON` after each string Stanford NER defined as the name of a person. The second is the *[IAMS Photos](https://github.com/CatalogueLegacies/antconc.github.io/blob/gh-pages/data/IAMS_Photographs_1850-1950_selection3_wordlist.txt)* with the tag `/LOCATION` after each string Stanford NER defined as the name of a place.

We can use these tags to search for the contexts in which people and places - proper names that make of much of the long tail of infrequent vocabulary that we observed in [Episode 5](https://cataloguelegacies.github.io/antconc.github.io/05-wordlists/index.html) - appear in the [IAMS Photos](https://github.com/CatalogueLegacies/antconc.github.io/blob/gh-pages/data/IAMS_Photographs_1850-1950_selection3_wordlist.txt)* catalogue.

To do this, first adjust your settings from [Episode 7](https://cataloguelegacies.github.io/antconc.github.io/07-collocates/index.html), so that under `Token Definition` in `Global Settings`, only `Letter` and `Number` are selected.

Next, clear the `Corpus Files` panel in AntConc and open `IAMS_Photographs_1850-1950_selection3.txt_people.txt` (`File`, `Open File(s)...`), go to the `Word List` tool, and hit `Start`

- Global Settings. Set to 'Token Definition' of 'letter' only.
- Tool Prefs. For Wordlist, untick 'treat all as lower case' as usual.
- Then in Concordance tab search: `by */PERSON` with words and case selected, and Level 1 set to 1L
- This is a good start on the kind of contexts in which people appear (and is an essay search for antconc!)
