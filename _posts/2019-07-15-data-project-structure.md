---
layout: post
title:  "Data project structure"
date:   2019-07-15 18:34:10 +0700
categories: [python, skills, reproducibility]
---

<br/>
Sooner or later you will come to the conclusion that you need some work structure, some logical plan of operation. Of course, each and every task is in some way unique, but there are so many things that could be standardised. Before you say something, let me explain why standardisation may be helpful for you:

- in long term, it will **speed up your work**
- you will make **less mistakes**
- your work will be **more transparent for others**
- it will be **easier to understood your work**
- and it will be definitely **easier to reproduce**

Standardisation may come in many forms, but in this post we will talk only about **project file structure**. The very first thing that you should create when you are starting the new project.

There is no simple recipe for good project structure - answer depends on your task, needs, technology or even your coworkers/team mates opinions. Nevertheless, all of the possible solutions have several similar blocks:

----------------

- [Data folder](#data_folder)
  - raw data
  - processed data
  - transformed data
- [EDA (notebooks/scripts)](#eda)
- [Models](#models)
- [Source](#source)
- [Requirements.txt](#requirements)
- [README.md](#readme)

----------------
But why this parts are important?

### **<a id="data_folder"></a>1. Data folder:**<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Data should be always provided with your code! It's necessary to store all the data needed for the future analysis. How you will reproduce results and build knowledge without it? Data is inseparable from the code/analysis! But single file is not enough - there should be strong line separating raw data and processed one.<br/>
Why? Let's ask some experts:
<br/>
<br/>
>"The spreadsheet software Microsoft Excel, when used with default settings, is known to convert gene names to dates and floating-point numbers. A programmatic scan of leading genomics journals reveals that approximately one-fifth of papers with supplementary Excel gene lists contain erroneous gene name conversions." [[1](https://genomebiology.biomedcentral.com/articles/10.1186/s13059-016-1044-7)]

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Lesson learned:** - store your data as raw files and **do not** edit it with any tool! In this case Excel change the format of data, but imagine if anyone will change some values in random cells. There is no possibility to track this change and to revert it. In this case no one will be able to reproduce your work and your conclusion may be not so good. Of course there is also another big topic - *data version control* - but it's beyond the scope of this note.
<br/>
>Some economic's superstars - C. Reinhart and K. Rogoff - made an mistake with some calculations: "Reinhart and Rogoff’s work showed average real economic growth slows (a 0.1% decline) when a country’s debt rises to more than 90% of gross domestic product (GDP) – and this 90% figure was employed repeatedly in political arguments over high-profile austerity measures. The most serious was that, in their Excel spreadsheet, Reinhart and Rogoff had not selected the entire row when averaging growth figures: they omitted data from Australia, Austria, Belgium, Canada and Denmark. When that error was corrected, the “0.1% decline” data became a 2.2% average increase in economic growth." [[2](https://theconversation.com/the-reinhart-rogoff-error-or-how-not-to-excel-at-economics-13646)]

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Lesson learned:** - make all the calculations with your code, make it reproducible and most importantly;

### **<a id="eda"></a>2. Exploratory Data Analysis (EDA):**<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; It's your favourite place! Here you will do all the dirty work! Every idea, every line of the final code, every mistake - it will all happen here. However you are allowed to challenge every idea, please remember to keep this place clean. If not, you will be lost! Pretty quickly - trust me. Here's some advices:
- keep coherent file name convention (ex. 20190617_data_munging_ver_1.ipynb) - remember that it's hard to check for differences between "*final_final_2_version.ipynb*" and "*final_final_version.ipynb*" after some days.
- read and use [**PEP-8 style guide**](https://www.python.org/dev/peps/pep-0008/); better to learn standards from the beginning. Style guide will give you guarantee of code transparency and readability. *'Future you'* and others will thank you later!
- use comments (but also be aware that **you should always update comments** when you changed code)
- test code!
- Use [version control](https://git-scm.com/)! It's hard with jupter notebooks, but try! If you are not using jupyter, there is no reasonable excuse to not use version control! Want some examples? [Link](https://git-scm.com/docs)
- try to use virtual environments - [virtualenv](https://virtualenv.pypa.io/en/latest/), [conda](https://docs.conda.io/en/latest/) (or/and [docker](https://www.docker.com/))

### **<a id="models"></a>3. Models:**<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; This is the place for all the models that you will managed to develop

### **<a id="source"></a>4. Source:**<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Production code. This version is ready for development/use. It will not get any unexpected error (hope so!).

### **<a id="requirements"></a>5. requirements.txt:**<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; This file is crucial for project reproducibility. Always use [pip](https://pip.pypa.io/en/stable/user_guide/#requirements-files) and freeze all the packages dependences used in your project. It will allow others to install all necessary package (with the correct versions!) to run your code!

### **<a id="readme"></a>6. README.md:**<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Insert here your thoughts, instructions, some helpful content.
