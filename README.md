# Jump-Game-II
Problem: Given an array of non-negative integers, you are initially positioned at the first index of the array. Each element in the array represents the maximum jump length at that position. The goal is to reach the last index in the minimum number of jumps. 

Solution: 

Runtime: 8 ms 

Memory Usage: 10.1 MB 

In this problem our goal is to make minimum jumps, or in another words, to start every jump from the position, where we will reach the biggest possible index. The biggest index we can reach in the current jump is the maximum jump length. But lets’ look one step forward and find out what is the biggest index we can reach in our next jump. Or which element we should choose to start the next jump from. To accomplish this, we need to check all the elements in the range, starting from the next to the element, we started our current jump from, and till the last element before the one, that indicates the maximum length of the current jump. We are looking for the biggest index we can reach by our next jump if we start it from one of the elements in this range. Inside the main loop, which is going through the whole array, lets’ make a nested one 

 

for (int j = i + 1; j < Curr_Max_Length; j++){ 

       int finish = j + nums[j]; 

       if (finish > (Prev + nums[Prev])){ 

             Prev = j; 

            flag = !flag;}} 

where “j” is the element in the range, which we are checking now, “i” is the element we started our current jump from, and “Curr_Max_Length” is the maximum length of the current jump.  

The possible index we can reach if we start the next jump from the element with the index “j” (indicated the variable “finish”) is counted like (j+ nums[j]), the sum of “j” and the value of the element with the index “j”. If this possible index is bigger than the index, which we will reach starting our next jump from the element with the index “Curr_Max_Length”, the index “Prev” will be replaced with this possible index. Initially Prev has the value of “Curr_Max_Length”. Also the variable with type bool “flag” will change its’ value to the opposite one to indicate that we should start the next jump from the index “Prev”. 

if ((!flag) && (i != Curr_Max_Length){ 

  i = Prev; 

  Curr_Max_Length = i + nums[i]; 

   count++; 

   flag = !flag;} 

Of cause the “flag” needs to be changed again in order to start next check in the nested loop. 

In case, the biggest index we can reach with the next jump is still the index, which will be reached from the element with the index “Curr_Max_Length”( and is the maximum length of the current jump), “i” will reach “Curr_Max_Length”. If we still didn’t reach the last index in the array, “Curr_Max_Length” will get new value. 

if ((i == Curr_Max_Length) && (i < nums.size() - 1)) { 

 Curr_Max_Length = i + nums[i]; 

                    count++;} 

In both cases and in the nested loop in order to avoid extra iterations we need to check if we will reach the last index of the array with the next jump. 

Curr_Max_Length = i + nums[i]; 

if (Curr_Max_Length >= nums.size() - 1){ 

  goto point;} 

 

In the nested loop it looks like 

if (Prev+ nums[Prev] >= nums.size() - 1){ 

 count += 1; 

  goto point;} 

“point” is the returning value of the function. 

Before we start the jumping lets’ check 2 conditions: 

1) when it is impossible to make the first jump (when the first element of the array is 0) or there is only one element in the array. 

2) when the first or the second jump will reach the end of the array 

if (Curr_Max_Length >= nums.size() - 1){ 

       goto point;} 

else if (Curr_Max_Length + nums[Curr_Max_Length] >= nums.size() - 1) { 

       count++; 

       goto point;} 

This solution runs faster than 96% of other solutions and takes less memory than 85% solutions. 

 

 

 
