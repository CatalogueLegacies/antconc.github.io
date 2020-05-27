---
title: "Search"
teaching: 10
exercises: 10
questions:
- "How do search in AntConc?"
- "How can I use search to discover features of catalogue data?"
objectives:
- "Explain how to search"
- "Explain how to read a concordance"
keypoints:
- "You can search a corpus in AntConc using free text and wildcards"
- "Carefully changing the search settings enables you to build better queries"
- "In addition to generating precise data, AntConc can be used get to know a corpus and make rough suggestions as to its character"
---

## Searching in AntConc
After generating lists that characterise a whole corpus, the other main way to interact with a dataset in AntConc is to use search to narrow your enquiry to a subset of a corpus.

The `Concordance` tab is one many that responds to search. Navigate to the `Concordance` tab, put the string "wear" into the search box, and hit `Start`.

After a little thought, AntConc populates the tab. We can observe that - by default - a search in the `Concordance` tab does a number of things:

- It returns a series of lines of text, known as 'condordances' (hence the name of the tab).
- It prompts AntConc to tell us how many times the search term has matched in the corpus.
- It looks for the search term as a word rather than as a string of characters (so our hit count is for *words* not *strings*).
- It uses a case-insensitive search.
- It assumes we care more about the word next *after* the search term rather than *before* it.
- It sorts the results alphabetically by the first character after the search term.
- For each line, it returns information on the file name from which the search term orginates. That is, whilst we’ve separated our file into parts to ease import and processing, you should be able to see there is comparative potential here.

