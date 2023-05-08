Download Link: https://assignmentchef.com/product/solved-programming-project-most-negative-subarray-sum
<br>
The goal of this project is to implement the most negative sum subarray problem in MIPS. The most negative subarray sum takes as input an array of integers and produces as output the most negative sum of any contiguous subarray in the original array.

For example: The input can be the array {2, 5, -6, 2, 3, -1, -5, 6}. An example of a subarray is {5,-6,2} but {2,3,-5} is not a subarray. We seek to find the most negative sum of elements in any subarray of the given array. In this example, the highlighted subarray has the most negative sum, which is -7. (You can verify this for yourself by trying other subarrays; this value will be the most negative possible).

We solve this problem using divide-and-conquer. A divide-and-conquer algorithm works by recursively breaking down a problem into two or more sub-problems of the same or related type, until these become simple enough to be solved directly.

In this project, we will develop a program to take as input an array, use a divide-and-conquer (function <em>MaxNegSubArraySum</em> defined below) to calculate the most negative sum of any subarray of the array, and print the most negative sum and its starting and ending positions in the array on the console and exit.

<strong> </strong>

<strong></strong>

<ol start="2">

 <li><strong> Important Links</strong></li>

</ol>

Your project must use the provided template file. While you are free to add any further helper functions, your code must implement the following functions according to the specifications given in this document.

The grader should be able to remove any of your functions (and any non-essential helper functions it may use) from your code and use it in another person’s programming assignment without issue (i.e. do not flip the order of variables passed to functions via registers <em>$a0</em> and <em>$a1</em> or returned via <em>$v0</em> and <em>$v1 —</em> use the conventions given). Several functions are provided, along with all the text strings one needs to complete this project. These should not, in any form, be modified, unless explicitly instructed.

You should use MIPS assembly code best practices as far as register storing and stack management. See these quick guides for more info (they are excellent, so read them before asking questions):

<ul>

 <li><a href="http://logos.cs.uic.edu/366/notes/mips%20quick%20tutorial.htm">http://logos.cs.uic.edu/366/notes/mips%20quick%20tutorial.htm</a></li>

</ul>

<strong> </strong>

<strong></strong>

<ol start="3">

 <li><strong> The Algorithm</strong></li>

</ol>

<strong>Notation</strong>: if <em>arr</em> is an array, we use <em>arr[s…e]</em> to indicate the subarray that starts with element with index <em>s</em> and ends with element with index <em>e</em> (inclusive).

We will develop a procedure called  <em>MaxNegSubarraySum</em>.

<strong>The input:</strong> an array <em>arr[], </em>a starting index <em>s</em>, and an ending index <em>e</em>.

<strong>The output:</strong> the maximum negative subarray sum in <em>arr[s…e].</em>

The recursive divide-and-conquer algorithmic:

<ol>

 <li>Divide the array <em>arr[s…e]</em> in the middle into a left subarray <em>arr[s…m]</em> and a right subarray, <em>arr[m+1…e]</em>, where <em>m</em> is the middle index: <em>m=(s+e)/2. </em></li>

 <li>Recursively call the <em>MaxNegSubarraySum</em> function twice to find the most negative subarray sum for the left subarray and the right subarray.</li>

 <li>Use a different function, called <em>MaxNegCrossingSum</em> to find the maximum negative sum of any subarray of <em>arr[s…e] </em>that includes elements from both left and right subarrays.</li>

 <li>Return the most negative value among the two values computed in step 2 and the value computed in step 3.</li>

</ol>




<strong></strong>

<ol start="4">

 <li><strong> Project Structure and Function Pseudo-Code</strong></li>

</ol>

Your code must implement the following functions according to specification given below. Remember to manage your stack!

The following functions must be implemented or have been supplied:

<ul>

 <li><strong><em>main </em></strong>(Supplied)<strong>:</strong></li>

</ul>

<ol>

 <li>Saves state of all relevant registers on the stack.</li>

 <li>Reads in the numbers and size of array from data segment.</li>

 <li>Calls the <em>MaxNegSumSubArray</em> function to return the value of the maximum negative subarray sum.</li>

 <li>Calls <em>PrintSum</em> to print the value returned by <em>MaxNegSumSubArray</em> on the console.</li>

 <li>Calls <em>syscall</em> to terminate the program.</li>

</ol>




<ul>

 <li><strong><em>PrintSum </em></strong>(Supplied)<strong>:</strong></li>

</ul>

<strong><em> </em></strong>

<ul>

 <li><em>$a0</em> holds the value to be printed.</li>

 <li>This function has no return value.</li>

</ul>

It prints “MaxNeg Sub Array Sum is:” and a number on the console.




<ul>

 <li><strong><em>FindMaxNeg2 </em></strong>(To be implemented)<strong>:</strong></li>

</ul>

<ul>

 <li><em>$a1</em> holds the first number.</li>

 <li><em>$a2</em> holds the second number.</li>

 <li><em>$v0</em> contains the more negative of the two input numbers.</li>

</ul>

This function returns the most negative of two numbers.

<strong><em></em></strong>

<strong><em> </em></strong>

<ul>

 <li><strong><em>FindMaxNeg3 </em></strong>(To be implemented)<strong>:</strong></li>

</ul>

<ul>

 <li><em>$a1</em> holds the first number.</li>

 <li><em>$a2</em> holds the second number.</li>

 <li><em>$a3</em> holds the third number.</li>

 <li><em>$v0</em> contains the most negative among the 3 numbers.</li>

</ul>

This function does the following:

