---
title: "Modern OS part 1 : Page Fault and Page Replacement"
date: 2022-02-27 2:52:50 +0600
categories: [Academics,Modern Operating System]
tags: [academic courses,os]     # TAG names should always be lowercase
author:
  name: Nazia Shehnaz Joynab
toc: false
pin: false
---

## Page fault

A page fault occurs
when a page referenced by the CPU is not found in the main memory.
The required page has to be brought from the secondary memory into the main memory.
A page that is mapped in the RAM/physical memory/main memory has to be replaced if all the frames of main memory are already occupied.

## Page Replacement

Page replacement is a process of swapping out an existing page from the frame of a main memory and replacing it with the required page. Page replacement algorithms help to decide which page must be swapped out from the main memory to create a room for the incoming page.

- page fault occurred i.e the referenced page by the CPU is not found in ram.
- Find a free page frame
- If there is a free page frame, use it (go to step no 7)
- Otherwise, Select a page to be replaced using page replacement algorithm
- Write the selected page to the disk if modified bit of that page is 1
- wanted free page frame found
- Fetch disk block into page frame
- When disk read finishes, add VM mapping for the page
- change page table entries
