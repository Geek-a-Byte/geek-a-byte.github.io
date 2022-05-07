---
title: "Modern OS part 3 : Not Recently Used Page Replacement Algorithm"
date: 2022-02-27 2:52:50 +0600
categories: [Academics,Modern Operating System]
tags: [academic courses,os]     # TAG names should always be lowercase
author:
  name: Nazia Shehnaz Joynab
toc: false
pin: false
comments: true
---

In most computers with virtual memory, each page is associated with two status bits.
Referenced (R) bit is set whenever a page is read or written.
Modified (M) bit is set whenever the page is written.

In this algorithm, the operating system uses (R) and (M) bits to distinguish between pages.

- When a process starts, both page bits (R) and (M) are set to 0 by OS.
- If a page has been referenced, a page fault will occur and the (R) bit is set by the OS.
- If a page is modified, then another page fault will occur and the OS will set the (M) bit.

Periodically the R bit is cleared by a clock interrupt. Only pages referenced within the current clock interval are marked with a referenced bit. When a page fault occurs and there are no empty frames, the operating system inspects all the pages and divides them into 4 categories:

- Class 0: NR, NM
- Class 1: NR,M
- Class 2: R,NM
- Class 3: R,M

Looking at it like this, it feels class 1 is not possible. How can a page be modified but not referenced? Well, this happens when a clock interrupt resets the R bit to 0. The M bit doesn’t reset by the clock interrupt.
Based on the R and M bits, all the pages are categorized into the above 4 categories. The algorithm removes a random page with the lowest numbered non-empty class. If class 0 is empty, then a random page from class 1 is replaced and so on.
