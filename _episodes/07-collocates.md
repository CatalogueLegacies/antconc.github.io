---
title: "Collocates (fixme)"
teaching: 5
exercises: 5
questions:
- "What are collocates?"
- "How do collocates work in AntConc?"
- "What conclusions can be reached based on collocation data?"
objectives:
- "Learn how collocates work in AntConc"
keypoints:
- "The collocates of a word are those words that tend to occur in proximity to that word more than they occur in proximity to all other words in the corpus general"
---

## Introducing Transformations

Through facets, filters and clusters OpenRefine offers relatively straightforward ways of getting an overview of your data, and making changes where you want to standardise terms used to a common set of values.

However, sometimes there will be changes you want to make to the data that cannot be achieved in this way. Such types of changes include:

* Splitting data that is in a single column into multiple columns (e.g. splitting an address into multiple parts)
* Standardising the format of data in a column without changing the values (e.g. removing punctuation or standardising a date format)
* Extracting a particular type of data from a longer text string (e.g. finding ISBNs in a bibliographic citation)

To support this type of activity OpenRefine supports 'Transformations' which are ways of manipulating data in columns. Transformations are normally written in a special language called 'GREL' (General Refine Expression Language). To some extent GREL expressions are similar to Excel Formula, although they tend to focus on text manipulations rather than numeric functions.

Full documentation for the GREL is available at [https://github.com/OpenRefine/OpenRefine/wiki/General-Refine-Expression-Language](https://github.com/OpenRefine/OpenRefine/wiki/General-Refine-Expression-Language). This tutorial covers only a small subset of the commands available.

### Common transformations
Some transformations are used regularly and are accessible directly through menu options, without having to type them directly.

Examples of some of these common transformations are given in the table below, with their 'GREL' equivalents. We'll see how to use the GREL version later in this lesson.

Common Transformation  | Action | GREL expression
--------------------| ------------- | -------------
To Uppercase| Converts the current value to uppercase | ```value.toUppercase()```
To Lowercase| Converts the current value to lowercase | ```value.toLowercase()```
To Titlecase| Converts the current value to titlecase (i.e. each word starts with an uppercase character and all other characters are converted to lowercase) | ```value.toTitlecase()```
Trim leading and trailing whitespace | Removes any 'whitespace' characters (e.g. spaces, tabs) from the start or end of the current value | ```value.trim()```

> ## Comparative analysis in AntConc
>
> By working on multiple files, and by providing outputs that identify which result relates to which file, the `Concordance` tab gives us a way into comparative analysis of catalogue data, be that longitudinal (files seperated by the decades in which catalogue entries were made), by collection, or be catalouger. We discuss comparing corpora in more detail in a [later episode](https://cataloguelegacies.github.io/antconc.github.io/09-comparing/index.html).
{: .callout}

>## Task 1: get to know the Kwic sort
>* Search the corpus until you find a word with somehow between 50 and 100 hits (you might want to play around with the `Words` and `Case` options to narrow or expand your search). Spending a few minutes changing the `Kwic Sort` to resort your output in various ways. Write down any queries you have about how the sort works and ask your instructor when the time is up.
{: .challenge}

>## Task 2: Work out rough % of the word "he" used at the start of a sentence.
>* Note: to solve this problem, you may find it helpful to do more than one search.
>
>>## Solution
>>
>>1. Search "he" and "He" separately with `Words` and `Case` both ticked. You should get `4716` hits for "he" and `4456` hits for "He".
>>2. The answer is just under half.
>>>* If you scroll through the results, you'll see that this is an exact solution *for this corpus*. However, this is not a perfect query, as other corpora may contain typographic errors or uncommon uses of the word "he". This is an example when knowing your corpus can help you craft a good enough query, rather than have to expend time and energy creating the perfect query. Handily, the ouputs provided by AntConc are a great way of getting to know a corpus.
>{: .solution}
{: .challenge}
