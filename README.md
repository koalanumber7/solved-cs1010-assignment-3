Download Link: https://assignmentchef.com/product/solved-cs1010-assignment-3
<br>
Question 1: ID————————

Your NUS student id has a letter at the end. This letter iscalled a check code and is a form of redundancy check usedfor detecting errors, especially when your student id ismanually entered into a software application.

Your check code is calculated by:

1. Sum up the digits in your student id. Let the sum be N.2. Divide N by 13, and take the remainder. Let the remainderbe R.3. Look up the table below:

R  | Check Code—|————0  | Y1  | X2  | W3  | U4  | R5  | N6  | M7  | L8  | J9  | H10 | E11 | A12 | B

Write a program `id.c` that reads in a positive integercontaining the digits of a student’s id from the standardinput. Print out the check code to the standard output.

You can use the `putchar` function to print a single `char`variable to the standard output.

Use array and loops to solve this problem instead ofconditional statements.  Solutions that use conditionalstatements (in any form) will receive a 0.

Sample Run———-“`<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="d1bebeb8a6a591a1b4e0e0e7">[email protected]</a>:~/as03-ooiwt$ ./id1933091Y<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="d7b8b8bea0a397a7b2e6e6e1">[email protected]</a>:~/as03-ooiwt$ ./id3364497E<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="096666607e7d49796c38383f">[email protected]</a>:~/as03-ooiwt$ ./id1111111111111Y“`

Question 2: Kendall—————————–

Suppose that we are given a set of items and we ask twodifferent parties to rank the items according to some order.We may get two different orders of the items. How do wemeasure how similar (or dissimilar) the two rankings are?

For example, consider a search engine that returns a list ofweb pages ranked by their relevance to the search query. Auser may not always agree with the ranking of the searchengine and may judge the relevance of the search resultdifferently, i.e., the user may have his or her own ranking.This measurement of similarity between the ranking by thesearch engine and the ranking by the user gives us a metricon how good the search engine result is. The more similar itis to the ranking of the user, the better the search engineis in ranking in the search results.

One way to measure the similarity of two rankings is theKendall tau distance. You will write a program `kendall` thatcalculates the normalized Kendall tau distance for thisquestion.

We will represent a ranking by the order of the items. Thefirst item is ranked 1, the second is ranked 2, and so on. Tosimplify the problem, we take one of the rankings that wewant to calculate the Kendall tau distance on, and label theitems sequentially, as the sequence 1, 2, 3, 4, 5, … n,where n is the number of items. We call this the baseranking. The other ranking will then be a permutation of thenumbers 1 to n.

For example, suppose we have three items A, B, C. The firstranking ranks the items as B, C, A. The second ranking ranksthe items C, A, B. After relabelling the first ranking as 1,2, 3, the second ranking becomes 2, 3, 1.

The Kendall tau distance counts the number of pairs of itemsin one ranking that are ranked in a different order in the otherranking. In the example above, we have three possible pairs:

Pair | Ranking 1 | Ranking 2—–|———–|———-A-B  | B then A  | A then BA-C  | C then A  | C then AB-C  | B then C  | C then B

Out of the three pairs, the pair A-B and B-C are ordereddifferently in the two rankings, so that Kendall taudistance is 2.

The normalized Kendall tau distance is the ratio of thenumber of pairs ranked in a different order to all possiblenumber of pairs.

In the example above, the normalized Kendall distance is2/3 = 0.6666.

Your program should read the following from the standardinput:

– The first positive integer, n, is the number of items(n &gt; 1).– The next n numbers is a permutation of integers between1 to n. This corresponds to the ranking of the itemsfrom 1 to n.

Your program should print the normalized Kendall taudistance between the ranking read above and the base ranking(1, 2, 3, .. n) to the standard output.

Sample Run———-“`<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="345b5b5d434074445105050c">[email protected]</a>:~/as03-skeleton$ ./kendall32 3 10.6667<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="7e111117090a3e0e1b4f4f46">[email protected]</a>:~/as03-skeleton$ ./kendall101 2 3 4 5 6 7 8 9 100.0000<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="85eaeaecf2f1c5f5e0b4b4bd">[email protected]</a>:~/as03-skeleton$ ./kendall66 5 4 3 2 11.0000“`

Question 3: Max (7 marks)————————-

Write a program max that finds the maximum value from a listof n integers L.

Instead of doing this with a loop, solve this question with_recursion_. Write a function

“`long max(const long list[], long start, long end){:}“`

that calls itself and return the maximum value among thearray elements list[start] .. list[end – 1]. It should splitthe input list into two halves (roughly), find the maximumof the left half, find the maximum of the right half, andreturn the larger of these two maximums.

In the function definition above, the keyword `const` (shortfor constant) is used to annotate that the array list ismeant to remain unchanged.

The program should read the following from the standardinputs:

– The first number is a positive integer n.– The next n numbers correspond to the list of integers L.

The program should then print to the largest value amongthe inputs to the standard output.

Note that you are not allowed to use loops of any kind inyour solution (`for`, `while`, `do-while`).

Sample Run———-

“`<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="84ebebedf3f0c4f4e1b5b5b2">[email protected]</a>:~/ex04-ooiwt$ cat input5-5 3 1 8 2<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="305f5f594744704055010106">[email protected]</a>:~/ex04-ooiwt$ ./max &lt; input8“`

Question 4: Counting Sort (11 Marks)————————————

Sorting is a fundamental computational problem: given a listof items, we want to rearrange the items in some order.

In this question, you will write your first sortingalgorithm, called counting sort. This is an extremely fastalgorithm for sorting positive integers if the range of theintegers is limited.

The idea of counting sort is that, given the list ofintegers (each guaranteed to be between 1 to k) to sort, wecount how many times 1 appear in the list, how many times 2appears in the list, etc. Finally, we print out each numberbetween 1 to k, according to how many times they appear inthe list, skipping those numbers who do not appear.

For instance, suppose we have 6 integers between 1 to 9:

5 5 3 2 8 2

We first count how many times each number appears. Then weprint the sorted list the following way: 2 appears twice, sowe print

22

The number 3 appears once, we print

3

The number 5 appears twice, we print

55

Finally, 8 appears once, we print

8

The sorted output is thus

223558

which is the numbers sorted in increasing order.

Write a program countingsort.c that reads the following inorder from the standard input:

–  n, the number of integers to sort (n &gt; 0).–  The next n numbers are the integers to be sorted, eachguaranteed to be between 0 and 10000.

Sort the integers using the algorithms above and print thefollowing:

– The number of times each number appears.  On each line,print two numbers, i and the number of times i appearsin the input, separated by a space, in increasing orderof i.  Skip any number that does not appear in the input.

– The numbers in the input, in increasing order.

Note that if you use any other algorithms to sort thenumbers, you will be penalized heavily.

Further, your code should go through every element in thearray returned by the CS1010 I/O library exactly once.You will loose 1 mark for efficiency if you go through itmore than once.

Sample Run———-“`<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="99f6f6f0eeedd9e9fca8a8a1">[email protected]</a>:~/as03-skeleton$ ./countingsort65 5 3 2 8 22 23 15 28 1223558<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="0a6565637d7e4a7a6f3b3b32">[email protected]</a>:~/as03-skeleton$ ./countingsort3256 872 112112 1256 1872 1112256872“`