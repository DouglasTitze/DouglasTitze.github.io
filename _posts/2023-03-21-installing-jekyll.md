---
title: How to install jekyll
date: 2023-03-21 00:46:00 -400
categories: [introduction]
tags: [installation,jekyll]
---

1. Download and install a Ruby+Devkit version from https://rubyinstaller.org/downloads/. Use default options for installation.
2. Run the 
```powershell 
ridk install
```
step on the last stage of the installation wizard. This is needed for installing gems with native extensions. You can find additional information regarding this at https://github.com/oneclick/rubyinstaller2#using-the-installer-on-a-target-system. From the options choose         
        
```powershell
MSYS2 and MINGW development tool chain.
```
3. Open a new command prompt window from the start menu, so that changes to the ```PATH``` environment variable becomes effective. Install Jekyll and Bundler using gem 
```powershell
install jekyll bundler
```
4. Check if Jekyll has been installed properly: 
```powershell
jekyll -v
```