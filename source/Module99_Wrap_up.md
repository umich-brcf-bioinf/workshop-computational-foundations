---
title: "Wrapping up"
output:
        html_document:
            includes:
                in_header: header.html
            theme: paper
            toc: true
            toc_depth: 4
            toc_float: true
            number_sections: false
            fig_caption: true
            markdown: GFM
            code_download: false
---

<style type="text/css">

body, td {
   font-size: 18px;
}
code.r{
  font-size: 12px;
}
pre {
  font-size: 12px
}

</style>

We hope you now have more familiarity with key concepts, tools, and techniques
that will enable more efficient, reproducible, and impactful computational research.

---

## Housekeeping

- Please take our optional [post-workshop survey](https://forms.gle/JQg4tn1B4jAVxkz29){target="_blank"} (5-10 minutes) <br />

- We will email you a link to the final session recordings by next week.

- This workshop website will be available.

- The [UM Bioinformatics Core Workshop Slack channel](https://umbioinfcoreworkshops.slack.com){target="_blank"} will be available 
for 90 days.

---

### Can I continue to use the Bash/RStudio environments we used in the workshop?
- BASH Shell and RStudio workshop compute environment will be available for one week from today.
  - _Please save all your R scripts now_ so that we can "right-size" the compute environment immediately following today's workshop session.
- You can download files from the workshop environment from your terminal/command line window as below.
  (You will need to substitute your actual workshop username and type workshop password when prompted.)
  ```
  mkdir computational-foundations-workshop
  scp -r YOUR_USERNAME@bfx-workshop01.med.umich.edu:"CF*" computational-foundations-workshop
  ```
### How could I install this software on my workstation/laptop?
  - See [Advanced setup instructions](workshop_setup/setup_instructions_advanced.html){target="_blank"}
    for details on how to install programs on your own computer.

### Where can I learn more about Bash commands or RStudio functions?
- Bash cheatsheets:
  - [https://files.fosswire.com/2007/08/fwunixref.pdf](https://files.fosswire.com/2007/08/fwunixref.pdf){target="_blank"}
- [ExplainShell.com](https://explainshell.com/){target="_blank"} can elaborate the flags of specific Bash commands:
- Regular expression syntax (aka "regex") is extremely powerful but also a broad topic unto itself
  - [Regex tutorial — A quick cheatsheet by examples](https://medium.com/factory-mind/regex-tutorial-a-simple-cheatsheet-by-examples-649dc1c3f285){target="_blank"}
  - A bit like ExplainShell above, but for regex expressions:<br/>
  [https://regexr.com](https://regexr.com/){target="_blank"} 
- A nifty collection of [cheatsheets for R](https://www.rstudio.com/resources/cheatsheets/){target="_blank"} and links to download some our favorites:
  - [Base R](http://github.com/rstudio/cheatsheets/blob/main/base-r.pdf){target="_blank"}   - [Data transformation with dplyr](https://raw.githubusercontent.com/rstudio/cheatsheets/main/data-transformation.pdf){target="_blank"}
  - [Data visualization with ggplot2](https://raw.githubusercontent.com/rstudio/cheatsheets/main/data-visualization.pdf){target="_blank"}

### Can you recommend other relevant workshops or turorials?
- The [University of Michigan Bioinformatics Core](https://medresearch.umich.edu/office-research/about-office-research/biomedical-research-core-facilities/bioinformatics-core/bioinformatics-workshops-training){target="_blank"} hosts workshops through the year.
- Intro lessons and workshops in Bash / Git / R / Python : 
  - [Software Carpentry](https://software-carpentry.org/lessons/){target="_blank"}
  - [The Carpentries at the University of Michigan](https://umcarpentries.org/){target="_blank"} host several introductory workshops each year following curricula that are developed collaboratively and using the latest research into best practices for teaching computer science content. All workshops are offered for free to learners. 


## How can I learn more about computational research at University of Michigan?
- [UM CoderSpaces "office hours"](https://datascience.isr.umich.edu/events/coderspaces/){target="_blank"} and UM CoderSpaces Slack workspace. _(See "Useful Resources" section in CoderSpaces page for instructions on how to join and access the CoderSpaces Slack workspace.)_
- Upcoming [UM Advanced Research Computing workshops](https://arc.umich.edu/events/){target="_blank"}.
- Advanced Research Computing (ARC) at University of Michigan hosts a
  high-performance computing (HPC) platform called _Great Lakes_ which combines
  high-end computers, fast/resilient storage, and pre-installed software.
  GreatLakes may be a good resource for folks who need to run the more compute
  intensive steps and a substantial block of compute and storage is subsidized
  by ARC making it essentially free to many researchers.
  - About [Great Lakes HPC](https://arc.umich.edu/greatlakes/){target="_blank"}.
  - About the ARC [Research Computing Package](https://arc.umich.edu/umrcp/){target="_blank"}.
  - Videos on [getting started with Great Lakes](https://www.mivideo.it.umich.edu/channel/ARC-TS%2BTraining/181860561/){target="_blank"}. (available to UM folks)

---

## Thank you

![](images/Module00_Introduction/sponsor_logos.png)

## Thanks to/from the workshop team
| ![](images/Module00_Introduction/headshots/headshot_cgates.jpg) | ![](images/Module00_Introduction/headshots/headshot_mbradenb.jpg) | ![](images/Module00_Introduction/headshots/headshot_trsaari.jpg) | ![](images/Module00_Introduction/headshots/headshot_rcavalca.jpg) |
|:-:|:-:|:-:|:-:|
| **Chris** | **Marci** | **Travis** | **Raymond** |
| ![](images/Module00_Introduction/headshots/headshot_damki.jpg) | ![](images/Module00_Introduction/headshots/headshot_mkdohert.jpg) | ![](images/Module00_Introduction/headshots/headshot_ncarruth.jpg) |
| **Dana** | **Matt** | **Nick** |

<br/>

Thank you for participating in our workshop. We welcome your questions and
feedback now and in the future.

Bioinformatics Workshop Team

[bioinformatics-workshops@umich.edu](mailto:bioinformatics-workshops@umich.edu) <br/>
[UM BRCF Bioinformatics Core](https://medresearch.umich.edu/office-research/about-office-research/biomedical-research-core-facilities/bioinformatics-core){target="_blank"}
