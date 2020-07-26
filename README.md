# Session 3 – Test Cases and code understanding – without using in-built MATH functions
# Numertic Types
## encoded_from_base10: 
In this function, we return a string encoding in the "base" for the the "number" using the "digit_map". We are creating a custom code, so that for any given number and base, we get an encoding based on digit_map.
There are a few condition that this function must satisfy:
1)	The base should be between 2 and 36. If base is less than 2 or greater than 36, then we should raise a ValueError.
2)	For invalid base, ValueError must have relevant information (must include the string base).
3)	The digit_map must have sufficient length to represent the base. The length of digit_map must be the same as that of the number specified in base (that is – it should have the same number of characters). 
4)	The digit_map must not have any repeated character, else we should throw a ValueError. 
5)	If we have repeating character, the error must be relevant (must include the string repeating).
6)	The function must return proper encoding for all base ranges between 2 to 36 (including).
7)	It must return proper encoding for all negative "numbers". The encoding for negative numbers is equal to encoding for positive number, but with - sign added.
8)	We cannot use any in-built functions in the MATH module. We have a test case to check the functions which should not be included in the program.
9)	We cannot use bin() or oct() or hex() for base 2, 8, 16 respectively. The function must work irrespective of the number or the base.

We have used the logic of finding remainder when the number is continuously divided by the base, until the number becomes 0. When the number becomes 0, we consider all the remainders we have obtained from the first division to the last and assign it from right to left (that is we create a list and keep inserting the digits at the index 0 of the list). Once the list is formed, we iterate through each element and form a string having the corresponding value of that digit from the digit_map. The same steps are followed for negative numbers, but we have a negative sign before the encoded value of that of the absolute value of the number.
## float_equality_testing: 
This function emulates the ISCLOSE method from the MATH module, but we are not using this function straight away.
        We are going to assume:
        relative tolerance value as rel_tol = 1e-12
        absolute tolerance value as abs_tol = 1e-05
The isclose method uses the following formula to compare the values: 
abs(a-b) <= max(rel_tol * max(abs(a), abs(b)), abs_tol)
So, instead of using math.isclose() we use the formula, checks whether two values are close, or not. This method returns a Boolean value : True if the values are close, otherwise False.
## manual_truncation_function: 
This function emulates python's MATH.TRUNC method. It ignores everything after the decimal point. 
 We have used div operator to get the number before the decimal point for the positive numbers and for negative numbers we add 1 to the resulting value to get result equivalent to the trunc function. For number equal to zero, the result is zero.
## manual_rounding_function:
This function emulates python's inbuild ROUND function. We cannot convert the number to string, split it based on decimal point and find whether the digit after decimal point is greater than 5. Because we cannot use the int() function to covert the string back to int and compare the numbers. So we use operations similar to truncation function to get result equivalent to round function.