> ## Comparative analysis in AntConc
>
> By working on multiple files, and by providing outputs that identify which result relates to which file, the `Concordance` tab gives us a way into comparative analysis of catalogue data, be that longitudinal (files seperated by the decades in which catalogue entries were made), by collection, or be catalouger. We discuss comparing corpora in more detail in a [later module](https://cataloguelegacies.github.io/antconc.github.io/09-comparing/index.html).
{: .callout}

## Adapting your search
The default search can be changed by use of the options available in the `Condordance` tab.

If you untick `Words`, and rerun your search, you'll notice that AntConc returns more hits and that some of those results are for variants of the word "wear". This does not mean, however, that you've instructed AntConc to look for variants of the word "wear". Rather, you have searched for the four-character string `wear`, meaning that the results could include everything from real English words such as "wear", "wears", and "wearing" to strings that contain the character sequence `wear`, such as "footwear", "12345wear", or "jdeoakewearldsgldslg".

Now we know how the `Words` option works, tick the `Case` option, change the search term to the string "Wear" and hit `Start`. Five results are returned. This is because we have made a case-sensitive search, and the only instances of the string "Wear" in the corpus are for the word 'Wearing' positioned at the start of a sentence (presumably, there are no people called "Wearing" named in the corpus!) 

Finally for now, note the `Kwic Sort` section. `Kwic` means `Keywords in Context` and in AntConc this sort works on `levels`: first `Level 1`, then `Level 2`, then `Level 3`. The values to in the boxes refer to the position relative to the search term on which the sort takes places: so `1R` sorts by the first word to the right of the search term, `1L` by the first word to the left of the search term, `0` by the search term itself, and so on. Note that these `levels` correspond to not only to how the concordance is sorted, but also to the colouring on the words in the concordance.

>## Task 1: get to know the Kwic sort
>* Search the corpus until you find a word with somehow between 50 and 100 hits (you might want to play around with the `Words` and `Case` options to narrow or expand your search). Spending a few minutes changing the `Kwic Sort` to resort your output in various ways. Write down any queries you have about how the sort works and ask your instructor when the time is up.
{: .challenge}

## Wildcard search
Search in AntConc also takes wildcases, both in the form of a limited set of native wildcards, and in the form of regular expressions. We discuss using regular expressions (or regex) in AntConc in a [later module](https://cataloguelegacies.github.io/antconc.github.io/11-regex/index.html). For now, we will focus on the native wildcards, which are similar to those in regex (for those who are familiar). These are:

- `*` is a placeholder for zero or more characters
- `+` for zero or one character
- `?` for any character
- `|` used as an OR operator

Using the string "wear" as an example, wildcards behave as follows (with `Words` and `Case` ticked):

- `wear*` returns "wear", "wears", "wearing", and "wear123" (as well as any five or more letter strings starting wear), but not "footwear".
- `wear+` returns "wear" and "wears" (as well as any five letter strings starting wear), but not "wearing" , "wear123", or "footwear".
- `wear?` returns "wears" (as well as any five letter strings starting wear), but not "wear", "wearing", "wear123", or "footwear".
- `wear?*` returns "wears" (as well as any five or more letter strings starting wear), "wearing", "wear123", and "footwear", but not "wear".
- `wear|wears|wearing` returns only "wear", "wears", and "wearing".

Note that by turning off the `Words` option, AntConc will return results that contain your search string *irrespective* of where in the word it appears. So, for example with `Words` unticked (and `Case` ticked) wildcards behave as follows:

- `wear*` returns "wear", "wears", "wearing", "wear123" and "footwear" (as well as any strings containing "wear" followed by zero or more characters). Note: with `Words` unticked, this is the same as `wear`.
- `wear+` returns "wear", "wears", "footwear", "wearing" , and "wear123" (as well as any strings containing "wear" followed by zero or one character). Note: with `Words` unticked, this is the same as `wear`.
- `wear?` returns "wears", "wearing", and "wear123" (as well as any strings containing "wear" followed by one character), but not "wear" or "footwear".
- `wear?*` returns "wears", "wearing", and "wear123" (as well as any strings containing "wear" followed by one character), but not "wear" or "footwear". Note: with `Words` unticked, this is the same as `wear?`.
- `wear|wears|wearing` returns any strings containing "wear", "wears", or "wearing". Note: with `Words` unticked, this is the same as `wear`.

## Tasks

Having learnt using AntConc's `Concordance` tab to search a corpus, work in pairs or small groups on the following challenges.

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

>## Task 3: Compare the use of past and present tense forms of the verb "say". Decide which is more common, by roughly what factor, and if there anything that characterises the past tense form.
>* Note: there are three present tense forms of the word "say". This problem can also be solved with one query.
>
>>## Solution
>>
>>1. Search for `said|say|says|saying` (with `Words` ticked and `Case` unticked), with the `Kwic sort` set to `Level 1` equals `0` and the other levels unticked. 
>>2. The word "says" is the most common. We can infer this by scrolling through the sorted results, as "says" starts roughly half way down the list and continues to the end.
>>3. `8300` hits are returned, only around 70 of which are for the word "said", meaning that present tense forms are over one-hundred times more common.
>>4. In terms of what characterises the use of "said" in the corpus, browsing the concordance suggests two main uses: first, instances where the curator/cataloguer is speaking or interpretating ("he is said to be", "the print is said to be"), and second errors replacing transcribed speech with the placeholder `*TRANSCRIBED*`.
>>>* This is a good example of using the browsing features within AntConc to infer results. The exact answers could computed from outputs saved to file, but in many cases reading a sorted list does the same job.
>{: .solution}
{: .challenge}

>## Task 4: Examine the use of adverbs for the verb "stand".
>* Note: you can search for two-word strings and wildcards can be used more than once.
>
>>## Solution
>>
>>1. Search for `stand*` `Words` ticked and `Case` unticked. You should get `7858` hits.
>>2. Next, search for `stand* *ly` (again with `Words` ticked and `Case` unticked), with the `Kwic sort` set to `Level 1` equals `1R` and the other levels unticked. You should get `277` hits, suggesting that modifiers are used infrequently for the word "stand".
>>3. Browse through the output. Note that of the "-ly" words present, there is a small number of unique words, and that those that are more commons indicate readily identifiable states of being ("agressively" and "stiffly" are more common than "truculently" and "deprecatingly"). This potentially indicates that the cataloguer exercised relative control of their vocabulary (that is, there are few modifiers and of those a small number dominate), but this hypothesis would need to be tested against the wider corpus.
>{: .solution}
{: .challenge}
