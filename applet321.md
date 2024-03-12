# applet321 - LACTF 2024

This challenge included a file that, when opened, contained the letters ELF and a bunch of characters. From this information, I concluded it was an ELF file, and imported the file into Ghidra. This gave me a lot more information about the file, including the main function shown below.

<img width="453" alt="Screen Shot 2024-03-09 at 4 21 58 PM" src="https://github.com/renukabhu/ctf/assets/147457857/135dddee-0ff9-4c59-9682-9ba4a8527b51">



After looking at this code a little, I realized that iVar1 compares a substring of the input to “pretty,” and if the comparison is true, iVar5 is incremented by one on the next line. This information tells us that iVar5 is the count for “pretty”s in the input. Similarly, iVar4 is the count for “please”s in the input. With this knowledge in mind, I edited the variable names to make the code a bit easier to read as shown below.
<img width="631" alt="Screen Shot 2024-03-09 at 4 47 55 PM" src="https://github.com/renukabhu/ctf/assets/147457857/06f3bf45-92c7-45e2-b2f8-b018a208d6af">



The first if statement after the do while loop checks if the pleaseCount of the input is not zero, if it is, then it checks if “flag” is in the input. If it is not, then the main function returns 0. This means that flag has to be somewhere in our input. The if statement after that checks if the prettyCount and pleaseCount added together is 54 and checks if the prettyCount minus the pleaseCount is -24. This gives us the following equations:

# prettyCount + pleaseCount = 54, prettyCount - pleaseCount = -24

If we solve these equations, we get that prettyCount is 15 and pleaseCount is 39. From this information, we now know that there are 15 “pretty”s in the input and 39 “please”s along with “flag” somewhere. I created the following code:

<img width="381" alt="Screen Shot 2024-03-11 at 11 36 02 PM" src="https://github.com/renukabhu/ctf/assets/147457857/e52ceb9a-dfbd-4da5-b7a4-d57f61856db7">


This gives us the input shown below, and when inputted into the command line, the flag is given.


<img width="526" alt="Screen Shot 2024-03-11 at 11 39 43 PM" src="https://github.com/renukabhu/ctf/assets/147457857/ce0c2ceb-91c5-4551-8d18-16f57e4dc56e">
