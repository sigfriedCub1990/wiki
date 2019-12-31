---
description: >-
  This is a page dedicated to Arch Linux, here you can find some common problems
  that I've found along the way and their possible solutions.
---

# Arch Linux

## Install custom fonts

All fonts live inside `/usr/share/fonts`, this **fonts** are available to all users, to add new **fonts** only to the current user and avoid _sudoing_ do as follow:

* ```bash
  # In your user folder
  ~> mkdir -p /.local/share/fonts
  ```

* ```bash
  # Move the TTF files inside the newly created folder
  ~> cp *.ttf ~/.local/share/fonts
  ```

* ```bash
  # Refresh the system fonts cache with
  ~> fc-cache
  ~> fc-list | grep `font-name` # To check if the fonts is really installed
  ```

## Compile EVDI Kernel's module

If, like I do, you use a **Dock Station** from **Wavlink** or **Display Link** you may encounter some problems using this **Dock Station** with Arch Linux, since the manufacturers only support **Windows**, **MacOS** and **Ubuntu** as their main OS.

However, there's a solutions to this involving the compilation of the **EVDI** module with a patch for newer Kernels since the Github's version is a little out of date.

First, we need to clone the **EVDI** project from Github, if you haven't already, the link is [EVDI](https://github.com/DisplayLink/evdi) then we need to download [this patch to target newer Kernel versions](https://crazy.dev.frugalware.org/evdi-1.6.4-kernel-5.4.x.patch), from here I'll illustrate with _commands:_

```bash
# I'm assuming that you've already clone the repo and made `cd` into the folder so
# Also, inside this folder you must have an archive with the patch, 
# for illustration purposes let's call it `evdi-patch.patch`
~/evdi > patch -p1 < evdi-patch.patch
# Next line will copy the files inside `module` directory to the source were
# `dkms` will look for this module 
~/evdi > sudo cp -r module /usr/src/evdi-5.2.4
# Build `dkms` with this module
~/evdi > sudo dkms build evdi-5.2.4
# Finally let's install it
~/evdi > sudo dkms install evdi-5.2.4
```

#### **IMPORTANT DISCLAIMER** 

This last section is a **Work in progress** I had help from another programmer that hopefully will check this out and do some corrections.

