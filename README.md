# Assignme_Tijil
Product Analyst Assignment

**Understanding the problem statement**
The problem refers to time-series analysis or we can refer to it as a simple regression problem where in the optimization of the total cost incurred for the load capacity for computation is to be done. The problem is dealt in a way to cater both the minimum amount incurred as well the exceeding capaciteies at all times during a day. For example, if we have the provisioned load, say 4000 and the computation capacity beig used as a=50 and b=8000 and assuming that for the bought capacity we are supposed to 1 rupee per load ad 2 rupees per load for the exceeding part, there will be a loss of 4000-a in the first case and a loss of 2*(b-4000). Therefore, our aim should be to not only look at exceeding cost but also to reduce the extra cost being paid for the minima in usage capacity. 

Since there is very less data available, it becomes hard to use any ML model to be trained to get a good accuracy. 


**Approach**
To minimize the losses incurred due to extra payment when under utilization is there and paying 2 times in case of over-utilization we need to find a loss function which should be minimised. 
Let the provisioned load be, P
        utilized load be, U
        Cost per load for provisioned load = 1
        Cost per lod for over-utilization = 2
        Case 1, when P<U, 
               Actual CASE,          cost incurred, C = P  + 2 (U-P)
               Ideal CASE,         cost incurred, c = P
       
       Case 2, 
               Actual Case,       cost incurred, C = P
               Ideal Case,        cost incurred, c = U
               
 Therefore, the extreme cost for ideal case becomes, 
            When P<U ,
                      Extreme Cost, EC =  P  + 2 (U-P)
            When P>U, 
                      Extreme Cost, EC = U
                      
 Hence, our aim is to fin the global minima between these two Extreme Costs.
 The reason behind using this particular loss function is because with this we get a better R-squared value for the best fit line then some other loss functions which can be found in the google shhet - https://docs.google.com/spreadsheets/d/1hjAL-5vt3iN7F1fWZM4VQHEHFLcY9SH-R4pXNN24pSA/edit#gid=1244042988
 
 Question 1 - What are the capacity usage patterns?
 Answer -     The capacity usage pattern shows that maximum computation cost will be incurred during evening, that is between 4 PM and 8 PM. Also there are are local maxima                 and minima in the usage pattern. Appears to be the highest demand is during the evening which shoeld be dealt with by trying to shift the overall computation 
              load to different times during the day. 
              
Question 2 - What do you infer from the missing timestamps?
Answer -     Missing timestamps could be because the provisioned load is for every secodnd in time and to monitor that changing load could be difficult. 
             Although, from the given timestamps we can find out that the local maxima and minima exists however the global maxima and minima is unlikely to change due to the              missing timestamps.

Question - 3 - How would you solve this optimization problem - wherein at some time we’re overusing the capacity, and at other times, we’re under-using. How do we cut down on                the extra costs that we end up paying either way?
Answer -       Solution 1- One of the solution is used above in the **APPROACH**. 
               Solution 2- Another approach could be using the gradient descent method to reach to a minima of provisioned load using the computation load.
               Solution 3- Using an ML model to train on the data set and minimising the loss function.
              
