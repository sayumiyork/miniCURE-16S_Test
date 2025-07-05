

<!-- Set up code of OTTR Book-->



# 16S rRNA Data in spreadsheets

## Exploring 16S rRNA data in spreadsheets

In this section we will look at 16S data in a spreadsheet via Google Sheets. We will familiarize ourselves with the format of 16S data and manipulate just a few ASVs to better understand what kinds of research questions we can ask with the data. Through this exercise we will also come to understand the necessity of more powerful analysis tools in R; sorting through trends in a spreadsheet could take years!


## Lecture - Introducing 16S rRNA Data Using Spreadsheets

*Estimated time: *

![](resources/images/introducing-16S-data_files/figure-docx//14E26SbzaLEDJxAaZ1qjaZcJehAI8q2GHuTokNPKKDTc_g35f391192_00.png){width=100%}

[Lecture](https://docs.google.com/presentation/d/14E26SbzaLEDJxAaZ1qjaZcJehAI8q2GHuTokNPKKDTc/edit?usp=sharing)


## Activity - Introducing 16S rRNA Data Using Spreadsheet


### Learning objectives

1. Explore Amplicon Sequence Variants (ASVs) through the taxonomy profile of select ASVs, and sample metadata for a subset of ASVs.
1. Generate initial research questions based on the above exploratory data analysis

### Introduction
The most popular sequencing technique for the analysis of bacterial diversity is targeted sequencing, or sequencing of a specific gene (or region of a gene, e.g. a hypervariable region of the bacterial 16S ribosomal rRNA gene) using Polymerase Chain Reaction (PCR) to create sequences called amplicons. Sequence variation in the resulting amplicons creates Amplicon Sequence Variants (ASVs). ASVs varying from as little as one single nucleotide are defined as separate ASVs and as little as 1% difference in ASV sequence can be associated with different species. In this activity you will be exploring ASVs generated with sequencing 250 nucleotides (nt) Illumina sequencing, where Amplicon sequence variants (ASVs) were identified.

### Activity 1 – Quick data overview based on 1 sample

*Estimated time: 10 min*

Although the full dataset contains 105 samples from 21 subjects and 5 timepoints (representing 3 dietary conditions), in this activity we will familiarize ourselves with the data by exploring data from 1 sample only.

#### Activity 1-1. Explore data contents using one sample only, namely MISO1-S02-1 (subject 2, timepoint 1). 

Access [‘MISO_PS_Leah_SY_Sample1’](https://docs.google.com/spreadsheets/d/1hpSyjO0H8sXq6C1xM_oGMyv9vCY2qTvfYHVdqO9ZVhk/edit?usp=sharing) file and open it with Google Sheets.

- Rows = ASVs
- Columns = Samples and taxonomy:
  - Col A = ASV id 
  - Cols B-H = Taxonomic information
  - Col I = ASV counts (for sample MISO1-SO2-1)

|1-1.1 How many ASVs are there? HINT: Scroll down to see how many rows are there!|
|:--|
| <br> |

**1-1.2 How many microbes are there in an individual? In other words, what is the total number of ASVs per sample?**

IMPORTANT: An ASV is associated with an individual if it is NOT a zero. Zero means that particular ASV was not found in the individual, so you need to exclude zeroes from your calculations.

- Create an empty new first row for temporary calculations by clicking to insert 1 row above. 
- In the new row, calculate the number of ASVs per sample 1 (excluding the zeroes) using the following formula: =COUNTIF(range, "<>0").  For sample 1 (MISO1-S02-1) enter formula =COUNTIF(I2:I2185, "<>0"). 

| |
|:-|
| <br> |

|1-1.3 What taxonomy is associated with ASV1? Include all taxonomic ranks.|
|:--|
| <br> |

|1-1.4 What taxonomy is associated with ASV2? Include all taxonomic ranks.|
|:--|
| <br> |

|1-1.5 For sample 1 (MISO1-S02-1) what is the ASV1 count?|
|:--|
| <br> |

|1-1.6  For sample 1 (MISO1-S02-1) what is the ASV2 count?|
|:--|
| <br> |

**1-1.7  Plot ASV counts distribution (range of ASV abundance) for sample 1 ( (MISO1-S02-1).**

**A) Make a bar graph of ASV distribution.** To make a bar graph,  hold Command key (or Ctrl on Windows, allows you to select data that are not next to each other) and then highlight columns A, with ASV ids (column “ASV”) and I, with ASV counts (column “MISO1-S02-1”) and go to Insert Chart. 

- Make sure your graph is a bar plot:  click on the 3 dots in the top right corner of the plot → edit chart  and in the Chart editor, under Chart type, selecting Column Chart.
- Copy the bar graph into a box below: click on the 3 dots in the top right corner of the plot, and select copy chart, then, paste it below.

| |
|:-|
| <br> |

|B) What is the highest abundance ASV in sample 1? A simple way to get an answer is to hover over the highest bar in your ASV distribution plot from activity at its highest point.|
|:--|
| <br> |

|C) Describe abundance pattern between ASVs. E.g., is abundance even or spotty and what does that say about ASV/taxa variation?|
|:--|
| <br> |

### Activity 2 – Explore variation between individuals

*Estimated time: 10 min*

One aspect of Guthrie et al. study is the extent to which diet contributes to interpersonal microbiome variation (variation in microbiome between individuals). To this end, authors  ‘normalize’ the diet for all individuals with the same Homogenized Diet (HD) to evaluate how much of an effect the diet has. **The study period is 28 days.** The study has 3 dietary conditions: 1) **BD** (Baseline Diet) which lasted 14 days (2 time points collected), followed by 2) **HD** which lasted 7 days (2 time points collected), followed by 3) **WO** (washout diet),  which lasted for 7 days and simply marks the return to baseline, regular diet (1 time point). 

