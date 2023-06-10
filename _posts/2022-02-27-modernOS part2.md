---
title: "Modern OS part 2 : Optimal Page Replacement Algorithm"
date: 2022-02-27 2:52:50 +0600
categories: [Academics,Modern Operating System]
tags: [academic courses,os]     # TAG names should always be lowercase
author:
  name: Nazia Shehnaz Joynab
toc: false
pin: false
comments: true
---

This algorithm replaces the page that will not be referred by the CPU in future for the longest time.It is practically impossible to implement this algorithm.This is because the pages that will not be used in future for the longest time can not be predicted.However, it is the best known algorithm and gives the least number of page faults.Hence, it is used as a performance measure criterion for other algorithms.

Let’s understand this through an example. Let’s consider a page reference string (7, 0, 1, 2, 0, 3, 0, 4, 2, 3, 0, 3, 2) with 4 page frames.
Initially all the memory slots will be empty so (7, 0, 1, 2) will be allocated to the memory with 4 page-faults(Miss). As (0) is already there, there’s no page fault(Hit). Next in the string is (3), it’ll replace (7) as it’s not used for the longest period of time in the future, with one page fault. Again, 0 is already there, so no page fault. 4 will replace 1 with one page fault. And for the rest of the string, there will be no page fault as all the arriving pages are already there in the memory.

<!-- ![Optimal Page Replacement](/assets/OS/Optimal Page Replacement algo.png){: .normal } -->

Total Page Fault = total miss = 6

Now, as we understand this algorithm, we tend to realize that this algorithm can’t be implemented practically as an operating system cannot know the future page requests in advance. So, this algorithm is just an instance of what can be the optimal solution.
