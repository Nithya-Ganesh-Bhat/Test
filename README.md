# Session 2 – Test Cases and code understanding
# Garbage Collection and Interning
# add_something : 
In this function, an object of class Something is created. The variable of this object is assigned to class SomethingNew, the input of which is the object something itself. So this creates a circular reference. 
# clear_memory : 
Since, there is a circular reference, even though we clear the collection in this function, there is memory leak. So we have to use Garbage Collector. Imported gc and the gc.collect() function to avoid memory leak. In critical_function invoked the function clear_memory.
# compare_strings_old : 
In this we are suboptimally testing whether two strings are exactly same or not. We are using relational operator == which will increase the time and reduce the performance. 
After that we are trying to see if we have a particular character in that string or not. For this we have created a character list which is a list of all the characters in string ‘a’. And then check for a particular character in the list. 
# compare_strings_new : 
Compare_strings_old code is suboptimal. Implemented it in such a way that it takes 1/10 the current time.
Changes made : 
1)	Interning : In the old code interning was not present for the strings ‘a’ and ‘b’. Imported sys and used sys.intern for interning the strings. 
The sys.intern function is intended to be used for performance optimization. The sys.intern function maintains a table of interned strings. When we attempt to intern a string, the function looks it up in the table and if the string has not been interned yet the function saves it in the table and returns it from the interned strings table.
In this case when we intern a, and then b, since the string has been interned already, the function returns it from the interned strings table.
But, if we create the same string without using intern, we end up with two different string objects that have the same value.
By using sys.intern we ensure that you never create two string objects that have the same value—when we request the creation of a second string object with the same value as an existing string object, we receive a reference to the pre-existing string object. This way we save memory.
2)	Using is instead of relational operator == : 
Since now we have used interning, strings with same value are allocated the same memory address. And we can compare the memory addresses instead of comparing the contents of the string. String comparison becomes very efficient now.
3)	Using set instead of list :
Sets are significantly faster than list when it comes to determining if an object is present in the set. In our case we are checking if character ‘d’ is present in string a.
# sleep : 
time.sleep() suspends execution for the given number of seconds.
# char_list : 
It is a list of characters in the string. Instead of using this if we use a set for checking for the presence of a character, the processing time is significantly faster.
# collection :
Collections in Python are containers that are used to store collections of data, for example, list, dict, set, tuple etc. 
Here we have used a collection of list in the add_something() function.
# __init__ :
__init__ is a reseved method in python classes. This method is automatically called when an object is created from a class. The sole purpose of __init__ is to initialize the values of instance members for the new object. It is called as a constructor in object oriented terminology.