**To explore variation between individuals, here we simplify the dietary variation to a single condition, WO.**

- For this activity, the data file [MISO_PS_Leah_SY_WO-select](https://docs.google.com/spreadsheets/d/1vD0wbxgYuDlfKA0DF2Km-N4GHL2gRoUaEN_oCrSb2jU/edit?usp=sharing) contains samples pre-filtered for WO condition only (and excludes samples corresponding to BD and HD). 

- Since there is only 1 WO datapoint per individual, each WO sample corresponds to a different individual, so you should see 21 samples.

#### Activity 2-1 - What are the most common ASVs between individuals?

IMPORTANT: An ASV is associated with an individual if it is NOT a zero. Zero means that particular ASV was not found in the individual, so you need to exclude zeroes from your calculations. 

**A) Calculate the number of samples associated with each ASVs. Record first 5 values below.**

- Create an empty new first column for temporary calculations by inserting new column  A (via clicking on column A and selecting to Insert 1 column to the left). Label new column “Occurrence”.
- Starting with the first ASV in row 3, in an empty cell A3 use the following formula: =COUNTIF(range, "<>0").  For example, for ASV1 enter formula = COUNTIF(C3:W3, "<>0"). The answer should be 17 (so 17 of 21 WO  samples have ASV1). 
- Extend the function to all ASVs 

| |
|:-|
| <br> |

**B) Calculate % of samples associated with  each ASV and record the first top 5.**

- Create another new column A and label it “% Occurrence”. 

| |
|:-|
| <br> |

**C) How many ASVs are present in all 21 individuals and what are their ids?  Simply find which ASVs are present in 100% of samples.**

- Copy columns A (% samples) and  C (ASV id)  into a new sheet and Paste Special → Values only
- Delete empty row 1 
- Right-click on Row 1 to Create a filter, then Sort Z to A
- Count the ASVs that have 100 in % samples  

| |
|:-|
| <br> |

#### Activity 2-2. Explore most common ASV taxonomy

- Go the original MISO_PS_Leah_SY_Sample1  google docs and record taxonomic information for most common ASV from the activity above.

- In MISO_PS_Leah_SY_Sample1, Columns B-H correspond to taxonomic information

|2-2.1 What is the taxonomy assigned to the most common ASV you found in Activity above?|
|:--|
| <br> |

|2-2.2 According to the taxonomy for most common ASV  above, what might be the most abundant phyla in the human gut?|
|:--|
| <br> |

### Activity 2-3.  Plot individual  variation in abundance of the most common ASV

**A) Make a bar graph of most common ASV distribution across 21 individuals**
1. In the original MISO_PS_Leah_SY_WO-select find the row corresponding to the most common ASV, from Activity 2-1 above. 
2. Highlight the header row (corresponding to sample IDs) and the row corresponding to most common ASV and go to Insert Chart. Make sure you don’t include the columns with the # of samples  with that ASV and % samples columns.

