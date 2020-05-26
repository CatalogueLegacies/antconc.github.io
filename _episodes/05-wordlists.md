---
title: "Wordlists"
teaching: 10
exercises: 10
questions:
- "What are wordlists in AntConc and when would you use it?"
- "How do wordlists work in AntConc?"
- "How might I interpret wordlists generated from catalogue data?"
objectives:
- "Explain what wordlists are in OpenRefine"
- "Use wordlists to start identifying the lingustic character of a corpus"
keypoints:
- "Wordlists are a way of getting an overview of the lingustic features of a corpus"
- "AntConc provides a number of options for presenting wordlists"
- "When using AntConc to count things, we need to be mindful that machine readable strings and are not the same as human readable words"
- "Outputs from AntConc queries can be saved locally as text files"
---

## Clustering
The Cluster function groups together similar, but inconsistent values in a given column and lets you merge these inconsistent values into a single value you choose.

This is very effective where you have data with minor variations in data values, e.g. names of people, organisations, places, classification terms.

To use the 'Cluster' function, click on the `Edit Cells` menu option in the relevant column and choose `Cluster and edit...`

The 'Clusters' are created automatically according to an algorithm. OpenRefine supports a number of different clustering algorithms - some experimentation may be required to see which clustering algorithm works best with any particular set of data, and you may find that using different algorithms highlights different clusters.

For more information on the methods used to create Clusters, see [https://github.com/OpenRefine/OpenRefine/wiki/Clustering-In-Depth](https://github.com/OpenRefine/OpenRefine/wiki/Clustering-In-Depth)

For each cluster, you have the option of 'merging' the values together - that is, replace the various inconsistent values with a single consistent value. By default, OpenRefine uses the most common value in the cluster as the new value, but you can select another value by clicking the value itself, or you can simply type the desired value into the 'New Cell Value' box.

>## Use Clustering to clean up author data
>
>1. Split out the author names into individual cells using `Edit cells -> Split multi-valued cells`, using the pipe ( \| ) character as the separator
>2. Choose `Edit cells -> Cluster and edit` from the 'author' column.
>3. Using the `key collision` method with the `fingerprint` Keying Function, work through the clusters of values, merging them to a single value where appropriate
>4. Try changing the clustering method being used - which ones work well?
{: .challenge}
