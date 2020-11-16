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

## Comparing Wordlists

One way to use AntConc to compare catalogue data, is to generate wordlists for comparison. In [Episode 5](https://cataloguelegacies.github.io/antconc.github.io/05-wordlists/index.html#saving-your-output) you used the `Word List` tool to generate an wordlist from `IAMS_Photographs_1850-1950_selection3.txt` in .txt format.

Create a comparator corpus by downloading the *BMSatire Descriptions Corpus*, a wordlist from it, and downloading that wordlist in .txt format. Go to [Episode 10](https://cataloguelegacies.github.io/antconc.github.io/10-BM-wordlists/index.html) and come back here when you are ready.

Now you should have two wordlists. I have called them `IAMS_Photographs_1850-1950_selection3_wordlist.txt` and `BM-MDG_wordlist.txt`, hereafter *IAMS Photos* and *BM Satires* respectively, though you may have given them different names ([don't forget the value](https://cataloguelegacies.github.io/antconc.github.io/05-wordlists/index.html#saving-your-output) of giving logical names to AntConc outputs!). Open them up in a text editor and arrange them side-by-side. The first thing you will see is that they are different. What we now need to do is observe those differences and start to infer what they might mean.

- **Word Types and Tokens**. *IAMS-Photos* contains more unique words than *BM Satires* (69,476 vs 56,062) despite containing three-fifths of the total words (759,930 vs 1,236,723). This suggests that, lingustically, *BM Satires* has a more constrained corpus than *IAMS-Photos*
- **Transcribed and Bracketed**. However, *BM Satires* contains two special characters that appear 3rd and 6th in its wordlist: `*transcribed*` and `*bracketed*` are placeholders for text in the description that was either transcribed by the cataloguers (in this case from the objects being described) or placed in brackets as asides or incidental details. This is because, as described in the *[Creation of the BMSatire Descriptions corpus](http://doi.org/10.5281/zenodo.3245037)* document, *BM Satires* was a corpus created to analyse the lingustic choices made during the initial stages of cataloguing, and as consistent patterns for transcriptions and later asides were used, these were removed and replaced with the placeholders `*transcribed*` and `*bracketed*`. Due to the varied nature of *IAMS Photos* no such changes were made to this corpus, meaning that a variety of textual elements - trascribed text, third-party quotations, citations - are included in its wordlist. These differences in the preparation of the corpora likely account for the relative linguistic diversity of the two corpora.
- **Spatial language**. Nevertheless, as a greater variety of language is likely to be represented by infrequent vocabulary, we can still start to draw conclusions from the two words lists. For example, looking at the 40 most frequent words in *BM Satires*, spatial language is prominent: `behind` (27th), `left` (30th), `right` (31st). These words are not prominent in *IAMS Photos*, instead the we observe the prominence of `towards` (18th) and its correlate looking `15th`. The comparison suggests two very different approaches to descriptions: one, for satires, that moves the reader around the two-dimensional surface of the object and the three-dimensional space of the imagined scene, another; and another, for photography, that uses the viewpoint of the photographer and viewer alike to take a perspectival approach to the scene at hand. And whilst these lingustic effects are functions of the objects under examination, they remain choices embedded in systems of cataloguing labour and knowledge production.
