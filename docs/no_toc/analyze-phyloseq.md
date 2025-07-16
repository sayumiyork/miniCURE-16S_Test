

<!-- Set up code of OTTR Book-->



# Analyzing 16S rRNA Data with phyloseq

## Analyzing 16S rRNA Data with phyloseq

<!-- Intro text -->


## Lecture - Analyzing 16S rRNA Data with phyloseq

*Estimated time: *

<img src="resources/images/analyze-phyloseq_files/figure-html//1QZbSBPOGkBeizh1L45C6EaktOxl6pqrTDGNIncHQ5lY_g35f391192_00.png" alt="Image test" width="100%" style="display: block; margin: auto;" />

[Lecture](https://docs.google.com/presentation/d/1QZbSBPOGkBeizh1L45C6EaktOxl6pqrTDGNIncHQ5lY/edit?usp=sharing)


## Activity - Exploring 16S rRNA Data with phyloseq

To analyze bacterial diversity based on 16S rRNA gene sequencing using data from the “Impact of a 7-day homogeneous diet on interpersonal variation in human gut microbiomes and metabolomes” by Guthrie et al., 2023. This study is also referred to as the MISO study for “Microbiome Individuality and Stability Over Time” because the study aims to understand variation (or stability) of microbiomes across individuals.

This activity aims to analyze metagenomic diversity using the following R packages:

- **phyloseq**: A popular package for taxonomy profiling
- **DESeq2**: A package originally designed for differential expression which we will use for differential abundance
- **ggplot2**: A tidyverse package that produces high-quality figures

### Learning objectives

1. Use phyloseq to cluster samples based on the similarity of their microbial compositions using multidimensional scaling methods (NMDS or PCoA)
1. Use phyloseq to profile alpha diversity (Shannon and Simpson’s indices)
1. Use DESeq2 to perform differential abundance analysis


### Introduction
16S data can be manipulated and visualized in a variety of ways. In Google Sheets, we explored the data manually to gain an understanding at the level of 1-10 ASVs. Through phyloseq we collapsed ASVs with the same taxonomic annotation to survey microbial diversity and perform the same exploration across the entire dataset. In this activity, we will use the functions of phyloseq and DESeq2 that are more advanced. These analyses would be extremely difficult and tedious to do manually and will allow us deeper insights into our dataset. We will cluster samples based on similarity of ASV counts, survey alpha diversity, and search for differentially abundant ASVs between different groups.


### Activity 1 – Analyze 16S rRNA Data with phyloseq tutorial

*Estimated time: 35 min*

**Activity 1. Explore a phyloseq object through the “Analyze 16S rRNA Data with phyloseq” tutorial on SciServer.**

1. Log into SciServer, click on compute, and create a new C-MOOR LearnR container.  When creating a container, remember to:

- Use the “C-MOOR LearnR (Bioconductor 3.17)” image (not the Bioconductor 3.16)
- Check the box next to Data volume “C-MOOR Data”

2. Start the “Analyze 16S rRNA Data with phyloseq” tutorial. Visit SciServer Guides and FAQs. If you need assistance accessing the tutorial.
3. To move through the activities click “Continue” at the bottom of the screen. When you are done with a topic, click “Next Topic” to move on.
4. This tutorial has small boxes in which you can enter and run short lines of code to analyze the data.
5. As you work through the tutorial, take snapshots of your work and paste your answers in the grey boxes below:

**1-1. Take a snapshot and paste the code for an alpha diversity plot (Simpson) from the quiz question:** What male subject has the data point for the LOWEST alpha diversity? HINT: Use subset_samples() to subset males, and specify individuals (subject) on x-axis of the alpha diversity plot

| |
|:-|
| <br> |

**1-2. Take a snapshot and paste the code for a PCoA plot from the quiz question:** 
In a PCoA with only data from ASVs with the class Bacteroidia, what is the percent of variance in the dataset explained by principal coordinate 1? HINT: You will need to change the code subsetting phylum and Firmicutes

- Subsets the Bacteroidetes phylum
- Color is by subject 
- Shape is by timepointgroup

| |
|:-|
| <br> |

**1-3. Take a snapshot and paste the code for the differential abundance plot for the quiz question:**
Which of the following Phylum have ASVs that are differentially abundant between the subject S02 and subject S03?

| |
|:-|
| <br> |

### Activity 2 – Try it out questions

*Estimated time: 60 min*

With your group, perform some exploratory data analysis selecting from one of the four questions below or coming up with your own question.  When you are done, copy and paste your results into the [class poster](---).

There are 4 different questions for groups to explore. Take a look at the four questions below and go to the section of your chosen question for more instructions!

#### Question 1. How sensitive is microbial diversity to variables like diet, age and gender?

Alpha diversity is a measure that estimates how the distribution of microbes changes due to a variable (or metadata category). Alpha diversity measures changes in the richness (the number of different organisms or ASVs) and evenness (how evenly are these organisms distributed in terms of their abundance). Using the “MISO” study dataset we will use Simpson (or specifically, Gini-Simpson) alpha diversity to evaluate changes in microbial diversity in individuals due to different metadata variables.  

Approach: Plot Simpson alpha diversity using plot_richness() command in phyloseq and assess the impact of different study variables on changes in microbial diversity. Identify variables that impact alpha diversity. Visible shifts in alpha diversity  suggest a shift in microbial diversity, and a higher alpha diversity value indicates an increase in alpha diversity (either richness or abundance).

1. Evaluate the impact of diet on alpha diversity by plotting  ASVs based on “timepointgroup” variable.
1. Evaluate the impact of individuality on alpha diversity by plotting ASVs based on “subject” variable.
1. Evaluate the impact of gender on alpha diversity by plotting ASVs based on “age” variable.
1. Evaluate the impact of gender on alpha diversity by plotting ASVs based on “gender” variable.
1. Evaluate the impact of gender on alpha diversity by plotting ASVs based on the 5 different levels of metabolites in the study (Creatinine, PCS, IS, HIPP, PAG).

#### Question 2. Do diet, age, gender and levels of metabolites correlate with microbe variation between individuals?  

PCoA plot is a principal coordinate analysis used to represent similarity between samples (sample microbiomes in our case). Using the “MISO” study dataset, we will use the PCoA plot  to summarize individuals based on ASVs and plot the resulting relationships between individuals. Based on how well color-coding the different variables matches the sample distribution on the PcOA plot, we will aim to help explain potential sources of sample similarity.

Approach: Perform multidimensional scaling (also known as principal component analysis) to establish a relationship between the samples given multivariate data (metadata variables). Using a PcOA plot (via commands ordinate() and plot_ordination() in phyloseq), you will condense the original high-dimensional data into a low-dimensional one by converting data to distance map (matrix) with 2 dimensions, x and y, that best explain variability in your data. From your PCoA plot you will assess the contribution of different study variables to sample diversity and identify variables that correlate with sample diversity. In a PcOA plot, samples with similar microbial profiles will be plotted close and may appear as groups.

1. Make a PCoA plot, ordinate on the entire dataset (all ASVs) and color by individual. Investigate the shape of the resulting PCoA plot. 
1. Correlate PCoA plot shape with metadata variables by coloring the PCoA plot with different variables including diet, subject, age and gender. Do any of the variables correlate with the shape of PCoA plot and data groupings?
1. Correlate PCoA plot shape with the levels of metabolites in the study (Creatinine, PCS, IS, HIPP, PAG). From the color-coding pattern, identify 1. which variables help potentially explain the data groups formed in the PCoA plot.
Subset “HD”, ordinate on “HD”, and make a new PCoA plot.

#### Question 3. What microbes (ASVs) differ between males and females, and does age have an impact?

Approach: Perform DESeq2 differential abundance analysis between females and males and determine how many differentially abundant microbes are there between the sexes. Then examine if age has a further impact on the differential abundance of the microbes between the sexes. 

1. Perform DESeq2 analysis between females and males and identify differences. 
1. Test if younger age contributes to differential microbe abundance between females and males by subsetting younger (< 50 years old) individuals.
1. Test if older  age contributes to differential microbe abundance between females and males by subsetting older (> 50 years old) individuals.

#### Question 4. Is there diet and age interaction and what microbes (ASVs) correlate with changes in diet-age interaction?

Approach: Use alpha diversity measure and DESeq2 tools to answer this question. Using alpha diversity, determine if there is an interaction between diet and age. Then use DESeq2 to see if any ASVs are associated with changes in die-age interaction. Using Simpson alpha diversity measure (or specifically, Gini-Simpson) evaluate how microbial diversity changes with age and diet in general, or age and BD, HD and WO diet specifically. Then, use DESeq2 to evaluate if younger or older age changes ASVs associated with diet.

1. Plot alpha diversity based age for the population in general, and then for individuals subsetted for BD, HD and WO diets. Look for shifts in alpha diversity with change in diet.
1. Perform DESeq2 analysis based on the diet for the population in general, establishing baseline differential abundance between dietary groups HD and BD.
1. Perform DESeq2 analysis based on the diet for the younger (<= 50 yo) and older (>=50 yo) individuals, evaluating age-associated changes in differential abundance between dietary groups HD and BD.



### Grading criteria

- Download this assignment as Microsoft Word (.docx) and upload on Canvas

### Footnotes

#### Resources

[Google Doc](https://docs.google.com/document/d/1OWgUwaT2MlSd-qq7wSlB3BnM-cq_GTxEyy38HV5ajoU/edit?usp=sharing)

#### Contributions and affiliations

- Valeriya Gaysinskaya, Johns Hopkins University
- Gauri Paul, Clovis Community College
- Frederick Tan, Johns Hopkins University
- Sayumi York, Notre Dame of Maryland University


## Try it Question 1 - How sensitive is microbial diversity to variables like diet, age and gender

Approach: Plot Simpson alpha diversity using plot_richness() command in phyloseq and assess the impact of different study variables on changes in microbial diversity. Identify the variables that impact alpha diversity. Visible shifts in alpha diversity measure suggests a shift in microbial diversity, and higher alpha diversity value indicates an increase in alpha diversity.

**Note, when plotting this data you may get a warning below. That is ok!**


``` r
Warning: The data you have provided does not have any singletons. This is highly suspicious. Results of richness estimates (for example) are probably unreliable, or wrong, if you have already trimmed low-abundance taxa from the data.We recommended that you find the un-trimmed data and retry.
```

Refer to the “alpha diversity” section of the  “Analyze 16S rRNA Data with phyloseq” tutorial for help using the plot_richness() function.

### Step  1A. Plot alpha diversity of the full MISO dataset by subject (individuals).

- subject is on the x-axis
- Color is by subject
- Use the following code as a template:


``` r
plot_richness(miso_counts, x="fill in the blank", 
              color="subject", 
              measures= "Simpson")
```

|1-A. Paste the resulting plot below:|
|:--|
| <br> |
<br>

**1A-2. Based on the alpha plot above, is individuality a strong determinant of microbial alpha diversity (richness and evenness) within an individual? Explain.**

How close are the 5 points for an individual? Are individual data points closer to each other or to the 5 points of another individual? Give examples of individuals in your explanation (e.g. compare S26 and S30, or S02 and S09).

| |
|:-|
| <br> |

Some individual alpha diversity profiles appear to have “outliers”, such that e.g. one of the sample points appears separate from the rest. E.g., individuals S03, S10 and S31 seem to have 1 outlier sample. **Speculate in general on what such singleton “outliers” could mean including recalling what the 5 points represent, evoking concepts of replicates, thinking about sampling and real biology.**

| |
|:-|
| <br> |

### Step  1B. Plot alpha diversity of the full MISO dataset, by timepointgroup.

- timepoint group is on the x-axis
- Color is by subject
- Use the following code as a template:



``` r
plot_richness(miso_counts, x="fill in the blank", 
              color="fill in the blank", 
              measures= "Simpson")
```

|1B-1. Paste your plot below:|
|:--|
| <br> |
<br>

|1B-2. Based on the alpha plot above, does diet have an impact on microbial diversity (richness and evenness) of individuals? Explain - do you observe a shift up or down in data distribution? |
|:--|
| <br> |
<br>

### Step  1C. Plot alpha diversity of the full MISO dataset by age.

- age is on the x-axis
- Color is by subject
- Use the following code as a template:


``` r
plot_richness(miso_counts, x="fill in the blank", 
              color="fill in the blank", 
              measures= "Simpson")
```

|1C-1. Paste your plot below:|
|:--|
| <br> |
<br>

**1C-2. Based on the alpha plot above, does age have an impact on microbial diversity of individuals?** Explain - do you observe a shift up or down in data during ageing? Do you observe a tighter data distribution in younger or older individuals? Which group, younger (< 50 yo) or older (>50 yo) has higher and tiger overall distribution?

| |
|:-|
| <br> |

### Step  1D. Plot alpha diversity of the full MISO dataset by gender.

- gender is on the x-axis
- Color is by subject
- Use the following code as a template:


``` r
plot_richness(miso_counts, x="fill in the blank", 
              color="fill in the blank", 
              measures= "Simpson")
```

|1D-1. Paste your plot below:|
|:--|
| <br> |
<br>

|1D-2. Based on the alpha plot above, does gender have an impact on microbial diversity? Explain. Which group has a tighter distribution? Which group overall has a more diverse microbiome, males or females? Which microbiomes are more similar to each other, male or female microbiomes?|
|:--|
| <br> |
<br>

### Step  2. Plot alpha diversity of the full MISO dataset, grouping based on levels for 5 different metabolites: Creatinine, PCS, IS, HIPP, PAG.

Plot alpha diversity for the 5 metabolites independently then choose your favorite metabolite (e.g. one with most difference) and show plot below. 

- metabolite on the x-axis  (one at a time: Creatinine, PCS, IS, HIPP, PAG)
- Color is by subject
- Use the following code as a template:


``` r
plot_richness(miso_counts, x="fill in the blank metabolite name", 
              color="fill in the blank", 
              measures= "Simpson")
```

|2A-1. Paste your metabolite plot(s) below:|
|:--|
| <br> |
<br>


|2A-2. Which metabolite did you choose to show and why? Any difference between microbiomes for individuals with low versus high metabolite levels?|
|:--|
| <br> |
<br>

### Step  3. Select data for poster and include the code used to generate the figure.

1. Prepare your final figure and associated code for the poster. 
1. Figure suggestion: A 2-part figure with Figure A showing alpha diversity based on your favorite variable (subject, timepointgroup, age, or gender), and Figure B, showing alpha diversity with your favorite metabolite (Creatinine, PCS, IS, HIPP, or PAG). 

- Ensure you have a figure legend that explains your final figure.
- Ensure you submit the code you used to generate your final figure.

|3A-1. Paste final poster figure and code below:|
|:--|
| <br> |
<br>

## Try it Question 2 - Do diet, age, gender and levels of metabolites correlate with microbe variation between individuals 

Approach: Perform multidimensional scaling (also known as principal component analysis) to establish a relationship between the samples given multivariate data (metadata variables). Using a PcOA plot (via commands ordinate() and plot_ordination() in phyloseq), you will condense the original high-dimensional data into a low-dimensional one by converting data to distance map (matrix) with 2 dimensions, x and y, that best explain variability in your data. From your PCoA plot you will assess the contribution of different study variables to sample diversity and identify variables that help explain sample diversity. In a PcOA plot, samples with similar microbial profiles will be plotted close and may appear as “clusters”.

### Step  1. Make a PcOA plot, ordinating on the entire miso dataset, and coloring by individual. Investigate resulting plot shape.

- Ordination is a term used to summarize a multidimensional dataset when projected onto a low-dimensional space (like X & Y axes) and then observing any pattern the data may possess with a visual inspection. 
- Subsequent coloring of the pattern with metadata variables can reveal underlying relationships between data and experiment variables. 

- color - by subject
- Include a title for your PCoA plot
- Use the following code as a template:


``` r
#Ordinate 
miso.pcoa <- ordinate(miso, method="PCoA", distance="bray") 

#Plot PCoA
plot_ordination(miso, miso.pcoa, 
        color = "fill in the blank",  
        title="fill in the blank")
```


|1A-1. Paste your plot below:|
|:--|
| <br> |
<br>

|1A-2. Describe the shape of your PCoA plot. Does the PCoA organize the into groups?  Is there any pattern?|
|:--|
| <br> |
<br>


|1A-3. Do you observe sample clustering by individual? Provide examples and an explanation.|
|:--|
| <br> |
<br>


|1A-4. Offer one question you want to ask about this PCoA plot?|
|:--|
| <br> |
<br>

### Step  2. Using the PCoA plot from Step 1 above, look for any correlations between the shape of your PCoA plot and diet, gender and age

**Step 2A. Using the PCoA plot from Step 1, look for any correlations between the shape of your PCoA plot and diet?** 

How well is your data explained by the variation in the diet - look for signs of correlation between PCoA shape and variable “timepointgroup” representing BD, HD and WO diets. Note that since we are using the same plot, we do not need to re-ordinate (no ordinate() function).

- Color - by timepointgroup
- Include a title for your PcOA plot
- Use the following code as a template:



``` r
plot_ordination(miso, miso.pcoa, 
        color = "fill in the blank",  
        title="fill in the blank")
```

|2A-1. Paste your plot below:|
|:--|
| <br> |
<br>

|2A-2 Did coloring the ‘miso’ PCoA plot by timepointgroup explain any variation in your data? E.g. did each of the 3 data groups/clusters correspond to each of the 3 timepointgroups  or not? E.g. does the coloring appear randomly distributed or not?|
|:--|
| <br> |
<br>

**Step  2B. Using the PCoA plot from Step 1, look for any correlations between the shape of your PCoA plot and gender? ** 

How well is your data explained by the variation in the gender - look for signs of correlation between PcOA shape and variable “gender”. 

- Color - by gender
- Include a title for your PcOA plot
- Use the following code as a template. 



``` r
plot_ordination(miso, miso.pcoa, 
        color = "fill in the blank",  
        title="fill in the blank")
```

|2B-1. Paste your plot below:|
|:--|
| <br> |
<br>

|2B-2 Did coloring of the ‘miso’ PCoA plot by gender explain any variation in your data? E.g. does the coloring appear randomly distributed or not?|
|:--|
| <br> |
<br>

**Step  2C. Using the PCoA plot from Step 1, look for any correlations between the shape of your PCoA plot and age? How well is your data explained by the variation in the age - look for signs of correlation between PcOA shape and variable “age”.** 

- Color - age
- Include title name for your PcOA plot
- Use the following code as a template. To enhance the color range of the age variable, additionally included below (in blue) is the command to specify the color gradient with yellow–to-blue gradient. 
- Try running the code with and without the scale_colour_gradient() command to appreciate the difference.


``` r
plot_ordination(miso, miso.pcoa, 
        color = "fill in the blank",  
        title="fill in the blank") + 
scale_colour_gradient(low = "red", high = "green") 
```

|2C-1. Paste your plot below:|
|:--|
| <br> |
<br>

|2C-2 Did coloring of the ‘miso’ PCoA plot by age explain any variation in your data? E.g. Does the coloring appear randomly distributed or not? Is there any hint of a correlation between age and groups of data on the left or the right?|
|:--|
| <br> |
<br>

### Step 3. Using the PCoA plot from Step 1, look for any correlations between the shape of your PCoA plot and the level of metabolites. 

How well is your data correlated with the variation in the 5 metabolites  - Creatinine, PCS, IS, HIPP, or PAG? Test each metabolite by coloring each metabolite at a time, then, choose your favorite metabolite (e.g. one with most difference) and show the plot below. 

- Color - metabolite one at a time: Creatinine, PCS, IS, HIPP, PAG
- Include a title for your PcOA plot
- Use the following code as a template:


``` r
plot_ordination(miso, miso.pcoa fill in the blank metabolite name, 
        color = "fill in the blank",  
        title="fill in the blank") + 
scale_colour_gradient(low = "yellow", high = "blue")
```

|3A-1. Paste your metabolite plot(s) below:|
|:--|
| <br> |
<br>

|3A-2. Which metabolite did you choose to show and why? Any difference between microbiomes for individuals with low versus high metabolite levels? Any association between metabolite level and microbiome diversity?|
|:--|
| <br> |
<br>

### Step 4. One way of checking if the metabolite levels indeed correlate with your data, is to see if subsetting smaller chunks or specific chunks of the data will still maintain the metabolite-data relationship or break it. 

Using subset() command, subset out e.g. HD diet specifically, and then BD diet. Then, generate new PcOA plots and see if the correlation with your metabolite of interest still holds. 

**Step 4A. Subset “HD”, ordinate on “HD”, and make a new PCoA plot.**

- Subset data - by the timepointgroup “HD”
- Ordinate  - misoHD
- Color - by your selected metabolite from part 3
- Include a title for your PcOA plot
- Use the following code as a template:

a. Subset only “HD” timepoint from your miso data, creating a new phyloseq object called “misoHD”


``` r
misoHD = subset_samples(miso, timepointgroup == "fill in the blank") 
```

b. Ordinate using only “HD” subset, creating a new ordination matrix called “pcoa.misoHD”


``` r
pcoa.misoHD <- ordinate(misoHD, method="PCoA", distance="bray") 
```

c. Make a PCoA plot using your  “HD” subset.


``` r
plot_ordination(misoHD, pcoa.misoHD, 
        color = "fill in the blank", 
        title="fill in the blank")
```

|4A-1. Paste your plot below for HD subset:|
|:--|
| <br> |
<br>

|4A-2 Did subsetting by the timpointgroup “HD” maintain your data’s relationship to your chosen metabolite? Did the shape of the plot change or stay the same with “HD” subsetting? Can you conclude if your metabolite of choice correlates with HD diet?|
|:--|
| <br> |
<br>

**Step 4B. Repeat the analysis on only the BD timepoint group samples. Subset “BD”, ordinate on “BD”, and make a new PCoA plot.**

- Subset data - by the timepointgroup “BD”
- Ordinate  - misoBD
- Color - by your selected metabolite from part 3
- Include a title for your PcOA plot
- Use the code above as a template.

|4A-1. Paste your plot below for BD subset:|
|:--|
| <br> |
<br>

|Did subsetting “BD” maintain your data’s relationship to your chosen metabolitelevels? Did the shape of the plot change or stay the same with “BD” subsetting? Explain your results. Can you conclude if your metabolite of choice correlates with sample groups when only BD timepointgroup data is plotted?|
|:--|
| <br> |
<br>

**Step 5A. Select data for poster and include the code used to generate the figure.**

- Prepare your final figure and associated code for the poster. 
- Figure suggestion: A 2-part figure with Figure A showing PCoA plot based on subject and Figure B, showing PCoA plot with your favorite metabolite (Creatinine, PCS, IS, HIPP, or PAG). 
- Ensure you have a figure legend that explains your final figure.
- Ensure you submit the code you used to generate your final figure.

|5A-1. Paste final poster figure and code below:|
|:--|
| <br> |
<br>


## Try it Question 3 - What microbes (ASVs) differ between males and females, and does age have an impact

Approach: Perform DESeq analysis between females and males and determine how many differentially abundant microbes are there between the sexes. Then examine if age has a further impact on the abundance of the microbes between the sexes. 

### Step 3A. Perform differential abundance analysis between genders.

- Design -  is based on gender (no double quotes)
- Groups to compare -   females, F  and males, M (baseline) 
- Plot Phylum on the X-axis and color by Class

- Make sure your graph has a title that includes the comparison you are making (ex. WO vs HD)
- Refer to the “Differential abundance” section of the “Analyze 16S rRNA Data with phyloseq” tutorial for help using the plot_ordination() function.
- Use the code below as a template:

STEP 1: Convert the phyloseq object to a DESeq2 object and specify experimental design


``` r
DESeq2 <- phyloseq_to_deseq2(miso_counts, design = ~ fill in the blank)
```

STEP 2: Select the groups to compare, where the latter group is your baseline


``` r
my_comparision <-c("gender", "fill in the blank", "fill in the blank (baseline)")
```

STEP 3: Run the differential abundance analysis


``` r
Significant_DEseq2_ASVs<-Differential_Abundance(DESeq2, my_comparision, 0.05)
```

STEP 4: Retrieve the list of ASVs with a significant difference in abundance between the chosen groups

``` r
Significant_DEseq2_ASVs
```

STEP 5: Plot the results with your chosen x axis and legend

``` r
ggplot(significant_ASVs, aes(x = fill in the blank, y=log2FoldChange, color= fill in the blank)) + geom_point(size=4, position="jitter") +
  theme(axis.text.x = element_text(angle = -90, hjust = 0, vjust=0.5))+
  ggtitle("fill in the blank")
```

|3A-1. Insert the resulting plot below:|
|:--|
| <br> |
<br>

|3A-2. How many differentially abundant ASVs were identified?|
|:--|
| <br> |
<br>

|3A-3. Give an example of a differentially abundant ASVs that was significantly higher in females than males. Include ASV ID and taxa. HINT: If male was your baseline, then an example of an ASV that is higher in females will have a positive log2FC.|
|:--|
| <br> |
<br>

|3A-4. Give an example of a differentially abundant ASVs that was significantly higher in males than females. Include ASV ID and taxa. HINT: If male was your baseline, then an example of an ASV that is higher in males will have a negative log2FC.|
|:--|
| <br> |
<br>

### Step 3B. Determine the impact of younger age on differential abundance in males and females, by subsetting age < 50 data from the phyloseq object, and performing DESeq2 analysis on this subset.

- Subset phyloseq object to only include younger individuals (age < 50)
- For DESeq2 analysis, keep the design the same as in part A - based on gender
- Groups to compare:  females (F) and males (M, baseline)
- Plot Phylum on the X-axis and color by Class
- Use template code below:

STEP 1: subset by age < 50


``` r
ageA = subset_samples(miso_counts, age <50) 
```

STEP 2: Convert the phyloseq object to a DESeq2 object and specify experimental design


``` r
DESeq2 <- phyloseq_to_deseq2(ageA, design = ~ fill in the blank)
```

STEP 3: Select the groups to compare, where log2FoldChange reported will correspond to  y/x.


``` r
my_comparision <-c("gender", "fill in the blank", "fill in the blank (baseline)")
```

STEP 4: Run the differential abundance analysis 


``` r
significant_ASVs<-Differential_Abundance(DESeq2, my_comparision, 0.05)
```

STEP 5: Retrieve the list of ASVs with a significant difference in abundance between the chosen groups


``` r
significant_DEseq2_ASVs
```

STEP 6: Plot the results with your chosen x axis and legend


``` r
ggplot(significant_ASVs, aes(x = fill in the blank, y=log2FoldChange, color= fill in the blank)) + geom_point(size=4, position = "jitter") +
  theme(axis.text.x = element_text(angle = -90, hjust = 0, vjust=0.5))+
  ggtitle("fill in the blank")
```


|3B-1. Insert the resulting plot below:|
|:--|
| <br> |
<br>


|3B-2. How many differentially abundant ASVs were identified?|
|:--|
| <br> |
<br>


|3B-3. Give an example of a differentially abundant ASVs that was significantly higher in younger females than younger males. Include ASV ID and taxa. HINT: If male was your baseline, then an example of an ASV that is higher in females will have a positive log2FC.|
|:--|
| <br> |
<br>


|3B-4. Give an example of a differentially abundant ASVs that was significantly higher in younger males than younger females. Include ASV ID and taxa. HINT: If male was your baseline, then an example of an ASV that is higher in males will have a negative log2FC.|
|:--|
| <br> |
<br>


|3B-5. How does younger age impact microbe abundance between females and males in general?|
|:--|
| <br> |
<br>

### Step 3C. Determine the impact of older age on differential abundance in males and females, by subsetting age >= 50 data from the phyloseq object, and performing DESeq2 analysis on this subset.

|3C-1. Insert the resulting plot below:|
|:--|
| <br> |
<br>

|3C-2. How many differentially abundant ASVs were identified?|
|:--|
| <br> |
<br>

|3C-3. How does older age impact microbe abundance between females and males in general? |
|:--|
| <br> |
<br>

|3C-4. Comparing fold change plots between younger and older females and males, what is one difference between Phyla distribution?|
|:--|
| <br> |
<br>

### Step  4. Select data for poster and include the code used to generate the figure

Prepare your final figure and associated code for the poster. 

- Figure suggestion: A 3-part figure with Figure A showing fold change differences between males and females in general, Figure B showing gender differences in younger individuals, and Figure C showing gender differences in older individuals. 

- Ensure you have a figure legend that explains your final figure.
- Ensure you submit the code you used to generate your final figure.

|4A-1. Paste final poster figure and code below:|
|:--|
| <br> |
<br>


## Try it Question 4 -  Is there an interaction between diet and age and the microbiome

Approach: Use alpha diversity measure and DESeq2 tools to answer this question. Using alpha diversity, determine if there is an interaction between diet and age. Then use DESeq2 to see if any ASVs are associated with changes in die-age interaction. Using Simpson alpha diversity measure (or specifically, Gini-Simpson) evaluate how microbial diversity changes with age and diet in general, or age and BD, HD and WO diet specifically. Remember, shifts in alpha diversity measure suggest a shift in microbial diversity, with high alpha diversity suggesting high microbial diversity. Then, use DESeq2 to evaluate if ageing changes ASVs associated with diet.

Note, when plotting this data you may get a warning below. That is ok!


``` r
Warning: The data you have provided does not have any singletons. This is highly suspicious. Results of richness estimates (for example) are probably unreliable, or wrong, if you have already trimmed low-abundance taxa from the data.We recommended that you find the un-trimmed data and retry.
```

Refer to the “alpha diversity” section of the  “Analyze 16S rRNA Data with phyloseq” tutorial for help using the plot_richness() function.

### Step  1. Plot alpha diversity based on age for all dietary groups, and then for BD, HD and WO.

**1A-1. Plot alpha diversity based on age for all dietary groups.**

- Subset data - None
- age is on the x-axis
- Color is by subject
- Use the following code as a template:


``` r
plot_richness(miso_counts, x="age",
          	color="subject",
          	title = "miso",
          	measures= c("Simpson"))
```

|Paste your plot below:|
|:--|
| <br> |
<br>

|1A-2. Based on the alpha plot above, is age a good determinant of microbial alpha diversity? Explain. Is there an age-based trend in alpha diversity? |
|:--|
| <br> |
<br>

**1B-1. Plot alpha diversity based on age for BD diet only.**

- Subset data - timepointgroup BD
- age is on the x-axis
- Color is by subject
- Use the following code as a template:



``` r
# Subset only BD samples
miso_counts_BD = subset_samples(miso_counts, timepointgroup == "BD")

plot_richness(miso_counts_BD, x="fill in the blank",
          	color="fill in the blank",
          	title = "fill in the blank",
          	measures= c("Simpson"))
```

|Paste your plot below:|
|:--|
| <br> |
<br>

|1B-2. Based on the alpha plot above, how did subsetting  for BD alter the age-based alpha diversity plot? Did the trend in age-based alpha diversity change? Explain if this makes sense.|
|:--|
| <br> |
<br>

**1C-1. Plot alpha diversity based on age for HD diet only.**

- Subset data - timepointgroup HD
- age is on the x-axis
- Color is by subject
- Use the following code as a template:



``` r
# Subset only HD samples
miso_counts_BD = subset_samples(miso_counts, timepointgroup == "HD")

plot_richness(miso_counts_BD, x="fill in the blank",
          	color="fill in the blank",
          	title = "fill in the blank",
          	measures= c("Simpson"))
```

|Paste your plot below:|
|:--|
| <br> |
<br>

|1C-2. Based on the alpha plot above, how did subsetting  for HD alter the age-based alpha diversity plot? Did the trend in age-based alpha diversity change? Explain if this makes sense.|
|:--|
| <br> |
<br>

**1D-1. Plot alpha diversity based on age for WO diet only.**

- Subset data - timepointgroup WO
- age is on the x-axis
- Color is by subject
- Use the following code as a template:



``` r
# Subset only WO samples
miso_counts_BD = subset_samples(miso_counts, timepointgroup == "WO")

plot_richness(miso_counts_BD, x="fill in the blank",
          	color="fill in the blank",
          	title = "fill in the blank",
          	measures= c("Simpson"))
```

|Paste your plot below:|
|:--|
| <br> |
<br>

|1D-2. Based on the alpha plot above, how did subsetting  for WO alter the age-based alpha diversity plot? Did the trend in age-based alpha diversity change? Explain if this makes sense. Remember, WO has twice as few datapoints as BD and HD since there is only 1 WO timepoint (versus 2 for BD and HD).|
|:--|
| <br> |
<br>

### Step  2. Perform differential abundance analysis comparing HD to BD for the population in general, and then for older individuals specifically (because older individuals produced the biggest diet–age interaction based on alpha diversity).

**Step 2A. Perform differential abundance analysis between HD and BD.** 

- Design -  is based on timepointgroup (no double quotes)
- Groups to compare -   HD and BD (baseline) 
- Plot Phylum on the X-axis and color by Class

- Make sure your graph has a title that includes the comparison you are making (ex. WO vs HD)
- Refer to the “Differential abundance” section of the “Analyze 16S rRNA Data with phyloseq” tutorial for help using the plot_ordination() function.
- Use the code below as a template:

STEP 1: Convert the phyloseq object to a DESeq2 object and specify experimental design

``` r
DESeq2 <- phyloseq_to_deseq2(miso_counts, design = ~ timepointgroup)
```

STEP 2: Select the groups to compare, where the latter group is your baseline

``` r
comparision <-c("timepointgroup", "HD", "fill in the blank (baseline)")
```

STEP 3: Run the differential abundance analysis 

``` r
Significant_DEseq2_ASVs<-Differential_Abundance(DESeq2, comparision, 0.05)
```

STEP 4: Retrieve the list of ASVs with a significant difference in abundance between the chosen groups

``` r
Significant_DEseq2_ASVs
```

STEP 5: Plot the results with your chosen x axis and legend

``` r
ggplot(significant_ASVs, aes(x = Phylum, y=log2FoldChange, color= fill in the blank)) + geom_point(size=4) +
  theme(axis.text.x = element_text(angle = -90, hjust = 0, vjust=0.5))+
  ggtitle("fill in the blank")
```

|2A-1. Insert the resulting plot below:|
|:--|
| <br> |
<br>

|2A-2. How many differentially abundant ASVs were identified?|
|:--|
| <br> |
<br>

|2A-3. Discuss the meaning for your differential abundance plot above. Did you observe few or many differences between BD and HD for the general population (all individuals)? What does that indicate in terms of diet-induced microbiome changes?|
|:--|
| <br> |
<br>

### Step 2B. Perform differential abundance analysis between HD and BD for older individual (> 50 yo.) 

- Subset data - older age (> 50 yo)
- Design -  is based on timepointgroup (no double quotes)
- Groups to compare -   HD and BD (baseline) 
- Plot Phylum on the X-axis and color by Class

- Make sure your graph has a title that includes the comparison you are making (ex. WO vs HD)
- Refer to the “Differential abundance” section of the “Analyze 16S rRNA Data with phyloseq” tutorial for help using the plot_ordination() function.
- Use the code below as a template:

STEP 1: Subset miso_counts object to only include older individuals over age 50

``` r
subset = subset_samples(miso_counts, age >50)
```

STEP 2: Convert the phyloseq object to a DESeq2 object and specify experimental design

``` r
DESeq2 <- phyloseq_to_deseq2(subset, design = ~ timepointgroup)
```

STEP 3: Select the groups to compare, where the latter group is your baseline

``` r
comparision_subset <-c("timepointgroup", "HD", "fill in the blank (baseline)")
```

STEP 4: Run the differential abundance analysis 

``` r
Significant_ASVs_subset <- Differential_Abundance(DESeq2, comparision_subset, 0.05)
```

STEP 5: Retrieve the list of ASVs with a significant difference in abundance between the chosen groups

``` r
Significant_ASVs_subset
```

STEP 6: Plot the results with your chosen x axis and legend

``` r
ggplot(significant_ASVs_subset, aes(x = Phylum, y=log2FoldChange, color= fill in the blank)) + geom_point(size=4) +
  theme(axis.text.x = element_text(angle = -90, hjust = 0, vjust=0.5))+
  ggtitle("fill in the blank")
```

|2B-1. Insert the resulting plot below:|
|:--|
| <br> |
<br>

|2B-2. How many differentially abundant ASVs were identified?|
|:--|
| <br> |
<br>

|2B-3. Discuss the meaning for your differential abundance plot above. Did you observe any differences between BD and HD for the older individuals? How does that compare to general population? Note, by comparison, when subsetting the younger population (<= 50yo), the number of differential ASVs produced is 3.  What does that indicate in terms of diet-age interaction?|
|:--|
| <br> |
<br>

### Step 3. Select data for poster and include the code used to generate the figure.

- Prepare your final figure and associated code for the poster. 
- Figure suggestion: A 4-part figure with top panel: Figure A showing  alpha diversity in general (includes all 3 dietary interventions), and Figure B showing alpha diversity for HD diet only. The bottom panel: Figure C showing differentially abundant ASVs between HD and BD for all ages, and Figure D showing differentially abundant ASVs for older individuals. 
- Ensure you have a figure legend that explains your final figure.
- Ensure you submit the code you used to generate your final figure.


|Paste final poster figure and code below:|
|:--|
| <br> |
<br>