<ol>

 <li>Calls <em>MaxNeg</em> on the first 2 numbers and store return value.</li>

 <li>Calls <em>MaxNeg</em> on the return value in the previous step and the third number; returns the maximum negative of the result.</li>

</ol>







<ul>

 <li><strong><em>MaxNegSumBoundary </em></strong>(To be implemented)<strong>:</strong></li>

</ul>

The input is a subarray <em>arr[s…e]</em> and a direction (<em>d</em>).

<ul>

 <li>If <em>d==0</em>, it computes the maximum negative sum of any subbarray of <em>arr[s…e]</em> <u>that includes <em>arr[e]</em>.</u> Thus, it considers the most negative sum among subarrays: <em>arr[e]   arr[e-1…e]     arr[e-2…e]   …    arr[s…e]</em></li>

 <li>If <em>d==1</em>, it computes the most negative sum of any subarray of <em>arr[s…e]</em> <u>that include <em>arr[s]</em>.</u> Thus, it considers the most negative sum among subarrays:</li>

</ul>

<em>arr[s]    arr[s…s+1]     arr[s…s+2]   …    arr[s…e]</em>




<ul>

 <li><em>$a0</em> contains address to <em>arr[]</em>.</li>

 <li><em>$a1</em> contains <em>s</em></li>

 <li><em>$a2</em> contains <em>e</em></li>

 <li><em>$a3</em> is the direction (either <em>0</em> or <em>1</em>)</li>

 <li><em>$v0</em> returns the maximum negative subarray</li>

</ul>

This function does the following:

<ol>

 <li>if <em>s==e</em>, return <em>arr[s]</em>.</li>

 <li>If <em>$a3==0</em>:</li>

</ol>

Call  <em>MaxNegSumBoundary(arr,s,e-1,0)</em> and save the result in a register <em>x</em>

Return <em>MaxNeg(arr[e], arr[e]+</em> <em>x)</em>

Else:

Call  <em>MaxNegSumBoundary(arr,s+1,e,1)</em> and save the result in register <em>x</em>

Return <em>MaxNeg(arr[s], arr[s]+ x)</em>







<ul>

 <li><strong><em>MaxNegCrossingSum </em></strong>(To be implemented)<strong>:</strong></li>

</ul>

<ul>

 <li><em>$a0</em> contains arr[].</li>

 <li><em>$a1</em> contains <em>s</em>. // s is the minimum (i.e. leftmost) index of the input array.</li>

 <li><em>$a2</em> contains <em>m</em>. // <em>m</em> is the middle <em>((s+h)/2)</em> index of the input array.</li>

 <li><em>$a3</em> contains // <em>e</em> is the maximum (i.e. rightmost) index of the array.</li>

 <li><em>$v0</em> returns the maxneg sum of arrays that includes <em>arr[m]</em> and <em>arr[m+1]</em></li>

</ul>




This function does the following:

<ol>

 <li>Call <em>MaxNegSumBoundary</em> on the left subarray <em>a[s,m]</em> with direction <em>0</em>.</li>

 <li>Call <em>MaxNegSumBoundary</em> on the right subarray <em>a[m+1,e]</em> with direction <em>1</em>.</li>

 <li>Return the sum of the above two values.</li>

</ol>




<ul>

 <li><strong><em>MaxNegSubArraySum</em></strong>(To be implemented)<strong>:</strong></li>

</ul>

<ul>

 <li><em>$a0</em> contains <em>arr[]</em></li>

 <li><em>$a1</em> contains <em>s</em></li>

 <li><em>$a2</em> contains <em>e</em></li>

</ul>

This function does the following:

<ol>

 <li>If there is only one element i.e. <em>(s==e)</em> return <em>arr[s]</em></li>

 <li>Find the middle point of given array, <em>m=(s+e)/2</em></li>

 <li>Call <em>MaxNegSubArraySum(arr[], s, m)</em> to compute the maximum subarray sum of the left subarray <em>arr[s…m]</em>.</li>

 <li>Calls <em>MaxNegSubArraySum(arr[], m+1, e)</em> to compute the maximum subarray sum of the right subarray <em>arr[m+1…e]</em>.</li>

 <li>Calls <em>MaxNegCrossingSum(arr[],s,m,e)</em> to compute the maximum subarray sum that goes through the middle.</li>

 <li>Calls <em>MaxNeg3</em> to return the maximum value among the values computed in 3, 4, and 5</li>

</ol>

<strong> </strong>

<strong></strong>

<ol start="5">

 <li><strong> MIPS Program Requirements</strong></li>

</ol>

You must submit your solution by emailing a completed file ABC_XYZ_winter2017_project.s, where ABC and XYZ are the @ucsd.edu of each student, to <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="badfd9dfced2d3c8cec3faddd7dbd3d694d9d5d794">[email protected]</a>




<ol start="6">

 <li><strong>Other criteria</strong></li>

</ol>

We expect your code to be well-commented. Each instruction should be commented with a meaningful description of the operation. Ask yourself what kinds of comments would be useful if you didn’t touch this code for a year or two and have completely forgotten how to code in MIPS. For example, this comment is bad as it tells you nothing:

<em>addi $s0, $t0, -1</em>                                                                                          # <em>$s0</em> gets <em>$t0 – 1</em>

A good comment should explain the meaning behind the instruction. A better example would be:

<em>addi $s0, $t0, -1</em>                                                      # Initialize loop counter <em>$s0</em> to <em>“n-1”</em>

Each project team contributes their own unique code – no copying, cheating, or hiring help. Even if only one of the two partners is culpable, both students will be reported to Academic Affairs.


