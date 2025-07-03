

<!-- Set up code of OTTR Book-->



# Phyloseq - Part 1

## Exploring 16S rRNA Data with phyloseq

<!-- Intro text -->


## Lecture - Exploring 16S rRNA Data with phyloseq

*Estimated time: *

<img src="resources/images/explore-phyloseq_files/figure-html//1gJ_4YoqDJD5-40MArbpgTr_5652JpHI7cgnHHo4Vsws_g35f391192_00.png" alt="Image test" width="100%" style="display: block; margin: auto;" />

[Lecture](https://docs.google.com/presentation/d/1gJ_4YoqDJD5-40MArbpgTr_5652JpHI7cgnHHo4Vsws/edit?usp=sharing)


## Activity - Exploring 16S rRNA Data with phyloseq

To explore bacterial diversity based on 16S rRNA gene sequencing using data from the “Impact of a 7-day homogeneous diet on interpersonal variation in human gut microbiomes and metabolomes” by Guthrie et al., 2023. This study is also referred to as the MISO study for “Microbiome Individuality and Stability Over Time” because the study aims to understand variation (or stability) of microbiomes across individuals.

This activity aims to explore and profile the metagenomic diversity using the R/Bioconductor package phyloseq which leverages various R-based tools to produce publication-quality taxonomy profiling and analysis  graphics.

### Learning objectives

1. Use phyloseq to explore data associated with Amplicon Sequence Variants (ASVs).
1. In phyloseq, subset data based on metadata and taxonomy.
1. In phyloseq, profile and plot taxonomy.

### Introduction
The most popular sequencing technique for the analysis of bacterial diversity is targeted sequencing, or sequencing of a specific gene (or region of a gene, e.g. a hypervariable region of the bacterial 16S ribosomal rRNA gene) using polymerase chain reaction (PCR) to create sequences called amplicons. Sequence variation in the resulting amplicons creates amplicon sequence variants (ASVs). ASVs varying from as little as one single nucleotide can be defined as separate ASVs, which can be further clustered into OTUs (Operational Taxonomic Units) based on sequence similarity; e.g. as ASVs within 1% sequence difference can clustered into the same species/OTU. 

### Activity 1 – Explore 16S rRNA Data with phyloseq tutorial

*Estimated time: 25 min*

Explore a phyloseq object through the “Explore 16S rRNA Data with phyloseq” tutorial on SciServer.
Log into SciServer, click on compute, and create a new C-MOOR LearnR container. When creating a container, remember to:
1. Use the “C-MOOR LearnR (Bioconductor 3.17)” image (not the Bioconductor 3.16)
2. Check the box next to Data volume “C-MOOR Data”
3. Start the “Explore 16S rRNA Data with phyloseq” tutorial. Visit SciServer Guides and FAQs. If you need assistance accessing the tutorial.
4. To move through the activities click “Continue” at the bottom of the screen. When you are done with a topic, click “Next Topic” to move on.
5. This tutorial has small boxes in which you can enter and run short lines of code to analyze the data.
As you work through the tutorial, take snapshots of your work and paste your answers in the grey boxes below:


|1-1. OTU_table Exercise – Take a snapshot and paste your code and the output for the following question in the tutorial: “What is the normalized count for ASV115 in sample 10?”|
|:--|
| <br> |
<br>

|1-2. Visualizing Taxonomy Exercise – Take a snapshot and paste your code and the output for the following question in the tutorial: “What timepoint has the lowest proportion of phylum Verrucomicrobia?”|
|:--|
| <br> |
<br>

|1-3. Using subset_taxa() Exercise – Take a snapshot and paste your code and the output for the following question in the tutorial: “What are the 2 most abundant orders in the class Gammaproteobacteria?”|
|:--|
| <br> |
<br>

### Activity 2 – Try it out!

*Estimated time: 60 min*

With your group, perform some exploratory data analysis selecting from one of the four questions below or coming up with your own question.  When you are done, copy and paste your results into the class poster.   
[Class Poster](https://docs.google.com/presentation/d/1eE5AltbkW6km0r3uQO8KKnUVRLCLx70SDNuBHp6aASU/edit?slide=id.g343cb6dd56c_2_0#slide=id.g343cb6dd56c_2_0)

#### Question 1 - What has more impact on human microbial variation, diet or individuality?

Approach: Plot high level taxa (Phyla) for all timepoints and subjects and compare the plots to determine which factor has a stronger effect on microbiome composition.


**Step  1A: Plot high-level taxonomy (Phylum level) for each  timepoint using the plot_bar() function.** Specifically, your plot should show Phyla diversity across all 5 timepoints. 
- Refer to the “Explore 16S rRNA Data with phyloseq” tutorial for help using the plot_bar() function.
- Ensure your plot has a title
- Remember, the BD diet includes timepoints 1 and 2, the HD diet includes timepoints 3 and 4, and the WO diet includes timepoint 5.
- Use the following code as a template:


``` r
plot_bar(miso, "fill in the blank", fill = "fill in the blank", title = "choose a name for your graph") +
  geom_bar(aes(color = fill in the blank, fill = fill in the blank), stat = "identity", position = "stack")
```

|1A-1. Paste figure 1A below.|
|:--|
| <br> |
<br>

**1A-2. State your conclusion for  Figure 1A below.**
- Include a list of the identified Phyla and their names
- Include if you think  there is a difference between conditions and  your reasoning why or why not
||
|:--|
| <br> |
<br>

Step 1B: Plot high-level taxonomy (Phylum level) for each individual, using only normalized homogenized diet “HD” timepoints to minimize contribution of diet to the analysis using the plot_bar() function. Specifically, your plot should show Phyla diversity across all 21 individuals at HD timepoints. 

- Use the command below to create a phyloseq object with only “HD” timepoints


``` r
misoHD = subset_samples(miso, timepointgroup == "HD")
```

- Refer to the “Explore 16S rRNA Data with phyloseq” tutorial for help using the plot_bar() function.
- Ensure your plot has a title


|1B-1. Paste figure 1B below.|
|:--|
| <br> |
<br>

**1B-2. State your conclusion for  Figure 1B below.**
- Include a list of the identified Phyla and their names
- Include if you think  there is a difference between conditions and  your reasoning why or why not
||
|:--|
| <br> |
<br>

A suggestion for your poster: 
1. Combine plot 1A-1 and 1B-1 into a single figure. Include their titles and short figure description (figure legend).
1. Paste the code you used to generate your final figure(s) below:
||
|:--|
| <br> |
<br>


#### Question 2 - What are some of the most abundant microbes when viewed at different taxonomic resolutions? 

Approach: Plot progressively lower level taxa for all individuals, subsetting most abundant from each rank. 

**Step 2A. Plot Phyla across all subjects and identify the most abundant Phyla.** Specifically, your plot should show Phyla diversity across all 21 individuals. 
- Refer to the “Explore 16S rRNA Data with phyloseq” tutorial for help using the plot_bar() function.
- Use the following code as a template:


``` r
plot_bar(miso, "fill in the blank", fill = "fill in the blank", title = "choose a name for your graph") + geom_bar(aes(color = fill in the blank, fill = fill in the blank), stat = "identity", position = "stack")
```

|2A-1. Insert the resulting plot below:|
|:--|
| <br> |
<br>

|2A-2. Enter the name of the most abundant Phyla below:|
|:--|
| <br> |
<br>

**Step 2B. Subset the most abundant Phyla, and plot Order (Skip Class!)**
- Refer to the “Subset taxonomy” section of the “Explore 16S rRNA Data with phyloseq” tutorial for help using the subset_taxa and  plot_bar() functions.
- Use the following code as a template:


``` r
subset = subset_taxa(miso, Phylum == "fill in the blank")
plot_bar(subset, "subject", fill = "Order", title = "choose a name for your graph") + 
  geom_bar(aes(color = "fill in the blank", fill = "fill in the blank"), stat = "identity", position = "stack")
```

|2B-1. Insert the resulting plot below:|
|:--|
| <br> |
<br>

|2A-2. Enter the name of the most abundant Order below:|
|:--|
| <br> |
<br>

**Step 2C. Subset the most abundant Order, and plot associated Family**
- Refer to the “Subset taxonomy” section of the “Explore 16S rRNA Data with phyloseq” tutorial for help using the subset_taxa and  plot_bar() functions.
- Use the following code as a template:


``` r
subset = subset_taxa(miso, Order == "fill in the blank")
plot_bar(subset, "fill in the blank", fill = "Family", title = "choose a name for your graph") + 
  geom_bar(aes(color = fill in the blank, fill = fill in the blank), stat = "identity", position = "stack")
```

|2C-1. Insert the resulting plot below:|
|:--|
| <br> |
<br>

|2C-2. Enter the name of the most abundant Family below:|
|:--|
| <br> |
<br>

**Step 2D.  Subset most abundant Family, and plot associated Genus**
- Refer to the “Subset taxonomy” section of the “Explore 16S rRNA Data with phyloseq” tutorial for help using the subset_taxa and  plot_bar() functions.
- Use the following code as a template:


``` r
subset = subset_taxa(miso, Family == "fill in the blank")
plot_bar(subset, "fill in the blank", fill = "Genus", title = "choose a name for your graph") + 
  geom_bar(aes(color = fill in the blank, fill = fill in the blank), stat = "identity", position = "stack")
```

|2D-1. Insert the resulting plot below:|
|:--|
| <br> |
<br>

|2D-2. Enter the name of the most abundant Genus of your chosen Family below:|
|:--|
| <br> |
<br>

**Step 2E.  Subset the most abundant Genus, and plot associated Species**
- Refer to the “Subset taxonomy” section of the “Explore 16S rRNA Data with phyloseq” tutorial for help using the subset_taxa and  plot_bar() functions.
- Use the following code as a template:


``` r
subset = subset_taxa(miso, Genus == "fill in the blank")
plot_bar(subset, "fill in the blank", fill = "fill in the blank", title = "choose a name for your graph") + 
  geom_bar(aes(color = fill in the blank, fill = fill in the blank), stat = "identity", position = "stack")
```

- Note, given the many different Species associated with an abundant Genus, we may need to reduce the legend text and key size in order to visualize the plot better. 
- You can do so by adding the following lines of code:


``` r
theme(legend.text=element_text(size=6)) + 
theme(legend.key.size = unit(6, "pt"))
```


|2E-1. Insert the resulting plot below:|
|:--|
| <br> |
<br>

|2E-2. Enter the name of the some of the most abundant species below:|
|:--|
| <br> |
<br>

|2E-3. After looking through all your plots, summarize your conclusion regarding individual microbiome composition diversity. Explain what reasoning led you to your conclusion.|
|:--|
| <br> |
<br>

A suggestion for your poster: 
- Combine 4 plots into a single Figure showing your subsetting of the most abundant Order, Family, Genus, and Species. Skip showing Phyla because the group working on Activity 1 will have Phyla data and show a plot for that. Include title and short figure description (figure legend).
- Paste the code you used to generate your final figure(s) below:
| |
|:--|
| <br> |
<br>

#### Question 3 - Does gender contribute to individual microbiome variation? 

Approach: First survey the differences in microbiome across gender at the level of phyla and species, and identify potential candidates that may differ between males and females. Then, plot your candidates of interest  and additional candidate microbes previously associated with  gender-based variation.

**Step 3A. Perform an initial survey to see if there are any differences in phyla and species composition between genders.** Specifically, your plot should show phyla diversity within male and female groups.
- Refer to the “Explore 16S rRNA Data with phyloseq” tutorial for help using the plot_bar() function.
- Use the following code as a template:


``` r
plot_bar(miso, "fill in the blank", fill = "fill in the blank", title = "fill in the blank") + 
geom_bar(aes(color = fill in the blank, fill = fill in the blank), stat = "identity", position = "stack")
```

|3A-1. Insert the resulting plot below:|
|:--|
| <br> |
<br>

Consider any initial differences you see, then  choose one high-abundant and one low-abundant candidate Phylum that shows hints of being differentially abundant between genders.

|3A-2. Record the phylum you chose:|
|:--|
| <br> |
<br>

**Step 3B. Test gender-based difference in Species for the high abundant phylum you selected.** Specifically, your plot should show species diversity within male and female groups for only your phylum of choice.

- Refer to the “Subset taxonomy” section of the “Explore 16S rRNA Data with phyloseq” tutorial for help using the subset_taxa and  plot_bar() functions.
- Use the following code as a starter:


``` r
subset = subset_taxa(miso, Phylum == "fill in the blank")

plot_bar(subset, "fill in the blank", fill = "Species", title = "choose a name for your graph") + 
  geom_bar(aes(color = fill in the blank, fill = fill in the blank), stat = "identity", position = "stack")
```

- Note, given the many different Species associated with an abundant Genus, we may need to reduce the legend text and key size in order to visualize the plot better. 
- You can do so by adding the following lines of code:


``` r
theme(legend.text=element_text(size=6)) + 
theme(legend.key.size = unit(6, "pt"))
```


|3B-1. Insert the resulting plot below:|
|:--|
| <br> |
<br>

|3B-2. Do you observe any differences in species based on gender?|
|:--|
| <br> |
<br>

**Step 3C. Test gender-based difference in Species for the low abundant phylum you selected.** Specifically, your plot should show species diversity within male and female groups for only your phylum of choice.
- Refer to the “Subset taxonomy” section of the “Explore 16S rRNA Data with phyloseq” tutorial for help using the subset_taxa and  plot_bar() functions.
- Use the code you used in Step 3B as a template for your code

|3C-1. Insert the resulting plot below:|
|:--|
| <br> |
<br>

**Step 3D:  Plot the individual abundance of 2 candidate microbes for gender differences based on your analysis above,  and/or the curated menu of microbes below (previously associated with gender variation), with color denoting gender.** Specifically, your plot should show the chosen microbial group across 21 subjects with the bars colored by gender.

- Refer to the “Subset taxonomy” section of the “Explore 16S rRNA Data with phyloseq” tutorial for help using the subset_taxa and  plot_bar() functions.
- Use the following code as a template:


``` r
subset = subset_taxa(miso,  Phylum == "fill in the blank")
plot_bar(subset, "subject", fill = "gender", title = "fill in the blank") + 
 geom_bar(aes(color = gender, fill = gender), stat = "identity", position = "stack")
```

Here is the candidate list of different microbes previously implicated in  gender-based variation. 
- Phylum: Proteobacteria
- Order: Clostridiales
- Family: Ruminococcaceae
- Genus: Prevotella
- Genus: Fusobacterium
- Species: muciniphila 

|3D-1. Insert the plot from your first chosen microbial group below:|
|:--|
| <br> |
<br>

|3D-2. Insert the plot from your second chosen microbial group below:|
|:--|
| <br> |
<br>

|3D-3. Based on the all graphs you made, did you identify any candidate Phylum or Species that may differ between genders?|
|:--|
| <br> |
<br>

|3D-4. Based on the graphs you made, what conclusion can you make about microbiome differences  between genders? |
|:--|
| <br> |
<br>

|3D-5. Which seems to have more effect on microbial compositions? Gender or individual subject?|
|:--|
| <br> |
<br>

**A suggestion for your poster:** 
- Combine the 2 plots that cover the entire dataset (3A-1 and 3B-1) and 2 plots from exploring microbial groups (3D) to make one figure summarizing your findings for gender based differences in microbial composition. 
- Include titles and a short figure description (figure legend).
- Paste the code you used to generate your final figure(s) below:
| |
|:--|
| <br> |
<br>

#### Question 4 - Does age contribute to individual microbiome variation?  

Approach: Survey the differences in microbiome across age, refining the plot to accommodate a continuous variable (age) and unequal sample sizes (some individuals in the study are the same age). Then, test if there is a shift in microbiome abundance of phyla Firmicutes and Bacteroidetes, two phyla suggested previously to change with age. 

**Step 4A. Perform an initial survey to see if there are any differences in phyla related to age.** Specifically, your plot should show the relationship phyla diversity and age of an individual.
- Refer to the “Explore 16S rRNA Data with phyloseq” tutorial for help using the plot_bar() function.
- Use the following code as a template
plot_bar(miso, "fill in the blank", fill = "fill in the blank", title = "fill in the blank") + 
geom_bar(aes(color = fill in the blank, fill = fill in the blank), stat = "identity", position = "stack")



``` r
plot_bar(miso, "fill in the blank", fill = "fill in the blank", title = "fill in the blank") + 
geom_bar(aes(color = fill in the blank, fill = fill in the blank), stat = "identity", position = "stack")
```

|4A-1. Insert the resulting plot below: |
|:--|
| <br> |
<br>

- You probably found it difficult to discern any differences.
- Abundance is additive, so having more samples of the same age will result in adding the abundances together, so if there are say 2 samples with age 27 (as is the case), the abundance of the bar will be much higher than other ages that have only one individual.

**Step 4B.  Merge samples by age, then re-normalize and finally re-plot Phyla by age.**

1. Merge samples of the same age, saving  the resulting phyloseq object as ‘merge’. You will probably get a warning message letting you know “NAs were introduced by coercion.” That is OK.


``` r
merge <- merge_samples(miso, "age")
```

2. Check your merged phyloseq object.  Your new  ‘merge’ object should have 16 samples corresponding to 16 unique ages in the MISO dataset.


``` r
merge

phyloseq-class experiment-level object
otu_table()   OTU Table:         [ 1702 taxa and 16 samples ]
sample_data() Sample Data:       [ 16 samples by 32 sample variables ]
tax_table()   Taxonomy Table:    [ 1702 taxa by 9 taxonomic ranks ]
```
3. Normalize the sample counts using the function transform_sample_counts. Our function,  (100* x/sum(x)) will transform all the samples into proportions.


``` r
merge <- transform_sample_counts(merge, function(x) 100 * x/sum(x))
```
4. Re-plot Phyla by age.

``` r
plot_bar(merge, x= "age", fill = "fill in the blank", title = "fill in the blank") +
  geom_bar(aes(color = fill in the blank, fill = fill in the blank), stat = "identity", position = "stack")
```
5. If you need to decrease the size of your legend key and text to fit, add code below to your plot after adding a + to the end of the geom_bar  line:

``` r
theme(legend.text=element_text(size=6)) + 
theme(legend.key.size = unit(6, "pt"))
```

|4B-1. Insert the resulting plot below:|
|:--|
| <br> |
<br>


|4B-2. Do you observe any candidate Phyla that changes with age?|
|:--|
| <br> |
<br>

**Step 4C. Candidate Phyla implicated in age variation include Firmicutes and Bacteroidetes. Plot these specific phyla on their own, separately, to observe any shift that occurs with age.** Use your new merged and normalized  ‘merge’ phyloseq object as input.
- Refer to the “Subset taxonomy” section of the “Explore 16S rRNA Data with phyloseq” tutorial for help using the subset_taxa and  plot_bar() functions.
- Use the following code as a template:


``` r
subset = subset_taxa(merge,  Phylum == "fill in the blank")
plot_bar(subset, "age", fill = "fill in the blank", title = "fill in the blank") + 
 geom_bar(aes(color = fill in the blank, fill = fill in the blank), stat = "identity", position = "stack")
```

|4C-1. Insert the plot that graphs the relationship of age to the Phylum Firmicutes below:|
|:--|
| <br> |
<br>

|4C-2. Do you observe any changes in Phyla based on age?|
|:--|
| <br> |
<br>

|4C-3. Insert the plot that graphs the relationship of age to the Phylum Bacteroidetes below:|
|:--|
| <br> |
<br>

|4C-4 Do you observe any changes in Phyla based on age?|
|:--|
| <br> |
<br>

|Step 4C-5: Based on the graphs you made, did you identify any candidate Phylum that may differ between genders?|
|:--|
| <br> |
<br>

**A suggestion for your poster:** 
- Combine 2-4 of your plots to make one figure summarizing Phylum and Species age-based differences you observed in the MISO study. Include titles and short figure description (figure legend). 
- Paste the code you used to generate your final figure(s) below:
| |
|:--|
| <br> |
<br>

### Grading criteria

- Download this assignment as Microsoft Word (.docx) and upload on Canvas

### Footnotes

#### Resources

[Google Doc](https://docs.google.com/document/d/1dTRjAHHXeuzXqBOl-h80MRvNxxpMKfT-F_YLIKaxzmo/edit?usp=sharing)

#### Contributions and affiliations

- Valeriya Gaysinskaya, Johns Hopkins University
- Gauri Paul, Clovis Community College
- Frederick Tan, Johns Hopkins University
- Sayumi York, Notre Dame of Maryland University


