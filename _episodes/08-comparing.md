---
title: "Next Steps 1: comparing corpora (**not yet developed**)"
teaching: 30
exercises: 60
questions:
- "How can I use AntConc to compare multiple sets of catalogue data?"
- "How can I compare curatorial 'voice' to general language?"
- "What are the benefits of comparison?"
objectives:
- "Show how to use wordlists to perform an initial comparison of two or more corpora."
- "Show how to work with Keyword lists in AntConc."
keypoints:
- ""
---

## Why Compare

This episode introduces potential next steps for comparing corpora. Each of the three sections are only intended as jumping off points, rather than comprehensive accounts of their methods. This is because the method of comparison will be shaped by your initial lingustic analysis: as we wrote in [Episode 1](https://cataloguelegacies.github.io/antconc.github.io/01-introduction/index.html), corpus lingustics is therefore an iterative study of text, where a phenomenon suggested by one output is tested and refined by the next.

In the context of catalogue data, there are a number of reasons to compare corpora: because comparison provides an alternative point of analysis for defining the features of a given catalogue data under analysis; because a given catalogue can be broken into subsets that are then analysed comparatively (e.g. taking an exemplar or baseline collection of catalogue data to better understand the linguistic features of given subset in need of attention); because comparisons of catalogue data with other types of texts - e.g. everyday speech - can helpfully tease out the "special language" that might form the basis of, say, a guide to cataloguing at your institution.

Used creatively, AntConc can provide the basic toolset required to undertake a variety of comparative analyses, though the deeper your comparing goes, the more you may find yourself needing other computatational approaches.

## 1. Comparing Wordlists

One way to use AntConc to compare catalogue data, is to generate wordlists for comparison. In [Episode 5](https://cataloguelegacies.github.io/antconc.github.io/05-wordlists/index.html#saving-your-output) you used the `Word List` tool to generate a wordlist from `IAMS_Photographs_1850-1950_selection3.txt` in .txt format.

Create a comparator corpus by downloading the *BMSatire Descriptions Corpus*, making a wordlist from it, and exporting that wordlist in .txt format (`File`, `Save Output...`). To do this, go to [Episode 10](https://cataloguelegacies.github.io/antconc.github.io/10-BM-wordlists/index.html) and come back here when you are ready.

Now you should have two wordlists. I have called them `IAMS_Photographs_1850-1950_selection3_wordlist.txt` and `BM-MDG_wordlist.txt`, hereafter *[IAMS Photos](https://github.com/CatalogueLegacies/antconc.github.io/blob/gh-pages/data/IAMS_Photographs_1850-1950_selection3_wordlist.txt)* and *[BM Satires](https://github.com/CatalogueLegacies/antconc.github.io/blob/gh-pages/data/BM-MDG_wordlist.txt)* respectively, though you may have given them different names ([don't forget the value](https://cataloguelegacies.github.io/antconc.github.io/05-wordlists/index.html#saving-your-output) of giving logical names to AntConc outputs!).

Now open each wordlist in a text editor (such as [Notepad](https://en.wikipedia.org/wiki/Microsoft_Notepad) for Windows users, or [TextEdit](https://en.wikipedia.org/wiki/TextEdit) for MacOS users) and arrange them side-by-side on your screen. The first thing you will see is that they are different. What we now need to do is observe those differences and start to infer what they might mean.

### Word Types and Tokens

First we might note that *IAMS-Photos* contains more unique words than *BM Satires* (69,476 vs 56,062) despite containing three-fifths of the total words (759,930 vs 1,236,723). This suggests that, lingustically, *BM Satires* has a more constrained corpus than *IAMS-Photos*

### Transcribed and Bracketed

However, *BM Satires* contains two special characters that appear 3rd and 6th in its wordlist: `*transcribed*` and `*bracketed*` are placeholders for text in the description that was either transcribed by the cataloguers (in this case from the objects being described) or placed in brackets as asides or incidental details. This is because, as described in the *[Creation of the BMSatire Descriptions corpus](http://doi.org/10.5281/zenodo.3245037)* document, *BM Satires* was a corpus created to analyse the lingustic choices made during the initial stages of cataloguing, and as consistent patterns for transcriptions and later asides were used, these were removed and replaced with the placeholders `*transcribed*` and `*bracketed*`. Due to the varied nature of *IAMS Photos* no such changes were made to this corpus, meaning that a variety of textual elements - trascribed text, third-party quotations, citations - are included in its wordlist. These differences in the preparation of the corpora likely account for the relative linguistic diversity of the two corpora.

### Spatial language

Nevertheless, as a greater variety of language is likely to be represented by infrequent vocabulary, we can still start to draw conclusions from the two words lists. For example, looking at the 40 most frequent words in *BM Satires*, spatial language is prominent: `behind` (24th), `left` (30th), `right` (31st). These words are not prominent in *IAMS Photos*, instead we observe the prominence of `towards` (18th) and its correlate `looking` (15th). The comparison suggests two very different approaches to descriptions: one, for satires, that moves the reader around the two-dimensional surface of the object and the three-dimensional space of the imagined scene; and another, for photography, that uses the viewpoint of the photographer and viewer alike to take a perspectival approach to the scene at hand. And whilst these lingustic effects are functions of the objects under examination, they remain choices embedded in systems of cataloguing labour and knowledge production.

>## Task 1: Comparing the 25 most frequent words in *IAMS Photos* and *BM Satires*, make a list of the unique vocabulary and shared vocabulary. What questions might we ask next based on these findings?
>* We suggest that you ignore punctuation for this exercise.
>
>>## Solution
>>
>>1. The unique vocabulary for *IAMS Photos* are: view, print, general, looking, photo, towards, duplicate, portrait, group
>>2. The unique vocabulary for *BM Satires* are: `*transcribed*`, `*bracketed*`, his, are, he, an, which, inscribed.
>>3. The shared vocabulary is: the, of, in, a, and, with, on, at, to, from, is, by.
>>4. You may have a number of questions. But the first should be to check the assumptions that stand out. So, for *IAMS Photos*, is it correct that most descriptions are of photographs of people and scenes? (they are) And for *BM Satires*, do the descriptions contain a high frequency of named male individuals? (they do) From there, we might ask more specific questions: do the descriptions in *IAMS Photos* contain details of individuals within groups? given their frequency, what role does transcribed text play in the flow of the descriptions in *BM Satires*?
>>>* All the shared vocabulary are function words, and there is little that is remarkable about their composition. We may, however, note that words like "or" (that might incidate uncertainty of attribution) and "it" (that could be considered an imprecise placeholder for information) are absent in both cases from the 25 most frequent words (indeed, from the 50 most frequent). Keep this in mind as we move to the next part of the episode.
>{: .solution}
{: .challenge}

## 2. Keyness

Keyness is the frequency of a word in a text when compared with its frequency in another corpora, usually a reference corpora such as - for British English language text - the [British National Corpus](http://www.natcorp.ox.ac.uk/), "a 100 million word collection of samples of written and spoken language from a wide range of sources, designed to represent a wide cross-section of British English from the later part of the 20th century, both spoken and written".

In the context of catalogue descriptions, running keyness analysis over a corpora allows us to better understand the language choices that are unusually frequent and unusally infrequent in comparison to reference corpora, thereby furthering our understanding of the 'features' of a given catalogue. And by comparing catalogue data to samples of contemporary language, we improve the chances of foregrounding historic or archaic language choices that may work against the social justice ambitions of our cultural institutions.

### Creating keyness in AntConc

To examine keyness in the *IAMS-Photos* corpus, first ensure that `IAMS_Photographs_1850-1950_selection3_wordlist.txt` is the only file in the `Corpus Files` list.

Next, download [BNC_wordlist.txt](https://github.com/CatalogueLegacies/antconc.github.io/blob/gh-pages/data/BNC_wordlist.txt), a wordlist generated from the *[British National Corpus](http://www.natcorp.ox.ac.uk/)*. With your settings from [Episode 7](https://cataloguelegacies.github.io/antconc.github.io/07-collocates/index.html) still in place (import [IAMS_settings.ant](https://github.com/CatalogueLegacies/antconc.github.io/blob/gh-pages/data/IAMS_settings.ant) if you've had to quit AntConc for some reason), go to `Tool Preferences`, then `Keyword List` and set the preferences as follows:

- make sure `Treat all data as lowercase` is unticked.
- tick `Show negative keywords`.
- change `Keyword effect size measure` to "Ratio of relative frequencies"
- change the `Reference Corpus` toggle to `Use word list(s)`.
- Hit `Add Files`, select [BNC_wordlist.txt](https://github.com/CatalogueLegacies/antconc.github.io/blob/gh-pages/data/BNC_wordlist.txt), and hit `Load`.

Once AntConc has successfully processed the *[British National Corpus](http://www.natcorp.ox.ac.uk/)* wordlist, the `Loaded` checkbox will show as selected. Finally, hit `Apply`, navigate to the `Keyword List` tab, and hit start. After a short delay the output window will populate with results.

### Analysing Keyness

To read the output we need to understand the column headings, the most significant of which is `Keyness`, against which `Rank` is sorted by default. All positive values in the `Keyness` column are a score of how unusally frequent the word is in comparison to the [British National Corpus](http://www.natcorp.ox.ac.uk/), and for the *IAMS-Photos* corpus the highest ranked words deepen our understanding of the corpus: that compared to everyday language the descriptions emphasise perspective ("View", "view", "looking", "towards"), processes of production ("print", "Photo", "Duplicate", "silver", "paper"), and genre ("Full-length", "portrait", "seated").

If we then scroll down to the work ranked 12219, we find the first negative value in the keyness column. This word - "to" - is the most unusually infrequent word in the corpus in comparison to the *[British National Corpus](http://www.natcorp.ox.ac.uk/)*, and what we find is that the top 15 of these are a collection of pronouns ("I", "you", "he", "she", "her"), common verbs in past or active/future tense forms ("was", "be", "had", "have", "will"), and function words ("to", "that", "it", "for", "not"). Note that this adds weight to our analysis in Task 1, where we noted that "it" (5th most unusually infrequent) and "or" (64th most unusually infrequent) were absent from the top 25 more frequent words in *IAMS-Photos*, and that this indicated precision of language and certainty of attribution.

>## Task 2: Make a list of the 10 most unusually frequent verbs in the corpus compared with the British National Corpus.
>* This may require you to make a few assumptions about word use in the corpus (e.g. that "print" is not primarily used as a verb)
>* Don't worry too much about combining results (e.g. the multiple occurence of "view" in the top 20 ranking).
>
>>## Solution
>>
>>1. These are: view (1st, 3rd, 17th, 32nd), look (8th), seat (15th), stand (20th), pose (27th), carve (39th), reproduce (46th), show (47th, 48th), read (56th), fade (64th).
>>2. Making the list emphasises a number of patterns in the cataloguing: that viewpoints are central to the mode of description, the people are commonly found in the descriptions (though we'd need to check if it were animals or objects that are "seating", "standing", or "posing"), and that the descriptions are structured to include transcribed captions (click "reads:" (56th) to see this in the `Concordance` tab).
>{: .solution}
{: .challenge}

>## Task 3: Looking at the 30 most unusually infrequent words, what do they indicate about the *IAMS-Photos* cataloguing? Is this in line with what we've observed in previous episodes?
>
>>## Solution
>>
>>1. First, the unusually infrequent verb forms in the top 30 - "was", "had", "have", "will", "said", "would", "were", "could" - cluster around past and modal verb forms, indicating [as we suggested in Episode 6](https://cataloguelegacies.github.io/antconc.github.io/06-search/index.html#tasks) that the descriptions in *IAMS-Photos* are more 'of' that which the photographs depict than 'about' their histories or histories of those people or places depicted.
>>2. However, the unusual infrequency of third-person pronouns - "he", "she", "her", "they" - might erroneously suggest that the photography are not about people, when in fact the situation is quite the opposite: as [we've observed in Episode 6](https://cataloguelegacies.github.io/antconc.github.io/07-collocates/index.html#from-collocation-to-curatorial-voice) and [will observe in Episode 9](https://cataloguelegacies.github.io/antconc.github.io/09-named-entity-recognition/index.html) these descriptions are full of people, but people given their proper names, rather than refered to using pronouns.
>>>* This is yet another indication of why one test can lead us astray, and why corpus linguistics, as we [observed in Episode 1](https://cataloguelegacies.github.io/antconc.github.io/01-introduction/index.html#what-is-corpus-lingustics), is an iterative study of text, where a phenomenon suggested by one output is tested and refined by the next. 
>{: .solution}
{: .challenge}

### Next Steps

The many potential practical uses of keyness in the context of cataloguing are beyond the scope of this episode, though some are explored in Andrew Salway and James Baker, ‘Investigating Curatorial Voice with Corpus Linguistic Techniques: The Case of Dorothy George and Applications in Museological Practice’, *Museum and Society* 18:2 (2020), doi: [10.29311/mas.v18i2.3175](https://doi.org/10.29311/mas.v18i2.3175).

Keep in mind though that our examples here use AntConc to compare *IAMS-Photos* corpus to the *[British National Corpus](http://www.natcorp.ox.ac.uk/)*. But if you have a catalogue (or sub-collection of cataloguing) whose descriptions you consider to be gold standard, you could justifiably use that as your `Reference Corpus` as a means of better understanding what other catalogues over and under emphasise.

To do so, go to `Tool Preferences`, then `Keyword List`, hit `Clear` to remove `BNC_wordlist.txt` as a reference corpus and upload you own: either as a wordlist generated from AntConc (as we did with the *[British National Corpus](http://www.natcorp.ox.ac.uk/)*) or - by changing the `Reference Corpus` toggle to `Use raw file(s)` by uploading the catalogue itself (note that one of the benefits of using a word list as a reference corpus is that AntConc will run keyness analysis more quickly thatn with a raw corpus!)

## 3. Comparing Concordances

In [Episode 6](https://cataloguelegacies.github.io/antconc.github.io/06-search/index.html#adapting-your-search) we used the `Concordance` tab to search for the string "behind." (with `Regex` unticked and `Words` and `Case` both ticked and `Kwic sort` set to `Level 1` equals `1L`). We said that it was an instructive example because we see a pattern emerge around how this spatial word is used at the end of sentences, specifically the frequency of the construction ",with .. behind." (e.g. "..buildings, with walls on the hillside behind", "..monastery, with mountains behind.", or "..figures, with three attendants standing behind.").

AntConc can also be used to compare concordances. There are two main ways of doing this. The first involves exporting the results from the `Concordance` tab for multiple corpora seperately analysed in AntConc (`File` then `Save Output...`) and reading across them. The second involves importing multiple corpora into AntConc simultanously, and then making a search.

To do this, with `IAMS_Photographs_1850-1950_selection3.txt` already imported into AntConc, import the `BM Satire Corpus` into AntConc (see [Episode 2](https://cataloguelegacies.github.io/antconc.github.io/02-importing-data/index.html#importing-data) for details).

### Using the 'File' column

With both corpora listed under `Corpus Files`, search the `Concordance` tab for the string "behind." (with `Regex` unticked and `Words` and `Case` both ticked and `Kwic sort` set to `Level 1` equals `2L`).

188 results are returned (116 more than with `IAMS_Photographs_1850-1950_selection3.txt` alone). Note that the `File` column of the output window lists the name of the file corresponding to the search result. This gives us the ability it compare the concordance lines for the two corpora.

For example, if we scroll down to the phrases beginning with ", with" (starting at `hit` number 164, ending number 182), we find only one hit from the `BM Satire Corpus` (represented here by `part_aj.txt`). This gives us further evidence that the construction ",with .. behind." is particular to the `IAMS_Photographs_1850-1950_selection3.txt` corpus, rather than a generic term in all cataloguing. We might support our claim by re-sorting our results with `Kwic sort` set to `Level 1` equals `3L`, or introducing comparison with a third corpus.

[Elsewhere in Episode 6](https://cataloguelegacies.github.io/antconc.github.io/06-search/index.html#tasks), we suggested that verb use in the `IAMS_Photographs_1850-1950_selection3.txt` corpus tends towards the present tense. If we re-sort our "behind." search with `Kwic sort` set to `Level 1` equals `1L`, the dominant verb one position left of "behind." is stand. None are in the past tense, but what is striking is how the present tense forms map to the two catalogues:

- "stand behind." (IAMS Photographs = 4, BM Satires = 13)
- "standing behind." (IAMS Photographs = 35, BM Satires = 5)
- "stands behind." (IAMS Photographs = 4, BM Satires = 8)

BM Satires contains roughly double the word tokens of IAMS Photographs, which accounts - more or less - for the relative frequencies of "stand behind." and "stands behind.". This comparison, however, makes the frequency of the present participle form "standing behind." in `IAMS_Photographs_1850-1950_selection3.txt` even more striking. With more investigation, we might determine this to be a lingustic feature of the catalogue.

>## Task 4: Compare how adverbs are used to modify the verb "look" in *IAMS Photos* and *BM Satires*. Does this reinforce our earlier observations about the different approaches to description in the two corpora?
>
>>## Solution
>>
>>1. Search the Concordance tab for the string “look* *ly” (as we did  in [Episode 6](https://cataloguelegacies.github.io/antconc.github.io/06-search/index.html#tasks) with Regex unticked and Words and Case both ticked and Kwic sort set to Level 1 equals 1R).
>>2. There are 131 hits, only 31 instances found in the *IAMS Photos* descriptions.  
>>3. Browse through the output. Note that there is a great variety of modifiers ("amorously", "wryly" etc.) used for the word "look" in the *BM Satires* that desribe the characters in the prints and that are features of "curatorial voice". In comparison two common words (“directly”, “obliquely”) are used in the *IAMS Photos* as descriptions of perspective. As already observed the use of modifiers with the verb "look" illustrates two different approaches to descriptions: one, for satires, that focuses on the subjects taking part in the scene; and another, for photography, that uses the viewpoint of the photographer and viewer alike to take a perspectival approach to the scene at hand. 
>{: .solution}
{: .challenge}
