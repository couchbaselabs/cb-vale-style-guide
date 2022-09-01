# Couchbase Vale Style Guide

This repository is the home of the Couchbase Style Guide, translated into Vale format! 

## Get Started 

To get started with the Vale Style guide, you need to: 

1. [Install Vale](#install-vale). 
2. [Set up a `.vale.ini` file](#set-up-a-valeini-file).

### Install Vale

To install Vale: 

1. Install a package manager: 
    - On Windows: [Chocolatey](https://chocolatey.org/install)
    - On Mac/Linux: [Homebrew](https://brew.sh/)

2. Open a terminal application with administrator permissions. 

3. Follow the instructions at [Vale.sh](https://vale.sh/docs/vale-cli/installation/) for your platform. 

The package manager does all of the heavy lifting to install Vale. If you receive a prompt to "run additional scripts" from the terminal, approve it. 

### Set up a .vale.ini file 

This repository contains a `.vale.ini` file that contains everything you need to get started. This file contains all of the necessary configuration for Vale to lint your text files.

Make a couple changes to make sure your Vale installation pulls your styles from the correct location: 

1. In your file explorer, move the `.vale.ini` from this repository to your `$HOME` directory: 
    - On Windows: `C:\Users\<yourusername>`
    - On Mac: `/Users/<yourusername>`

    On Linux, the location of the `$HOME` directory varies based on your specific Linux distribution. 

2. Open the `.vale.ini` file in a text editor. 

3. Set the `StylesPath` to the location of the `ValeStyles` folder in this repository. 
    For example, `C:\Users\<yourusername>\GitHub\cb-vale-style-guide\ValeStyles` 

## Lint a file 

After you've done all the set up, you're ready to lint some files! 

1. Open the file or folder's location on your filesystem in a terminal window. 

2. Run `vale <FileName>` or `vale <FolderName>`. 

Vale generates a report that provides the following information: 

1. If you ran Vale on a folder, the name of the file where Vale found the following list of issues.  
2. The line number and character/column number where Vale found an issue. 
3. The severity of the issue: Suggestion, Warning, or Error.
4. The description of why Vale flagged the issue. 
5. The location of the YAML file that flagged the issue, written as `<FolderName>.<FileName>`. 

![A screenshot from Windows Terminal, showing a possible output of running Vale on a file.](vale-report-example.png)

If you run into issues linting a folder:

- Check your `.vale.ini` to see what file types Vale lints. If you see a [*] above the `BasedOnStyles` setting, Vale lints all file types. Enter a file type (`.adoc`, for example) to change the scope. 
- Change the folder to limit the scope of the files you want Vale to lint.

## Tweak styles 

To tweak the existing styles, open any `.yml` file in a text editor and make your changes. 

Vale uses Go-based RegEx. If you need help to write a RegEx pattern, use a site like [regex101.com](https://regex101.com/) to learn syntax and test your patterns.

If you have a specific term like a page or product name that must be spelled the same and appear the same way everywhere, add it to the **Vocab** files: 

1. Go to `ValeStyles\Vocab\Couchbase Docs`. 
2. Do one of the following: 
    - To add a word or phrase that Vale should never flag as incorrect in any other rule, modify the `accept.txt` file. 
    - To add a word or phrase that Vale should always reject that isn't yet covered by another rule, modify the `reject.txt` file. 

Keep the following in mind: 

- Add only a single word or phrase per line to the `accept.txt` or `reject.txt`. 
- If multiple spellings for your word or phrase are correct, make sure that you add them with RegEx to the `accept.txt`. Otherwise, Vale flags any spellings or capitalization styles that don't exactly match what's present in the file. 
- If your word or phrase includes punctuation or other characters that are a part of RegEx syntax, make sure you escape them with a backslash (\\). Otherwise, Vale breaks. 