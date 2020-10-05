---
title: "Searching concordances"
teaching: 15
exercises: 15
questions:
- "How can I search in AntConc?"
- "How can I use search to discover features of catalogue data?"
objectives:
- "Explain how to search a concordance"
- "Explain how to read a concordance"
keypoints:
- "You can search a corpus in AntConc using free text and wildcards"
- "Carefully changing the search settings enables you to build better queries"
- "In addition to generating precise data, AntConc can be used get to know a corpus and make rough suggestions as to its character"
---

## Searching in AntConc
After generating lists that characterise a whole corpus, the other main way to interact with a dataset in AntConc is to use search to narrow your enquiry to a subset of a corpus.

The `Concordance` tab is one of many tabs that responds to search. Navigate to the `Concordance` tab, put the string "wear" into the search box, and hit `Start`.

After a little thought, AntConc populates the tab. We can observe that - by default - a search in the `Concordance` tab does a number of things:

- It returns a series of lines of text, known as 'condordances lines' (hence the name of the tab).
- It prompts AntConc to tell us how many times the search term has matched in the corpus (39 in this case)
- It looks for the search term as a word rather than as a string of characters (so our hit count is for *words* not *strings*).
- It uses a case-insensitive search.
- It assumes we care more about the word next *after* the search term rather than *before* it (though this can be changed, as we shall see shortly!)
- It sorts the results alphabetically by the first character after the search term.
- For each line, it returns information on the file name from which the search term orginates. That is, whilst we’ve separated our file into parts to ease import and processing, you should be able to see there is comparative potential here.

