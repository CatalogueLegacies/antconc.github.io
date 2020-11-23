---
title: "Next Steps 1: comparing corpora (**not yet developed**)"
teaching: 5
exercises: 0
questions:
- "How do can I use AntConc to compare multiple sets of catalogue data?"
- "How can I compare curatorial 'voice' to general language?"
- "What are the benefits of comparison?"
objectives:
- "FIXME"
keypoints:
- "FIXME"
---

## Why Compare

This episode introduces potential next steps for comparing corpora. Each of the three sections are only intended as jumping off points, rather than comprehensive accounts of their methods. This is because the method of comparison will be shaped your initial lingustic analysis: as we wrote in [Episode 1](https://cataloguelegacies.github.io/antconc.github.io/01-introduction/index.html), corpus lingustics is therefore an iterative study of text, where a phenomenon suggested by one output is tested and refined by the next.

In the context of catalogue data, there are a number of reasons to compare corpora: because comparison provides an alternative point of analysis for defining the features of a given catalogue data under analysis; because a given catalogue can be broken into subsets that are then analysed comparatively (e.g. taking a exemplar or baseline collection of catalogue data to better understand the linguistic features of given subset in need of attention); because comparisons of catalogue data with other types of texts - e.g. everyday speech - can helpfully tease out the "special language" that might form the basis of, say, a guide to cataloguing at your institution.

Used creatively, AntConc can provide the basic toolset required to undertake a variety of comparative analyses, though the deeper your comparing goes, the more you may find yourself needing other computatational approaches.

## 1. Comparing Wordlists

One way to use AntConc to compare catalogue data, is to generate wordlists for comparison. In [Episode 5](https://cataloguelegacies.github.io/antconc.github.io/05-wordlists/index.html#saving-your-output) you used the `Word List` tool to generate an wordlist from `IAMS_Photographs_1850-1950_selection3.txt` in .txt format.

Create a comparator corpus by downloading the *BMSatire Descriptions Corpus*, a wordlist from it, and downloading that wordlist in .txt format. Go to [Episode 10](https://cataloguelegacies.github.io/antconc.github.io/10-BM-wordlists/index.html) and come back here when you are ready.

Now you should have two wordlists. I have called them `IAMS_Photographs_1850-1950_selection3_wordlist.txt` and `BM-MDG_wordlist.txt`, hereafter *[IAMS Photos](https://github.com/CatalogueLegacies/antconc.github.io/blob/gh-pages/data/IAMS_Photographs_1850-1950_selection3_wordlist.txt)* and *[BM Satires](https://github.com/CatalogueLegacies/antconc.github.io/blob/gh-pages/data/BM-MDG_wordlist.txt)* respectively, though you may have given them different names ([don't forget the value](https://cataloguelegacies.github.io/antconc.github.io/05-wordlists/index.html#saving-your-output) of giving logical names to AntConc outputs!). Open them up in a text editor and arrange them side-by-side. The first thing you will see is that they are different. What we now need to do is observe those differences and start to infer what they might mean.

- **Word Types and Tokens**. *IAMS-Photos* contains more unique words than *BM Satires* (69,476 vs 56,062) despite containing three-fifths of the total words (759,930 vs 1,236,723). This suggests that, lingustically, *BM Satires* has a more constrained corpus than *IAMS-Photos*
- **Transcribed and Bracketed**. However, *BM Satires* contains two special characters that appear 3rd and 6th in its wordlist: `*transcribed*` and `*bracketed*` are placeholders for text in the description that was either transcribed by the cataloguers (in this case from the objects being described) or placed in brackets as asides or incidental details. This is because, as described in the *[Creation of the BMSatire Descriptions corpus](http://doi.org/10.5281/zenodo.3245037)* document, *BM Satires* was a corpus created to analyse the lingustic choices made during the initial stages of cataloguing, and as consistent patterns for transcriptions and later asides were used, these were removed and replaced with the placeholders `*transcribed*` and `*bracketed*`. Due to the varied nature of *IAMS Photos* no such changes were made to this corpus, meaning that a variety of textual elements - trascribed text, third-party quotations, citations - are included in its wordlist. These differences in the preparation of the corpora likely account for the relative linguistic diversity of the two corpora.
- **Spatial language**. Nevertheless, as a greater variety of language is likely to be represented by infrequent vocabulary, we can still start to draw conclusions from the two words lists. For example, looking at the 40 most frequent words in *BM Satires*, spatial language is prominent: `behind` (27th), `left` (30th), `right` (31st). These words are not prominent in *IAMS Photos*, instead the we observe the prominence of `towards` (18th) and its correlate looking `15th`. The comparison suggests two very different approaches to descriptions: one, for satires, that moves the reader around the two-dimensional surface of the object and the three-dimensional space of the imagined scene, another; and another, for photography, that uses the viewpoint of the photographer and viewer alike to take a perspectival approach to the scene at hand. And whilst these lingustic effects are functions of the objects under examination, they remain choices embedded in systems of cataloguing labour and knowledge production.

>## Task 1: Comparing the 25 most frequent words in *IAMS Photos* and *BM Satires*, make a list of the unique vocabulary and shared vocabulary. What questions might we ask next based on these findings.
>* We suggest that you ignore punctuation for this exercise.
>
>>## Solution
>>
>>1. The unique vocabulary for *IAMS Photos* are: view, print, general, looking, photo, towards, duplicate, portrait, group
>>2. The unique vocabulary for *BM Satires* are: `*transcribed*`, `*bracketed*`, his, are, he, an, which, inscribed.
>>3. The shared vocabulary is: the, of, in, a, and, with, on, at, to, from, is, by.
>>4. You may have a number of questions. But the first should be to check the assumptions that stand out. So, for *IAMS Photos*, is it correct that most descriptions are of photographs of people and scenes? (they are) And for *BM Satires*, do the descriptions contain a high frequency of named male individuals? (they do) From there, we might ask more specific questions: do the descriptions in *IAMS Photos* contain details of individuals within groups? given their frequency, what role does transcribed text play in the flow of the descriptions in *BM Satires*
>>>* All the shares vocabulary are function words, and there is little that is remarkable about their composition. We may, however, note that words like "or" (that might incidate uncertainty of attribution) and "it" (that could be considered an imprecise placeholder for information) are absent in both cases from the 25 most frequent words (indeed, from the 50 most frequent). Keep this in mind as we move to the next part of the episode.
>{: .solution}
{: .challenge}

## 2. Keyness

FIXME

## 3. Comparing Concordances

In [Episode 6](https://cataloguelegacies.github.io/antconc.github.io/06-search/index.html#adapting-your-search) we used the `Concordance` tab to search for the string "behind." (with `Regex` unticked and `Words` and `Case` both ticked and `Kwic sort`). We said that it was an instructive example because we see a pattern emerge around how this spatial word is used at the end of sentences, specifically the frequency of the construction ",with .. behind." (e.g. "..buildings, with walls on the hillside behind", "..monastery, with mountains behind.", or "..figures, with three attendants standing behind.").

AntConc can also be used to compare concordances. There are two main ways of doing this. The first involves exporting the results from the `Concordance` tab for multiple corpora seperately analysed in AntConc (`File` then `Save Output...`) and reading across them. The second involves importing multiple corpora into AntConc simultanously, and then making a search.

To do this, with `IAMS_Photographs_1850-1950_selection3.txt` already imported into AntConc, import the `BM Satire Corpus` into AntConc (see [Episode 2](https://cataloguelegacies.github.io/antconc.github.io/02-importing-data/index.html#importing-data) for details).

With both corpora listed under `Corpus Files`, search the `Concordance` tab for the string "behind." (with `Regex` unticked and `Words` and `Case` both ticked and `Kwic sort` set to `Level 1` equals `2L`).

188 results are returned (116 more than with `IAMS_Photographs_1850-1950_selection3.txt` alone). Note that the `File` column of the output window lists the name of the file corresponding to the search result. This gives us the ability it compare the concordance lines for the two corpora.

For example, if we scroll down to the phrases beginning with ", with" (starting at `hit` number 164, ending number 182), we find only one hit from the `BM Satire Corpus` (represented here by `part_aj.txt`). This gives us further evidence that the construction ",with .. behind." is particular to the `IAMS_Photographs_1850-1950_selection3.txt` corpus, rather than a generic term in all cataloguing. We might support our claim by re-sorting our results with `Kwic sort` set to `Level 1` equals `3L`, or introducing comparison with a third corpus.

[Elsewhere in Episode 6](https://cataloguelegacies.github.io/antconc.github.io/06-search/index.html#tasks), we suggested that verb use in the `IAMS_Photographs_1850-1950_selection3.txt` corpus tends towards the present tense. If we re-sort our "behind." search with `Kwic sort` set to `Level 1` equals `1L`, the dominant verb one position left of "behind." is stand. None are in the past tense, but what is striking is how the present tense forms map to the two catalogues:

- "stand behind." (IAMS Photographs = 4, BM Satires = 13)
- "standing behind." (IAMS Photographs = 35, BM Satires = 5)
- "stands behind." (IAMS Photographs = 4, BM Satires = 8)

BM Satires contains roughly double the word tokens of IAMS Photographs, which accounts - more or less - the relative frequencies of "stand behind." and "stands behind.". This comparison, however, makes the frequency of the present participle form "standing behind." in `IAMS_Photographs_1850-1950_selection3.txt` even more striking. With more investigation, we might determinet his to be a lingustic feature of the catalogue.
