Convert numbers to Ordinal words Algorithm
step1: create a function NumToOrw with pararmeters number and output
step2: inside the function create an if statement such that if the number is 0 
the result will be "zeroth"
step3: create 4 arrays such that 
array1 contains all numbers from 1 to 9 in words 
array2 contains all numbers multiple of 10  from 10 to 90 in words 
array3 contains all numbers from 1 to 9 in ordinal words 
array4 contains all numbers multiple of 10 from 10 to 90 in ordinal words
step4: create nested if statement such that if number is modulo divisible by 10 the digit is in ones place and so on
step5: create nested if statements such that if the digit is in hundreds place output the digit from array1 and 2 followed by the word hundred and 
so on for thousands, millions etc
step6: create an if statement such that if the digit is in tens places and the digit in 0nes place is zero 
output the coressponding value from array3
else if the digit in ones place is not zero and the digit at tens place is a non zero output
the coressponding value from array2 and 4
step7: return return output 
step8: take the input for parameter number from the user and call the function NumToOrw
print the entered number and the output.
