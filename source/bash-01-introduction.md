---
title: "Introducing the Shell"
output:
        html_document:
            includes:
                in_header: header.html
            theme: paper
            toc: true
            number_sections: false
            fig_caption: false
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

<!--
---
title: "Introducing the Shell"
teaching: 20
exercises: 10
questions:
- "What is a command shell and why would I use one?"
- "How can I move around on my computer?"
- "How can I see what files and directories I have?"
- "How can I specify the location of a file or directory on my computer?"
objectives:
- "Describe key reasons for learning shell."
- "Navigate your file system using the command line."
- "Access and read help files for `bash` programs and use help files to identify useful command options."
- "Demonstrate the use of tab completion, and explain its advantages."
keypoints:
- "The shell gives you the ability to work more efficiently by using keyboard commands rather than a GUI."
- "Useful commands for navigating your file system include: `ls`, `pwd`, and `cd`."
- "Most commands take options (flags) which begin with a `-`."
- "Tab completion can reduce errors from mistyping and make work more efficient in the shell."
---
-->

<script language="javascript" type="text/javascript">
function set_page_view_defaults() {
    document.getElementById('div_win').style.display = 'block';
    document.getElementById('div_unix').style.display = 'none';
};

function change_content_by_platform(form_control){
    if (!form_control || document.getElementById(form_control).value == 'win') {
        set_page_view_defaults();
    } else if (document.getElementById(form_control).value == 'unix') {
        document.getElementById('div_win').style.display = 'none';
        document.getElementById('div_unix').style.display = 'block';
    } else {
        alert("Error: Missing platform value for 'change_content_by_platform()' script!");
    }
}

window.onload = set_page_view_defaults;
</script>

## What is a shell and why should I care?

A *shell* is a computer program that presents a command line interface which allows you to control your computer using commands entered with a keyboard instead of controlling graphical user interfaces (GUIs) with a mouse/keyboard/touchscreen combination.

There are many reasons to learn about the shell:

* Many bioinformatics tools can only be used through a command line interface. Many more have features and parameter options which are not available in the GUI. BLAST is an example. Many of the advanced functions are only accessible to users who know how to use a shell.
* The shell makes your work less boring. In bioinformatics you often need to repeat tasks with a large number of files. With the shell, you can automate those repetitive tasks and leave you free to do more exciting things.
* The shell makes your work less error-prone. When humans do the same thing a hundred different times (or even ten times), they're likely to make a mistake. Your computer can do the same thing a thousand times with no mistakes.
* The shell makes your work more reproducible. When you carry out your work in the command-line (rather than a GUI), your computer keeps a record of every step that you've carried out, which you can use to re-do your work when you need to. It also gives you a way to communicate unambiguously what you've done, so that others can inspect or apply your process to new data.
* Many bioinformatic tasks require large amounts of computing power and can't realistically be run on your own machine. These tasks are best performed using remote computers or cloud computing, which can only be accessed through a shell.

In this lesson you will learn how to use the command line interface to move around in your file system.

<br>
<br>

## Accessing the remote server

To save time, we are going to be working on a remote server where all the necessary data and software are available. When we say a 'remote sever', we are talking about a computer that is not the one you are working on right now. You will create a secure connection with the workshop remote server where everything is prepared for the lesson. We will learn the basics of the shell by manipulating some data files. Some of these files are very large, and would take time to download to your computer. We will also be using several bioinformatic packages in later lessons and installing all of the software would take up time even more time. A 'ready-to-go' sever let's us focus on learning.

This section will be done slightly differently depending on if you're using a Windows or Unix computer. Here is a drop-down menu to select the appropriate instructions for connecting to the AWS instance.

**Please select the platform you wish to use for the exercises: <select id="id_platform" name="platformlist" onchange="change_content_by_platform('id_platform');return false;"><option value="unix" id="id_unix" selected> UNIX </option><option value="win" id="id_win" selected> Windows </option></select>**

<div id="div_unix" style="display:block" markdown="1">

On a Mac or Linux computer, open up a terminal where you'll proceed with some commands. On a Mac, you can search for 'Terminal' and select the application with that name.

After you're in the terminal, you can enter the command to connect to the AWS instance, substituting `<username>` with the username provided to you before the workshop, in a email with the subject line "UM BioinfCore Workshop Login":

~~~
ssh <username>@bfx-workshop01.med.umich.edu
~~~

