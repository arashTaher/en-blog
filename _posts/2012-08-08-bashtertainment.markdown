---
author: arashthr
comments: true
date: 2012-08-08 01:53:07+00:00
layout: post
slug: bashtertainment
title: BashTertainment
wordpress_id: 180
categories:
- Linux
tags:
- Bash
- GNU/Linux
---




There's nothing out there that can be considered as a worthy replacement for bash. The power it gives you is so enormous that it takes year for someone to become a real proficient.

I'm not an expert in terminal at all, but still I enjoy it in some levels. These are some of the commands combinations that found much more interesting during past days, worth to give a glance :
How to select and sort mp3 musics ( or any other regular expression you desire ) in a messy directory and pipe them into totem player :


    find -iname '*.mp3' | sort -n | xargs -d 'n' totem &


How to search in specific column of a file ( like output of objdump -t ) and select qualified line :


    awk {if ($4==".data" || ($3=="F" && $4==".text") ) {print $0} } [filename]


This one can be very helpful. You hvae visited a web page saw some videos on it. now you want to watch them again. go to .mozila or .cache ( for chromium ) directoy and then enter :


    find -size +5M -exec cp {} ~/Videos ;


( For more options, like creation date filters, visit find man page )

How to pipe the output of command into vim :


    ... | vim -


Create a boot-able flash disk from a iso installation file ( Notice : use `sudo fdisk -l` to make sure you copy your iso file into correct destination )


    sudo dd if=~/Desktop/ubuntu12.04.iso of=[/dev/sdb] oflag=direct bs=1048576


Alright ! that's enough for today. maybe we continue this later :)