- Make sure your bar graph is a bar plot:  click on the 3 dots in the top right corner of the plot → edit chart  and in the Chart editor, under Chart type, selecting Column Chart.

- Copy the bar graph into a box below: click on the 3 dots in the top right corner of the plot, and select copy chart, then, paste it below.

| |
|:-|
| <br> |

|B) Comment on the chart above -  how similar is the ASV abundance between individuals?|
|:--|
| <br> |

### Activity 3 – Explore variation within a single individual associated with diet

*Estimated time: 10 min*

Although the full dataset contains 105 samples from 21 subjects and 5 timepoints (representing 3 dietary conditions), in this activity we will zoom into ASV counts data for 1 individual (comprised of 5 samples representing the 5 timepoints collected from that individual).

- Timepoints 1 and 2: BD (Baseline diet) prior to normalization with homogenized diet
- Timepoints 3 and 4: HD (Homogenized diet): normalized to be same for all
- Timepoint 5:  WO (Washout diet),  which simply involves individuals going back to their baseline, regular diet 

#### Activity 3-1 Access ‘MISO_PS_Leah_SY_Subject1’ file and open it with Google Sheets, then explore differences between dietary changes in individual 1 by exploring differences between the 5 sample timepoints.

**3-1.1  Calculate  variation in ASV abundance within individual 1 (MISO1-S02) and record the first 5 values below.** 
This involves plotting counts for ASV 1-10 for MISO1-SO2 timepoints 1 through 5.
To calculate variation within a sample, we will use the VAR.S function in google sheets to calculate variance of a sample.

1. Label an empty Column G  “VAR”. Use this column to calculate variance. 
1. Starting with the first ASV use the following formula: =VAR.S(range) to calculate ASV abundance variation in the 5 samples/timepoints collected for individual MISO1-SO2.  For example, for ASV1 enter formula =VAR.S(B2:F2). The answer should be 14947547.8. 
1. Extend the function to all ASVs and record the first 5 variance values below.

| |
|:-|
| <br> |

**3-1.2  Plot ASVs with highest variance.**

**A) Sort Variance column and record the top 5 values below.** To sort the variance column:

1. Click on the 1st (header) row
1. Right-click to select ‘Create a filter’
1. Sort ‘VAR’ column Z to A (click on the new arrow in the VAR column).

| |
|:-|
| <br> |

**B) Plot ASVs with highest variance.** 
After sorting ASVs based on high to low variance make a plot of ASV counts corresponding to top 15 ASVs with the highest variance. Insert the plot in the grey box below. Here, variance within a sample might suggest variation (difference) between conditions. For example, high variance may come from  the first 2 samples (BD diet) being different from samples 3 and 4 (HD diet).

- To make a bar graph highlight top 16 rows corresponding to sample names and the 15 ASVs with highest variance, for samples MISO1-S02-1 through 5. Exclude highlighting the variance column itself. 
- Go to Insert Chart. For this chart you can highlight the rows starting with title row so as to include sample names in your chart.
- Make sure your  graph is a bar plot:  click on the 3 dots in the top right corner of the plot → edit chart  and in the Chart editor, under Chart type, selecting Column Chart.
- Copy the bar graph into a box below: click on the 3 dots in the top right corner of the plot, and select copy chart, then, paste it below.

| |
|:-|
| <br> |

#### Activity 3-2.  Examine the top 15 most variable ASVs and in the box below comment/speculate on source of variation for one of the ASVs. Do  you think the source of variation is change of diet, inconsistent replicates or something else?

- E.g., Variance associated with different diets would produce a plot where ASV counts for samples 1 and 2 (BD diet) might be different from samples 3 and 4 (HD diet) or sample 5 (WO diet).  
- E.g., Variance observed between samples 1 and 2 (both BD diets) might suggest difference between biological replicate 1  and 2 due to unknown factors.

| |
|:-|
| <br> |

### Activity 4 – Try it Out!

*Estimated time: 60 min*

Now it’s time to explore the full dataset with all 105 samples!  Working with your group, explore one of the  questions below or come up with another question.  When you are done, copy and paste your results into the class poster.  Here are the files that you will need for this Activity:

- [ASV counts (2185 rows by 114 columns)](https://docs.google.com/spreadsheets/d/1mDk_enQzQVQVplbLzPMYJBF5whsvZ62gOPDwkqIpJvM/edit?usp=sharing)
- [Sample metadata (106 rows by 28 columns)](https://docs.google.com/spreadsheets/d/1TFXtaantSgDnMwnUvcAllQErWcOXOUwNCwRb_vyk2f0/edit?usp=sharing)
- [Class Poster](---)

Remember, to relate sample IDs from MISO_PS_Leah_SY_FULL, to the metadata in the MISO_metadata_FULL file.

For example, the MISO study timepoints are:

- Timepoints 1 and 2: **BD** (Baseline diet) prior to normalization with homogenized diet
- Timepoints 3 and 4: **HD** (Homogenized diet): normalized to be same for all
- Timepoint 5:  **WO** (Washout diet),  which simply involves individuals going back to their baseline, regular diet 

#### Question 1 - Profile and compare ASV abundance and taxonomy for 2 diets, BD and HD. Your final analysis should result in a plot and/or a table.

- Question 1A: Compare 1 BD timepoint and 1 HD timepoint (males): n = 20
- Question 1B: Compare 1 BD timepoint  and 1 HD timepoint (females) : n = 22

Sample approach:  Compare the 5 most abundant ASVs between BD1 and HD1.  You'll have to think about:

1. How will you identify the 5 most abundant ASVs? Will you identify the top 5 in the BD group, and top 5 in the HD group? Should you sort on 1, 2, or all samples within a group? Or just average all samples within a group?)
1. How will you compare the multiple BD1 samples against the multiple HD1 samples?
- ASV counts -  plot average or boxplot of abundance for top ASVs? 
- For taxonomy - is there an overlap between 5 BD and 5 HD taxa? Should you consider a pie chart, a barplot or no plot?)

#### Question 2 - Profile and compare ASV abundance and taxonomy of 21 individuals using a single homogenized dietary timepoint. Your final analysis should result in a plot and/or a table.

- Question 2A: Examine HD1 timepoint  (males and females): n = 21
- Question 2B: Examine HD2 timepoint (males and females): n = 21

Sample approach: You can compare the 5-10 most abundant ASVs between 21 individuals for HD1.  You'll have to think about
1. How will you identify the 5 most abundant ASVs? Should you show the top 5 per each sample? Sort on 1, 2, or all samples? Or just average all samples?)
1. How will you compare the 21 samples?
- ASV counts -  plot average or boxplot of abundance for top ASVs? 
- For taxonomy - Barplot top taxa for all individuals? Which rank - Phyla, Genus, Species?) 


### Grading criteria

- Download the assignment to your local computer as a .docx, complete it, and upload the assignment to your LMS (Blackboard, Canvas, Google Classroom).
- Download the Google Sheets to your local computers as a .xlsx, complete all the steps for the assignment, and upload the .xlsx to your LMS (Blackboard, Canvas, Google Classroom).

### Footnotes

#### Resources

- [Google Doc](https://docs.google.com/document/d/12pKSIwcVXisaf6dniyoG_AGdCQh1dG1dDwZ5s1cz92c/edit?usp=sharing)
- [‘MISO_PS_Leah_SY_Sample1’](https://docs.google.com/spreadsheets/d/1hpSyjO0H8sXq6C1xM_oGMyv9vCY2qTvfYHVdqO9ZVhk/edit?usp=sharing)
- [MISO_PS_Leah_SY_WO-select](https://docs.google.com/spreadsheets/d/1vD0wbxgYuDlfKA0DF2Km-N4GHL2gRoUaEN_oCrSb2jU/edit?usp=sharing)
- [ASV counts (2185 rows by 114 columns)](https://docs.google.com/spreadsheets/d/1mDk_enQzQVQVplbLzPMYJBF5whsvZ62gOPDwkqIpJvM/edit?usp=sharing)
- [Sample metadata (106 rows by 28 columns)](https://docs.google.com/spreadsheets/d/1TFXtaantSgDnMwnUvcAllQErWcOXOUwNCwRb_vyk2f0/edit?usp=sharing)
- [Class Poster](---)

#### Contributions and affiliations

- Valeriya Gaysinskaya, Johns Hopkins University
- Gauri Paul, Clovis Community College
- Frederick Tan, Johns Hopkins University
- Sayumi York, Notre Dame of Maryland University