You will need to enter the password that you were provided before the workshop, in the same email as your username.

> Note: As you type your password, nothing on the screen will change - no `*` characters will show up, etc. After you press enter, you'll receive a response.

If you haven't connected to the remote system previously, you'll see a message like the following:

~~~
The authenticity of host 'bfx-workshop01.med.umich.edu (50.17.210.255)' can't be established.
ECDSA key fingerprint is SHA256:na9lJaGIE5QFy7yDcaMVrcbkIWBfCDL3krj2Wpiie2c.
Are you sure you want to continue connecting (yes/no/[fingerprint])?
~~~

Type `yes` and press enter, and then you will proceed logging in.

</div>

<div id="div_win" style="display:block" markdown="1">

On a Windows machine, go to your start menu/search and enter the term **'cmd'**; Select the 'Command Prompt' application and it should start the shell. The shell should say something like `C:\Users\your-pc-username>`.

Then you can use the `ssh` command to connect to the AWS instance:

~~~
ssh <username>@bfx-workshop01.med.umich.edu
~~~

You will need to enter the password that you were provided before the workshop.

> Note: As you type your password, nothing on the screen will change - no `*` characters will show up, etc. After you press enter, you'll receive a response.

If you haven't connected to the remote system previously, you'll get a prompt asking if you're sure you want to connect to this new system. Type `yes` and press enter, and then you will proceed logging in.

Your shell should look similar to the following (note I've highlighted the portions that we've typed):

![Windows Command Prompt](images/bash_01_windows_cmd.png)

</div>

After logging in, you will see a screen showing something like this:

~~~
------------------------------------
Welcome to Computational Foundations
------------------------------------
Last login: Tue Feb 1 07:56:36 2022 from 68.40.57.123
<username>@ip-172-31-28-61:~$
~~~

This shows our login message "Welcome to Computational Foundations", some information about our last login, and our prompt. We should take a moment to become familiar with the appearance of our remote shell.

<br>
<br>

## Navigating your file system

The part of the operating system that manages files and directories is called the **file system**. It organizes our data into files, which hold information, and directories (also called "folders"), which hold files or other directories.

Several commands are frequently used to create, inspect, rename, and delete files and directories.

<br>
<br>

~~~
$
~~~

The dollar sign is a **prompt**, which shows us that the shell is waiting for input; your shell may use a different character as a prompt and may add information before the prompt. When typing commands, either from these lessons or from other sources, do not type the prompt, only the commands that follow it.

<br>

<details>
<summary>Preparation Magic - Customizing the prompt</summary>
You may have a prompt (the characters to the left of the cursor) that looks different from the `$` sign character used here. If you would like to change your prompt to match the example prompt, first type the command: `echo $PS1` into your shell, followed by pressing the <kbd>Enter</kbd> key.

This will print the bash special characters that are currently defining your prompt. To change the prompt to a `$` (followed by a space), enter the command: `PS1='$ '` Your window should look like our example in this lesson.

To change back to your original prompt, type in the output of the previous command `echo $PS1` (this will be different depending on the original configuration) between the quotes in the following command: `PS1=""`

For example, if the output of `echo $PS1` was `\u@\h:\w $ `, then type those characters between the quotes in the above command: `PS1="\u@\h:\w $ "`. Alternatively, you can reset your original prompt by exiting the shell and opening a new session.

This isn't necessary to follow along (in fact, your prompt may have other helpful information you want to know about).  This is up to you!

</details>

<br>

Let's find out where we are by running a command called `pwd` (which stands for "print working directory"). At any moment, our **current working directory** is our current default directory, i.e., the directory that the computer assumes we want to run commands in, unless we explicitly specify something else. Here, the computer's response is `/home/workshop/<username>`, which is the top level of your home directory on the remote system:

~~~
$ pwd
~~~

~~~
/home/workshop/<username>
~~~

Let's look at how our file system is organized. We can see what files and subdirectories are in this directory by running `ls`, which stands for "listing":

~~~
$ ls
~~~

~~~
CF_R  CF_Shell  miniconda3
~~~

`ls` prints the names of the files and directories in the current directory in alphabetical order, arranged neatly into columns. We'll be working within the `CF_Shell` subdirectory, and creating new subdirectories, throughout this workshop.

The command to change locations in our file system is `cd`, followed by a directory name to change our working directory. `cd` stands for "change directory".

