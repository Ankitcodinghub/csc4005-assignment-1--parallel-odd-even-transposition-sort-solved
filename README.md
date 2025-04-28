# csc4005-assignment-1--parallel-odd-even-transposition-sort-solved
**TO GET THIS SOLUTION VISIT:** [CSC4005 Assignment 1- Parallel Odd-Even Transposition Sort Solved](https://www.ankitcodinghub.com/product/csc4005-parallel-odd-even-transposition-sort-solved/)


---

📩 **If you need this solution or have special requests:** **Email:** ankitcoding@gmail.com  
📱 **WhatsApp:** +1 419 877 7882  
📄 **Get a quote instantly using this form:** [Ask Homework Questions](https://www.ankitcodinghub.com/services/ask-homework-questions/)

*We deliver fast, professional, and affordable academic help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;118009&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;2&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (2 votes)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;CSC4005 Assignment 1- Parallel Odd-Even Transposition Sort Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (2 votes)    </div>
    </div>
&nbsp;

Contents

1 Introduction 1

2 Parallel Implementation Method 1

3 Results and Analysis 4

4 Conclusion 4

Appendices 6

A Code – Sequential implementation 6

B Code – MPI implementation 8

1 Introduction

This report is aiming to implement an odd-even sort algorithm by both sequential method (normal C++ language) and MPI language.

The basic odd-even sort algorithm is: for an array with n elements, it totally needs no more than n iterations. In odd iteration, the array is sorted by number in odd position comparing with adjacent the number before it (in even position), swapped the latter one is smaller than the former one. In even iteration, just opposed, the array is sorted by number in even osition comparing with the adjacent number before it. This is what I do in sequential implementation.

The MPI (parallel implementation) described in the following: when using k processes, the origional array is splited into k parts, with each having numbers. In each iteration, for number within each sub-array (in each process), first sort them by sequential odd-even methid mentioned above. Then, there are some left-over groups of numbers which should be swapped but not. So we need to check these numbers on the boundary of each group.

Figure 1: General idea of parallel odd-even sort

2 Parallel Implementation Method

Here are several steps:

1. (In master node) Genetate a random array of given size n. In order to avoid excessive repetition of numbers, we use rand()%n to generate random numbers within range n.

2. (In master node) Since some n is not divisible by k, in order to use MPI_Scatter method to distribute the array to each process, we need to add n%k max elements to the end of array, which essentially do not influence the sorting.

3. In each process, first implement the normal odd-even sort. Here we need

5. Finally, use MPI_Gather to combine all subarrays in processes to master node. Then the sort is finished.

Fig 3 shows a flow chart of the MPI program.

Figure 2: flow chart of the MPI program In the code, the parallel implementation is sequential.cpp; the parallel implementation is mpi.cpp. The implementation pbs doc is sequential.pbs and parallel.pbs, respectively.

Here is a view of parallel.pbs:

#!/bin/bash

#PBS -l nodes=1:ppn=5,mem=1g,walltime=00:05:00

#PBS -q batch

#PBS -m abe #PBS -V

echo Name: Chen Yuan echo Student ID: 117010038 echo Assignment 1, Odd-even Sort, MPI implement.

echo;

for ((n=1;n&lt;=20;n++)) do timeout 60 mpirun -f /home/mpi_config -n $n /code/117010038/mpi 100 echo; done

3 Results and Analysis

The expirment conducts on 1 − 20 cores; array size n = 100,1000,10000,100000; both sequential and parallel version. (Sequential version do not have numti cores.) The following graph is the result of expriments.

4 Conclusion

Figure 3: result
