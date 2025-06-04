---
title: Mii Migration
date: 2025-06-03 4:16:00 -1900
categories: [3ds, guides]
tags: [3ds, guide]     # TAG names should always be lowercase
description: Migrating Miis from a 3ds to Azahar
---

## Introduction

This is a guide for migrating Miis from a 3ds into Azahar, as the standard artic setup process doesn't seem to transfer them. The issue is that Azahar doesn't encrypt anything, but the 3ds does, so we need to extract the raw mii data from the 3ds before we can import it into Azahar. Thankfully this isn't very difficult thanks to GodMode9.

## Pre-Requisites

  - A modded 3ds you want the Miis from
  - Azahar setup with the Artic Setup Tool
 
## Obtaining the file

  1. Enter GodMode9, usually by holding start while booting the 3ds.
  2. Navigate to `1:/data/<id0>/extdata/00048000/f000000b/00000000/`{: .filepath} and select `00000007`(: .filepath})
  3. Mount the image with GM9 and enter it.
    - Open the `partitionA.bin`{: .filepath} file in the hexeditor, and ensure it starts with `CFOG`. If it doesn't you may have mounted the wrong file.
  4. Copy `partitionA.bin`{: .filepath} to `0:/GM9/out`{: .filepath}
  
## Placing the file
  1. Open the Azahar folder in Azahar -> file
  2. Rename the `partitionA.bin`{: .filepath} file you extracted to `CFL_DB.dat`{: .filepath}
  3. Replace the `CFL_DB.dat`{: .filepath} in `nand/data/0000000000000000/extdata/00048000/f000000b/user/`{: .filepath} with the one you extracted from the 3ds.
  4. Repeat the last 2 steps with `CFL_oldDB.dat`{: .filepath}

## More Information
That should give you your Miis in Azahar. Azahar has done away with encryption so these steps are necessary, although a gm9 script could simplify the proccess slightly. It took a bit for me to research into this to figure out exactly how to get the actual Mii data, as the files are encrypted and a bit obfuscated internally. [3DBrew](https://www.3dbrew.org) as always is a very helpful resource for this type of thing, particularly the [Mii page](https://www.3dbrew.org/wiki/Mii) page and the pages relating to it and Mii Maker. A lot of files (not just 3ds stuff) start with what's known as ["Magic"](https://en.wikipedia.org/wiki/List_of_file_signatures) to signify what the file actually contains, which is quite useful when the file you're opening is as nonspecific as these are. The file we mounted was a [DIFF](https://www.3dbrew.org/wiki/DISA_and_DIFF) file which is a bit complex but still interesting. Thankfully GodMode9 can manage mounting them just fine. 
