# AMS325_hw2

## pi_est
#### type code -> pi_est(2^k) for k=10,11,...,20
##### This file uses a for loop to compute π using a fixed number of random points. The function takes Ntotal as input and return πest as output.
<br/> 

### HW2_Q1
#### type code -> nothing to type, just run
##### This file contains a function that takes Ntotal as input and πest as output. 
##### For (1-a), function for different number of points have been called, such as Ntotal = 2^k points with k =10,11,..,20.  
##### For (1-b), plot has been made for both the estimated value πest and the error |πest - π| versus Ntotal within the same figure. Named right side of the y-axis as |Estπ-π|, left side of the y-axis as Estπ, and x-ais as Ntotal.
<br/>

### pi_est2
#### type code -> pi_est2(2^k) for k=5,6,...,10
##### This file uses a while loop to compute π to a given relative error |πest - π|/π less than or equal to tol. The function has taken tol as the input and πest as output. 
<br/>

### HW2_Q2
#### type code -> nothing to type, just run
##### For (2-a), function for different tol, such as tol = 2^-k with k = 5, ..., 10 has been made.
##### For (2-b), tic-toc pair for different tol has ben used to time the function, and plotted the conputational cost versus tol. Labed x-axis as 'tol', y-axis as 'compuational cost, and title as 'computational cost versus tol'.
<br/>

### cirrdn
#### type code -> cirrdn(1000)
##### The for loop has been modified from task (1) to create a graphical display that plot the random points as generated. The colors has been used differently for points that are inside and outside the circle. Then, this function has been generated as a movie using VideoWriter to display the generation of 1000 random points.
<br/>
