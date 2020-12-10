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

To do this, first adjust your settings from [Episode 7](https://cataloguelegacies.github.io/antconc.github.io/07-collocates/index.html), so that under `Token Definition` in `Global Settings`, only `Punctuation` is unchecked.

>## Adjusting settings for the task at hand
>Keeping `Punctuation` checked would lead to the forward slash used to tag people and places being seen by AntConc as seperate from `/PERSON` and `/LOCATION` respectively. This then is a case where we adjust the AntConc settings for the task at hand. We must remain mindful, however, to carefully compare any results from this analysis with results generated from analysis using different settings.
{: .callout}

Next, clear the `Corpus Files` panel in AntConc and open `IAMS_Photographs_1850-1950_selection3.txt_people.txt` (`File`, `Open File(s)...`), go to the `Word List` tool, and hit `Start`. The `Word List` outputs should show `PERSON` as the second more frequent word type (frequency = 45,574).

Now go to the  `Collocates` tool and search for `by */PERSON` with `Words` and `Case` checked, `Window Span` set to `1L` and `0`, and `Min. Collocate Frequency` set to 20. This will search for the most common words 5 places left of the string `by */PERSON`, where `*` is any text, likely a name part.

The results tell us the kinds of activities for which people are given agency: they are likely agents ("probably by", "possibly by"), they are photographers ("photographed by"), and they are architects ("built by"). And most of these agents are involved in the production of the photography rather than the production of features in photographs. If we click on `taken`, we observe that all 127 concordance lines use "taken" in the context of photography. Only the 35 concordance lines associated with the phrase `built by */PERSON` refer consistency to the subjects of photographs in the *[IAMS Photos](https://github.com/CatalogueLegacies/antconc.github.io/blob/gh-pages/data/IAMS_Photographs_1850-1950_selection3_wordlist.txt)* catalogue.

>## Know Your Data
>The concordance lines for `built by */PERSON` also indicate to us that Stanford NER has successful identified many South Asian given and family names as names and in turn given them `/PERSON` tags. Whilst it tells us nothing about false-negatives (South Asian given and family names that Stanford NER has not given `/PERSON` tags), it is promising and a result we would continue to monitor as our analysis deepens. AntConc then is a useful tool for testing the results of computational processes  like NER in gradual and situated manner. So even if you hadn't planned to use corpus linguistics to understand your catalogue data, running some searches in a graphical tool like AntConc can help you get a better sense of the quality of computational processes you've run over that catalogue data.
{: .callout}