> ## Comparative analysis in AntConc
>
> By working on multiple files, and by providing outputs that identify which result relates to which file, the `Concordance` tab gives us a way into comparative analysis of catalogue data, be that longitudinal (files seperated by the decades in which catalogue entries were made), by collection, or be cataloguer. We discuss comparing corpora in more detail in a [later episode](https://cataloguelegacies.github.io/antconc.github.io/09-comparing/index.html).
{: .callout}

## Adapting your search
The default search can be changed by use of the options available in the `Condordance` tab.

If you untick `Words`, and rerun your search, you'll notice that AntConc returns many more hits (272 compared with 39 before) and that some of those results are for variants of the word "wear". This does not mean, however, that you've instructed AntConc to look for variants of the word "wear". Rather, you have searched for the four-character string `wear`, meaning that the results could include everything from real English words such as "wear", "wears", and "wearing" to strings that contain the character sequence `wear`, such as "footwear", "12345wear", or "jdeoakewearldsgldslg".

Now we know how the `Words` option works, tick the `Case` option, change the search term to the string "Wear" and hit `Start`. 271 results are returned (one fewer than before). This is because we have made a case-sensitive search, and the only instance of the string "Wear" in the corpus is for the word 'Wears' positioned at the start of a quotation (there are no people with the family name "Wearing" in this corpus!) 

Finally for now, note the `Kwic Sort` section. `Kwic` means `Keywords in Context` and in AntConc this sort works on `levels`: first `Level 1`, then `Level 2`, then `Level 3`. The values to in the boxes refer to the position relative to the search term on which the sort takes places: so `1R` sorts by the first word to the right of the search term, `1L` by the first word to the left of the search term, `0` by the search term itself, and so on. Note that these `levels` correspond not only to how the concordance is sorted, but also to the colouring on the words in the concordance.

>## Task 1: get to know the Kwic sort
>* Search the corpus until you find a word with somewhere between 50 and 100 hits (you might want to play around with the `Words` and `Case` options to narrow or expand your search - if you get stuck, try "richly"). Spending a few minutes changing the `Kwic Sort` to resort your output in various ways. Write down any queries you have about how the sort works and ask your instructor when the time is up.
{: .challenge}

## Wildcard search
Search in AntConc also takes wildcases, both in the form of a limited set of native wildcards, and in the form of regular expressions. We discuss using regular expressions (or regex) in AntConc in a [later episode](https://cataloguelegacies.github.io/antconc.github.io/11-regex/index.html). For now, we will focus on the native wildcards, which are similar to those in regex (for those who are familiar). These are:

- `*` is a placeholder for zero or more characters
- `+` for zero or one character
- `?` for any character
- `|` used as an OR operator

Using the string "wear" as an example, wildcards behave as follows (with `Words` and `Case` ticked):

- `wear*` could return "wear", "wears", "wearing", and "wear123" (as well as any five or more letter strings starting wear), but not "footwear".
- `wear+` could return "wear" and "wears" (as well as any five letter strings starting wear), but not "wearing" , "wear123", or "footwear".
- `wear?` could return "wears" (as well as any five letter strings starting wear), but not "wear", "wearing", "wear123", or "footwear".
- `wear?*` could return "wears" (as well as any five or more letter strings starting wear), "wearing", "wear123", and "footwear", but not "wear".
- `wear|wears|wearing` could return only "wear", "wears", and "wearing".
	- Note: not all examples above are of words in the corpus.

Note that by turning off the `Words` option, AntConc will return results that contain your search string *irrespective* of where in the word it appears. So, for example with `Words` unticked (and `Case` ticked) wildcards behave as follows:

- `wear*` could return "wear", "wears", "wearing", "wear123" and "footwear" (as well as any strings containing "wear" followed by zero or more characters). Note: with `Words` unticked, this is the same as `wear`.
- `wear+` could return "wear", "wears", "footwear", "wearing" , and "wear123" (as well as any strings containing "wear" followed by zero or one character). Note: with `Words` unticked, this is the same as `wear`.
- `wear?` could return "wears", "wearing", and "wear123" (as well as any strings containing "wear" followed by one character), but not "wear" or "footwear".
- `wear?*` could return "wears", "wearing", and "wear123" (as well as any strings containing "wear" followed by one character), but not "wear" or "footwear". Note: with `Words` unticked, this is the same as `wear?`.
- `wear|wears|wearing` returns any strings containing "wear", "wears", or "wearing". Note: with `Words` unticked, this is the same as searching `wear`.
	- Note: not all examples above are of words in the corpus.

## Tasks

Having learnt using AntConc's `Concordance` tab to search a corpus, work in pairs or small groups on the following challenges.

>## Task 2: Work out rough % of the word "he" used at the start of a sentence.
>* Note: to solve this problem, you may find it helpful to do more than one search.
>
>>## Solution
>>
>>1. Search "he" and "He" separately with `Words` and `Case` both ticked. You should get `372` hits for "he" and `213` hits for "He".
>>2. The answer is just over half.
>>>* If you scroll through the results, you'll see that this is an exact solution *for this corpus*. However, this is not a perfect query, as other corpora may contain typographic errors or uncommon uses of the word "he". This is an example when knowing your corpus can help you craft a good enough query, rather than have to expend time and energy creating the perfect query. Handily, the ouputs provided by this AntConc tool are a great way of getting to know a corpus.
>{: .solution}
{: .challenge}

>## Task 3: Compare the use of past and present tense forms of the verb "say". Decide which is more common, by roughly what factor, and if there anything that characterises the past tense form.
>* Note: there are three present tense forms of the word "say". This problem can also be solved with one query.
>
>>## Solution
>>
>>1. Search for `said|say|says|saying` (with `Words` ticked and `Case` unticked), with the `Kwic sort` set to `Level 1` equals `0` and the other levels unticked. 
>>2. The word "said" is the most common. We can infer this by scrolling through the sorted results, as "say" starts towards the end of the list.
>>3. `1539` hits are returned, only around 70 of which are for the word "said", meaning that present tense forms are over twenty times more common.
>>4. In terms of what characterises the use of "said" in the corpus, browsing the concordance suggests two main uses: first, instances where the curator/cataloguer is speaking or interpretating ("which is said to be", "the house said to have been"), and second, in third-party text brought into the description (line 45: "..'Oh,' said the Nono, 'I will send..").
>>>* This is a good example of using the browsing features within AntConc to infer results. The exact answers could be computed from outputs saved to file, but in many cases reading a sorted list does the same job.
>>>* Note how browsing rather than just counting helps us spot errors: here the names "Said" and "Say". 
>{: .solution}
{: .challenge}

>## Task 4: Examine how adverbs are used to modify the verbs "look".
>* Note: you can search for two-word strings and wildcards can be used more than once.
>
>>## Solution
>>
>>1. Search for `look*` `Words` ticked and `Case` unticked. You should get `5989` hits.
>>2. Next, search for `look* *ly` (again with `Words` ticked and `Case` unticked), with the `Kwic sort` set to `Level 1` equals `1R` and the other levels unticked. You should get `41` hits, suggesting that modifiers are used very infrequently for the word "look".
>>3. Browse through the output. Note that of the "-ly" words present, there are two common words ("directly", "obliquely") both of which can be clearly understood as descriptions of perspective. This indicates that the cataloguer(s) exercised relative control of their vocabulary (that is, there are few modifiers and of those a small number dominate), but this hypothesis would need to be tested against the wider corpus. One piece of supporting evidence is the small number of infrequent modifiers, most of which are found within third-party text (that is, text not written by the cataloguer or cataloguers). 
>{: .solution}
{: .challenge}
