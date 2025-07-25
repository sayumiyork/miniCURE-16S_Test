
## Set up billing in AnVIL

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


