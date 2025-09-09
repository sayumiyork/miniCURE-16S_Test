


# (PART\*) Setting up on a cloud platform {-}

<!-- AnVIL --> 


# AnVIL

<!-- Set up code of OTTR Book-->



## About AnVIL

AnVIL (The Genomic Data Science **An**alysis, **V**isualization, and **I**nformatics **L**ab-space) is a platform created by the National Human Genome Research Institute (NHGRI) in collaboration with cloud computing platform providers like Google and Microsoft. Using AnVIL we you can access computing resources on the cloud through your browser without need for any fancy physical equipment. Through AnVIL you will also have access to all the software and data necessary to complete your research project. 

In this section, we will set up our accounts on AnVIL and go through the entire lifecycle of an RStudio environment from creation to deletion. You will repeat this process throughout the semester; feel free to refer back to this section if you need a refresher on how to use AnVIL.


## Sign up for an AnVIL account

![](anvil-make-account_files/figure-docx//1uwlG7uaTOnItdpd4Ll6nNQiBJKBivsvR-erupicAwJM_g3709d9ac459_0_250.png){width=100%}

#### Purpose

You will need an account on AnVIL in order to use the platform. In this section we'll go over the specifics of account creation. 

#### Learning Objectives

1. Create an account on AnVIL
1. Login to AnVIL
1. Share the email you used to sign up for AnVIL with your instructor (if applicable)

### Create an AnVIL account

Follow the written steps below or refer to the [slides](https://docs.google.com/presentation/d/1uwlG7uaTOnItdpd4Ll6nNQiBJKBivsvR-erupicAwJM/edit?usp=sharing) or video guide.


![](anvil-make-account_files/figure-docx//1uwlG7uaTOnItdpd4Ll6nNQiBJKBivsvR-erupicAwJM_g3709d9ac459_0_299.png){width=100%}

1. Open [anvil.terra.bio](https://anvil.terra.bio/) in <mark> **Google Chrome** </mark>. Google Chrome is the only officially supported web browser for AnIVL. Because of this, while you can run AnVIL in other browsers you strongly suggest using Chrome.
    a. It is a good idea to bookmark this page so that you can easily access it throughout the course.
1. Click the hamburger icon (3 lines) in the top left corner of the screen 
1. Click "Sign in"


![](anvil-make-account_files/figure-docx//1uwlG7uaTOnItdpd4Ll6nNQiBJKBivsvR-erupicAwJM_g36368ab83bf_0_2.png){width=100%}

4. Click "Sign in with Google".
5. Sign in with a <mark>**Google associated email address**</mark> such as an institutional email that uses Gmail or a personal Gmail account. You must use a Google associated email address to gain access to Google Cloud computing resources. 
6. If you are a student, share the email you used to sign up for AnVIL with your instructor following their instructions. If you are an instructor on a C-MOOR billing project, share the email you used to sign up with someone from C-MOOR. 

**Until your account is associated with a billing project you will be unable to use computational resources on AnVIL.** 


## Set up billing in AnVIL

<mark>**This section is only for instructors. Students do NOT have to set up billing**</mark>

![](anvil-billing-projects_files/figure-docx//1yyH3DZb8Et19galJhNPiUnCevrFRC1acvMG2PB52FCo_g3709d9ac459_0_250.png){width=100%}

AnVIL will charge you for computing costs; as of the writing of this guide, the cost for running RStudio with the default settings is \$0.06 per hour. RStudio will also cost \$0.01 per hour while paused and not in use. Additionally, the persistent storage the environment comes with (50GB) costs \$2.00 per month if not deleted.

To minimize costs, we ask students to delete their RStudio Environment and persistent disk at the end of every session. While you can also reduce the amount of CPUs and memory allotted per session this will also slow down your computation.

We will not go over setting up a Google billing account which you will need to setting up a billing project on AnVIL. For assistance with setting up your billing account we suggest refering to the Terra (the platform on which AnVIL runs) [guide to billing](https://support.terra.bio/hc/en-us/articles/360048632271-Terra-costs-and-billing-GCP-details) and speaking with your institution’s information technology and finance departments. 

#### Purpose

We will learn about the billing structure of AnVIL and how to attach users to billing projects. We will then cover how to create groups on AnVIL which you may find helpful in organizing billing.

#### Learning Objectives

1. Distinguish between a billing account and a billing project
1. Understand how billing projects are connected to workspaces
1. Add users to a billing project
1. Learn how to create groups that can be used to control users' access 


### What is a billing project?

![](anvil-billing-projects_files/figure-docx//1yyH3DZb8Et19galJhNPiUnCevrFRC1acvMG2PB52FCo_g37166799c0e_0_6.png){width=100%}

A billing project is used to connect a workspace - where students will be executing code - to a billing account, which is where your actual payment information is stored. As you can see in the above diagram, a billing account can have multiple billing projects, and each billing project can be used by multiple workspaces. 

We suggest each student uses their own workspace and attaching all those workspaces to a billing project for the class. Currently, AnVIL only allow you to monitor costs from billing projects, not workspaces. But having different billing projects shown above for each class can help you learn how much computational resources reach class is using.


### Adding students to a billing account

Follow the written steps below or refer to the [slides](https://docs.google.com/presentation/d/1yyH3DZb8Et19galJhNPiUnCevrFRC1acvMG2PB52FCo/edit?usp=sharing) or video guide.

![](anvil-billing-projects_files/figure-docx//1yyH3DZb8Et19galJhNPiUnCevrFRC1acvMG2PB52FCo_g37166799c0e_0_90.png){width=100%}

1. Access billing by clicking on the hamburger icon in the top left corner of the window, click on your name, and select billing. That brings you to your billing projects page.
1. On the billing project you’d like to use, click on the Members tab.
1. Click Add users. A new window will open. You are then able to add students to the billing project with the same email they used to sign up for their AnVIL account.


### Using groups to manage classes


![](anvil-billing-projects_files/figure-docx//1yyH3DZb8Et19galJhNPiUnCevrFRC1acvMG2PB52FCo_g37166799c0e_0_17.png){width=100%}

If you have a lot of students and classes, you may find it helpful to organize your students with groups. Everyone in the group is controlled by a single email address.

1. Access billing by clicking on the hamburger icon in the top left corner of the window, click on your name, and select groups. This will take you to this groups page.
1. Click Create New group. You will be prompted to give your group a unique name.
1. Click on the name of the newly created group to enter it.
1. Click add users. Add users to the group using the same email they used to sign up for AnVIL.
1. You can use the group email created for the group seen on the group management page to manage everyone in that group. For example, you can add everyone in the group to a billing project by adding this group email to the billing project.


### Preventing runaway costs

Our team at C-MOOR is still piloting our curriculum on AnVIL. As such, we don't have much information on the approximate cost per student. We hope to provide this data in the future. 

The best way to conserve costs is to <mark>make sure that students close out their session on AnVIL properly, including the deletion of the persistent disk</mark> after they are done working. AnVIL will continue to bill the billing project even if the environment is not in active use. 

For more information on how to control computing charges, please see the Terra guide: [How to cut off GCP charges](https://support.terra.bio/hc/en-us/articles/360042023952-Runaway-costs-How-to-cut-off-GCP-charges). 


## Running a module on AnVIL

![](anvil-run-module_files/figure-docx//11wb3b7i9SwrDX_WO3mWNAycd2mbY4Moy8SuT0X3XvXo_g3709d9ac459_0_250.png){width=100%}

#### Purpose

In this section we will go over how to run C-MOOR modules on AnVIL. First we will need to clone the workspace that correlates to the research project we want to do (RNA-seq or 16S). We will only need to do this step once. Then we will go over how to create an RStudio environment in that workspace to run the module and properly end a session on AnVIL to prevent runaway costs.

#### Learning Objectives

1. Clone a public workspace for the research project you want to do (RNA-seq or 16S)
1. Launch a module through the cloned workspace
1. Close out a session on AnVIL properly to prevent runaway costs

### What is a workspace?

The workspace is the heart of AnVIL. Here are some key points about workspaces:

- Every workspace comes with its own Google Bucket (our cloud storage). Your bucket will be empty.
- Every workspace has its own billing project. Students who are not yet associated with a billing project will not be able to compute on their workspace.
- We can control access levels of users and set them either as owners, writers, or readers. Students will be writers with compute access.


### Clone a workspace on AnVIL

**We only have to do this once.** 

Follow the written steps below or refer to the [slides](https://docs.google.com/presentation/d/11wb3b7i9SwrDX_WO3mWNAycd2mbY4Moy8SuT0X3XvXo/edit?usp=sharing) or video guide.

![](anvil-run-module_files/figure-docx//11wb3b7i9SwrDX_WO3mWNAycd2mbY4Moy8SuT0X3XvXo_g3709d9ac459_0_263.png){width=100%}

1. While logged into AnVIL, using the hamburger icon in the top left corner of the screen, navigate to the workspaces page
2. Select the public tab
3. Search for the desired workspace. Your instructor will tell you which workspace to look for (miniCURE-RNA-seq or miniCURE-16S-microbiome).
4. Click on the more options icon on the right side of the desired workspace and click clone

![](anvil-run-module_files/figure-docx//11wb3b7i9SwrDX_WO3mWNAycd2mbY4Moy8SuT0X3XvXo_g3709d9ac459_0_267.png){width=100%}


5. Give the cloned workspace a unique name, such as by adding your initials or last name. All workspaces must have unique names; if someone has already taken the workspace name you initially wanted, please try a different name.
6. Confirm the billing project is the one your instructor has chosen.
7. The rest of the options should be left as is. Clone the workspace. It may take a few minutes to clone.


<mark>**You only have to clone the workspace once. From now on, use your cloned workspace.**</mark> After you clone the workspace you will automatically be directed to it. For all other times, your workspaces can be found using the hamburger icon in the top left.


### Running modules on AnVIL

#### Starting a module on AnVIL


When you open the workspace, you will be on the dashboard tab by default. The dashboard contains the instructions on how to use the workspace, links to C-MOOR websites, and the startup script. Let’s try running a module.

![](anvil-run-module_files/figure-docx//11wb3b7i9SwrDX_WO3mWNAycd2mbY4Moy8SuT0X3XvXo_g3709d9ac459_0_271.png){width=100%}

1. Take note of the container image for the custom environment. We recommend copying this to a word document or notepad. Make sure there are no spaces before or after what you copy. You will need to input this URL soon.

2. Take note of the startup script. Make sure there are no spaces before or after what you copy. This script is held in the original workspace everyone cloned. It does not have to be in your own workspace for it to work. You will need to input this URL soon.

3. Click on the Environment Configuration button , the cloud with a thunderbolt.

![](anvil-run-module_files/figure-docx//11wb3b7i9SwrDX_WO3mWNAycd2mbY4Moy8SuT0X3XvXo_g3709d9ac459_0_275.png){width=100%}

4. In the RStudio section, click Settings.

5. <mark>Make sure you have the following settings matching these instructions. Under Application configuration, choose “Custom environment”. In the container image field that appears, paste the container image URL that we copied earlier from the workspace. The URL should end with Bioconductor 3.19.1. In the startup script field, paste the URL for the startup script. This URL contains the words C-MOOR Startup Script. </mark>

6. Select 4 CPUs and 15 gigabytes of memory. 

7. Confirm that the cloud compute cost is 20 cents per hour. If it is not 20 cents per hour, reselect CPUs and memory allocation in part 6. This is a known bug in AnVIL at the writing of this guide.

8. Scroll to the bottom of the window and click “Create”. 

![](anvil-run-module_files/figure-docx//11wb3b7i9SwrDX_WO3mWNAycd2mbY4Moy8SuT0X3XvXo_g3709d9ac459_0_279.png){width=100%}

It will take some time for the RStudio Environment to be created. You can keep track of the status of the environment based on the colored dot next to the RStudio icon. The dot will turn green when the environment is ready. While it is loading (blue), you cannot interact with it.

![](anvil-run-module_files/figure-docx//11wb3b7i9SwrDX_WO3mWNAycd2mbY4Moy8SuT0X3XvXo_g3709d9ac459_0_283.png){width=100%}

9. When the environment is ready, use the Open RStudio button that will pop up. You can also access RStudio through the Analyses tab. If you hold down Ctrl as you click, you can open RStudio in a new window.

![](anvil-run-module_files/figure-docx//11wb3b7i9SwrDX_WO3mWNAycd2mbY4Moy8SuT0X3XvXo_g3709d9ac459_0_287.png){width=100%}

10. Use the file explorer in RStudio to navigate to your module of choice. From the folder called cure-rnaseq, go to tutorials, and then the folder of the module you want.

![](anvil-run-module_files/figure-docx//11wb3b7i9SwrDX_WO3mWNAycd2mbY4Moy8SuT0X3XvXo_g3709d9ac459_0_291.png){width=100%}

11. In the module’s directory, open the .Rmd file by double clicking its name.

![](anvil-run-module_files/figure-docx//11wb3b7i9SwrDX_WO3mWNAycd2mbY4Moy8SuT0X3XvXo_g3709d9ac459_0_295.png){width=100%}

12. Click Run Document in the open .Rmd file

<mark>**When you are finished, make sure you close out your session properly to prevent runaway costs!**</mark>. 

### Closing out a session on AnVIL

![](anvil-run-module_files/figure-docx//11wb3b7i9SwrDX_WO3mWNAycd2mbY4Moy8SuT0X3XvXo_g3709d9ac459_0_299.png){width=100%}

1. On the right side of the screen, click the Cloud Environment button. This is the Cloud with the lighting symbol.
1. Under the RStudio section, click settings.
1. Scroll to the bottom of the new window and click delete environment.
1. Check <mark>**Delete everything, including the persistent disk or your instructor's billing account will incur costs for storage**</mark>. 