Let's say we want to navigate to the `CF_Shell` directory we saw above.  We can use the following command to get there:

~~~
$ cd CF_Shell
~~~

Let's look at what is in this directory:

~~~
$ ls
~~~

~~~
sra_metadata  untrimmed_fastq
~~~

We can make the `ls` output more comprehensible by using the **flag** `-F`, which tells `ls` to add a trailing `/` to the names of directories:

~~~
$ ls -F
~~~

~~~
sra_metadata/  untrimmed_fastq/
~~~

Anything with a "/" after it is a directory. Things with a "*" after them are programs. If there are no decorations, it's a file.

`ls` has lots of other options. To find out what they are, we can type:

~~~
$ man ls
~~~

`man` (short for manual) displays detailed documentation (also referred as man page or man file) for `bash` commands. It is a powerful resource to explore `bash` commands, understand their usage and flags. Some manual files are very long. You can scroll through the file using your keyboard's down arrow or use the <kbd>Space</kbd> key to go forward one page and the <kbd>b</kbd> key to go backwards one page. When you are done reading, hit <kbd>q</kbd> to quit.

<br>
<br>

## Challenge - Inspecting the filesystem with `ls`
Use the `-l` option for the `ls` command to display more information for each item in the directory. What is one piece of additional information this long format gives you that you don't see with the bare `ls` command?

<details>
<summary>Solution - Inspecting the filesystem with `ls`</summary>
~~~
$ ls -l
~~~

~~~
total 8
drwxr-x--- 2 dcuser dcuser 4096 Jul 30  2015 sra_metadata
drwxr-xr-x 2 dcuser dcuser 4096 Nov 15  2017 untrimmed_fastq
~~~

The additional information given includes the name of the owner of the file, when the file was last modified, and whether the current user has permission to read and write to the file.

</details>

<br>
<br>

No one can possibly learn all of these arguments, that's what the manual page is for. You can (and should) refer to the manual page or other help files as needed.

Let's go into the `untrimmed_fastq` directory and see what is in there.

~~~
$ cd untrimmed_fastq
$ ls -F
~~~

~~~
sample_01.fastq  sample_02.fastq
~~~

This directory contains two files with `.fastq` extensions. FASTQ is a format for storing information about sequencing reads and their quality. We will be learning more about FASTQ files in a later lesson.

<br>
<br>

### Shortcut: Tab Completion

Typing out file or directory names can waste a lot of time and it's easy to make typing mistakes. Instead we can use tab complete as a shortcut. When you start typing out the name of a directory or file, then hit the <kbd>Tab</kbd> key, the shell will try to fill in the rest of the directory or file name.

Return to your home directory:

~~~
$ cd
~~~

then enter:

~~~
$ cd CF_S<tab>
~~~

The shell will fill in the rest of the directory name for `CF_Shell`.

Now change directories to `untrimmed_fastq` in `CF_Shell`

~~~
$ cd CF_Shell
$ cd untrimmed_fastq
~~~

Using tab complete can be very helpful. However, it will only autocomplete a file or directory name if you've typed enough characters to provide a unique identifier for the file or directory you are trying to access.

For example, if we now try to list the files which names start with `sa` by using tab complete:

~~~
$ ls sa<tab>
~~~

The shell auto-completes your command to `sample_`, because all file names in the directory begin with this prefix. When you hit <kbd>Tab</kbd> again, the shell will list the possible choices.

~~~
$ ls sample_<tab><tab>
~~~

~~~
sample_01.fastq  sample_02.fastq
~~~

Tab completion can also fill in the names of programs, which can be useful if you remember the beginning of a program name.

~~~
$ pw<tab><tab>
~~~

~~~
pwck      pwconv    pwd       pwdx      pwunconv
~~~

Displays the name of every program that starts with `pw`.

<br>
<br>

## Summary

We now know how to move around our file system using the command line. This provides certain advantage over interacting with the file system through a GUI. It allows us to work on a remote server, carry out the same set of operations on a large number of files quickly, and opens up many opportunities for using command line software packages, e.g. for bioinformatics analyses.

In the next few episodes, we'll be expanding on these skills and seeing how using the command line shell enables us to make our workflow more efficient and reproducible.

<br/>
<br/>
<hr/>
| [Back to Intro](Module00_Introduction.html) | [Top of this lesson](#top) | [Next lesson](bash-02-the-filesystem.html) |
| :--- | :----: | ---: |
