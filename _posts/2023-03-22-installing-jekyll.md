---
title: How to Install Jekyll on Windows
date: 2023-03-22 9:10:00 -400
categories: [Installations]
tags: [installation, jekyll]
---

This is my rendition of the already easy-to-follow installation process. The complete installation process is [here](https://jekyllrb.com/docs/). I just removed some of the filler.<br>
<br>

1. Download and install a [Ruby+Devkit 3.2.1](<https://rubyinstaller.org/downloads/>) or higher. Use default options for installation.

2. Run the `ridk install` step on the last stage of the installation wizard.

3. Open the start menu and search "Start Command Prompt with Ruby" so that changes to the **PATH** changes go into effect. Install Jekyll and Bundler using gem
```console
C:\Users\YOUR_NAME> gem install jekyll
```
after it has completed running check it has been properly installed
```terminal
C:\Users\YOUR_NAME> jekyll -v
```
if sucessful, then run
```terminal
C:\Users\YOUR_NAME> gem install bundler
```
after it has completed running check it has been properly installed
```terminal
C:\Users\YOUR_NAME> bundler -v
```

  
You **must** restart your computer to perform terminal commands through VSCode, or any other text editor, with your updated PATH, such as running your Jekyll website on your local machine `bundle exec jekyll serve` .
