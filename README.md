Download Link: https://assignmentchef.com/product/solved-cis1300-assignment-3-whats-in-a-name
<br>
<h1>Introduction</h1>




There is an interesting data set created by the U.S. Social Security Agency that stores the most popular first names of babies born in the U.S. since the 1880’s.  You can information about it at <u>https://www.ssa.gov/OACT/babynames/index.html</u>.  We will be working with the most popular names for male and female babies in each decade from 1880 to 2010.  The information will be contained in 14 files with the following names:




1880Names.txt        1890Names.txt       1900Names.txt       1910Names.txt      1920Names.txt

1930Names.txt        1940Names.txt       1950Names.txt       1960Names.txt      1970Names.txt

1980Names.txt        1990Names.txt       2000Names.txt       2010Names.txt




<h1>File Description</h1>




Each file contains 200 lines representing the top 200 names for male and female babies.  The format of each line is as follows:




<h2><strong>1       John    89,950  Mary    91,668 </strong></h2>




<ul>

 <li><strong>[1]</strong> The first number is the rank, <em>e.</em> 1 means that these are the most popular male and female names in the decade from 1880 to 1889.</li>

 <li><strong>[John 89,950]</strong> This is followed by the male baby name and then the number of babies with that name born in the decade.</li>

 <li><strong>[Mary 91,668]</strong> The fourth item is the female baby name of rank 1, followed by the number of babies with that name.</li>

</ul>




<strong>Program 1: </strong><strong>babyQuery.c </strong>




<h1>Source Code Files</h1>




Your program will have the name babyQuery.c and you will also use the header file babies.h.   In babies.h, you will find the definitions that you will need for your program.  It has the following contents:




/*  Defines */

#define MAXLENGTH 20 #define ROWS 200




/* Struct definitions */ struct pNames {    int  year;    int  rank[ROWS];

char maleName[ROWS][MAXLENGTH];    int  maleNumber[ROWS];    char femaleName[ROWS][MAXLENGTH];    int  femaleNumber[ROWS];

};




/* Function definitions */

int removeCommas ( char * );




You may add to this header file as needed but you cannot change want is already in the file.




<h1>Functionality</h1>




The program will accomplish the following tasks:

<ul>

 <li>Read in all the information about a decade that the user requests, <em>g.</em> if the user wants information about the 1880’s then you must read in the file 1880Names.txt.

  <ul>

   <li>As part of the input process you will have to eliminate the commas that appear in the numbers in the input files, e.g. the string 89,950 has to be changed to 89950 before being sent to atoi(). This must be done in a function called removeCommas() which will take one parameter, a pointer to a character array. The function will return the number of commas removed from the string.</li>

  </ul></li>

 <li>Store this information in a structure that will be given to you in the header file h.</li>

 <li>You will then ask your user questions that will allow you to find the following types of information: o For a given <strong>rank</strong>, what is the (male, female, both) <strong>name</strong>, <em>g.</em> in the 1880’s, the female name of rank 1 is Mary.

  <ul>

   <li>The <strong>top</strong> 10 names (male and female) for the given decade.</li>

   <li>Given a name (female, male or both), find the rank for the given decade.</li>

  </ul></li>

</ul>




<h1>Question Script</h1>




The questioning of the user must follow the following script:




$ ./babyQuery

What decade do you want to look at?  [1880 to 2010]: <em>1880</em>

Would you like to see a rank, search for a name, or see the top 10? [rank, search, top]: <em>rank</em> <em>Now there are three different paths for questioning: </em>

<h2>Path 1: rank</h2>

What rank do you wish to see? [1-200]: <em>2</em>

Would you like to see the male (0), female (1), or both (2) name(s)? [0-2]: <em>2</em>

Rank 2:  Male: William (84881) and Female: Anna (38159)  <em>if response is 2</em>

Rank 2:  Male: William (84881)   <em>if response is 0</em>

Rank 2:  Female: Anna (38159)   <em>if response is 1</em>

<h2>Path 2: search</h2>

What name do you want to search for? [case sensitive]: <em>Emily</em>

Do you wish to search male (0), female (1), or both (2) name? [0-2]: <em>1</em>

In 1880, the female name Emily is ranked 91 with a count of 3368.   <em>if response is 1</em>

In 1880, the male name Emily is not ranked.  <em>if response is 0 and the name is not found </em>In 1880, the female name Emily is ranked 91 with a count of 3368 and the male name Emily is not ranked.    <em>if response is 2 – the female name will always go first even if it is not found</em> <em>Path 3: top </em>

<ul>

 <li>John             89950  Mary    91668</li>

 <li>William 84881  Anna    38159</li>

 <li>James 54056  Emma              25404</li>

 <li>George 47651  Elizabeth         25006</li>

 <li>Charles 46656  Margaret         21799</li>

 <li>Frank 30967  Minnie             21724</li>

 <li>Joseph            26292  Ida                   18283</li>

 <li>Henry 24139  Bertha             18263</li>

 <li>Robert            24074  Clara                17717</li>

 <li>Thomas 23750  Alice                17142</li>

</ul>

<em>Notice that the columns are lined up.  The number of spaces between each column is not less than 3 and not more than 8.  The number of spaces is not the point, the point is that the columns are aligned and look pleasing to the eye.</em>




After the answer has been presented to the user the following questions will be asked:




Do you want to ask another question about 1880? [Y or N]: <em>Y</em>

If the response is <em>Y</em> then return to the question “Would you like to see a rank, search for a name, or see the top 10? [rank, search, top]: ”.

If the response is <em>N</em> then ask the following:

Would you like to select another year? [Y or N]: <em>Y</em>

If the response is <em>Y </em>then return to the question “What decade do you want to look at?  [1880 to 2010]: “.

If the response is <em>N</em> then terminate the program with the message: Thank you for using babyQuery.




<h1>Error Checking</h1>




Error checking is extremely important when users are giving information to the program.  For all of the questions asked of the user, you must check that the input is exactly what was asked for. Let us examine the various responses requested from the user:

<ul>

 <li>What decade do you want to look at? [1880 to 2010]:

  <ul>

   <li>The response must be 1880, 1890, 1900, 1910, 1920, 1930, 1940, 1950, 1960, 1970, 1980, 1990, 2000, or 2010. No other numbers are acceptable.</li>

  </ul></li>

 <li>Would you like to see a rank, search for a name, or see the top 10? [rank, search, top]:

  <ul>

   <li>The user must type in rank or search or top – all lower case and all spelled correctly and in full.</li>

  </ul></li>

 <li>What rank do you wish to see? [1-200]:

  <ul>

   <li>Only numbers between 1 and 200 are acceptable.</li>

  </ul></li>

 <li>Would you like to see the male (0), female (1), or both (2) name(s)? [0-2]:

  <ul>

   <li>Only the numbers 0, 1, or 2 are acceptable.</li>

  </ul></li>

 <li>What name do you want to search for? [case sensitive]:

  <ul>

   <li>The requested string is to be treated as case sensitive (names in the files have the first letter in upper case and the rest in lower case). If they enter a name that does not follow this format, the string is to be accepted as input but the program is to do nothing to “fix” the case and thus the request will fail.</li>

  </ul></li>

 <li>Do you wish to search male (0), female (1), or both (2) name? [0-2]:

  <ul>

   <li>Only the numbers 0, 1, or 2 are acceptable.</li>

  </ul></li>

 <li>Do you want to ask another question about 1880? [Y or N]:

  <ul>

   <li>The user is to respond with a single letter, either Y or N but it is to be treated in a case insensitive manner; i.e. y and n are acceptable.</li>

  </ul></li>

 <li>Would you like to select another year? [Y or N]:

  <ul>

   <li>The user is to respond with a single letter, either Y or N but it is to be treated in a case insensitive manner; i.e. y and n are acceptable.</li>

  </ul></li>

</ul>




If the user makes an error, the program is to give an error message and then repeat the question.  The following are the error messages that are to be given:

<ul>

 <li>What decade do you want to look at? [1880 to 2010]:

  <ul>

   <li>Acceptable decades are 1880, 1890, 1900, 1910, 1920, 1930, 1940, 1950, 1960, 1970, 1980, 1990, 2000, or 2010. No other numbers are acceptable.</li>

  </ul></li>

 <li>Would you like to see a rank, search for a name, or see the top 10? [rank, search, top]:

  <ul>

   <li>Please type in rank, search, or top exactly as requested.</li>

  </ul></li>

 <li>What rank do you wish to see? [1-200]:

  <ul>

   <li>Only numbers between 1 and 200 are acceptable.</li>

  </ul></li>

 <li>Would you like to see the male (0), female (1), or both (2) name(s)? [0-2]:

  <ul>

   <li>Only the numbers 0, 1, or 2 are acceptable.</li>

  </ul></li>

 <li>What name do you want to search for? [case sensitive]:

  <ul>

   <li>No error message is needed for this question.</li>

  </ul></li>

 <li>Do you wish to search male (0), female (1), or both (2) name? [0-2]:

  <ul>

   <li>Only the numbers 0, 1, or 2 are acceptable.</li>

  </ul></li>

 <li>Do you want to ask another question about 1880? [Y or N]:

  <ul>

   <li>Only the single characters Y or N are acceptable. Would you like to select another year? [Y or N]:</li>

   <li>Only the single characters Y or N are acceptable.</li>

  </ul></li>

</ul>







<strong>CIS1300 (Fall 2019) Assignment 3 (Part 2) – What’s in a Name? </strong>




<h1>Introduction</h1>




Welcome to Part 2 of Assignment 3.  The challenge in this part of the assignment (worth 15% of the total grade) is to use 2 data sets at the same time to do some comparisons.




<strong>Program 2: </strong><strong>babiesQuery.c </strong>




<h1>Source Code Files</h1>




Your program will have the name babiesQuery.c and you will also use the header file babies.h.   In babies.h, you will find the definitions that you will need for your program.  It has the following contents:




/*  Defines */

#define MAXLENGTH 20 #define ROWS 200




/* Struct definitions */ struct pNames {    int  year;    int  rank[ROWS];

char maleName[ROWS][MAXLENGTH];    int  maleNumber[ROWS];    char femaleName[ROWS][MAXLENGTH];    int  femaleNumber[ROWS];

};




/* Function definitions */

int removeCommas ( char * );




You may add to this header file as needed but you cannot change want is already in the file.




<h1>Functionality</h1>




The program will accomplish the following tasks:

<ul>

 <li>Read in all the information about multiple decades that the user requests, <em>g.</em> if the user wants to compare the 1880’s to the 1980’s then you must read in the file</li>

</ul>

1880Names.txt and 1980Names.txt.

<ul>

 <li>You can also decide to load all of the Names files into your program before you ask the user which decades they want.</li>

</ul>

<ul>

 <li>As before you will store this information in the structure given to you in the header file h.

  <ul>

   <li>Once again you have a choice – you can create two structures, for example</li>

  </ul></li>

</ul>

struct pNames decade1; struct pNames decade2;

<ul>

 <li>Or you can store the Names data in an array of type struct pNames struct pNames decades[num] where num is from 2 to 14.</li>

</ul>




<ul>

 <li>You will then ask your user questions that will allow you to find the following types of information: o For a given <strong>rank</strong>, what is the (male, female, both) <strong>name </strong>, <em>g.</em> in the 1880’s and the 1980’s, the female name of rank 1 is Mary in 1880 and Jessica for 1980. o The <strong>top</strong> 10 names (male and female) for the given decades that are the same.

  <ul>

   <li>Given a name (female, male or both), find the rank for the given decades.</li>

  </ul></li>

</ul>




<h1>Question Script</h1>




The questioning of the user must follow the following script:




$ ./babiesQuery

What 2 decades do you want to look at?  [1880 to 2010]: <em>1880 1980</em>

Would you like to see a rank, search for a name, or see the top 10? [rank, search, top]: <em>rank</em> <em>Now there are three different paths for questioning: </em>

<em>Path 1: rank </em>

What rank do you wish to see? [1-200]: <em>2</em>

Would you like to see the male (0), female (1), or both (2) name(s)? [0-2]: <em>2</em>

Rank 2:  1880: Male: William (84881) and Female: Anna (38159)

1980: Male: Christopher (554984) and Female: Jennifer (440871)   <em>if response is 2</em>

Rank 2:  1880 Male: William (84881)

1980 Male: Christopher (554984)   <em>if response is 0</em>

Rank 2:  1880: Female: Anna (38159)

1980: Female: Jennifer (440871)    <em>if response is 1</em>   <em>Path 2: search </em>

What name do you want to search for? [case sensitive]: <em>Emily</em>

Do you wish to search male (0), female (1), or both (2) name? [0-2]: <em>1</em>

In 1880, the female name Emily is ranked 91 with a count of 3368 and

In 1980, the female name Emily is ranked 25 with a count of 131755.   <em>if response is 1</em>

In 1880, the male name Emily is not ranked and

In 1980, the male name Emily is not ranked.  <em>if response is 0 and the name is not found </em>In 1880, the female name Emily is ranked 91 with a count of 3368 and the male name Emily is not ranked

And in 1980, the female name Emily is ranked 25 with a count of 131755 and the male name

Emily is not ranked.   <em>if response is 2 – the female name will always go first even if it is not found</em> <em>Path 3: top </em>

Male names that appear in both 1880 and 1980 Top Tens: John, James, Joseph, Robert

Female names that appear in  both1880 and 1980 Top Tens: Elizabeth




After the answer has been presented to the user the following questions will be asked:




Do you want to ask another question about 1880 and 1980? [Y or N]: <em>Y</em>

If the response is <em>Y</em> then return to the question “Would you like to see a rank, search for a name, or see the top 10? [rank, search, top]: ”.

If the response is <em>N</em> then ask the following:

Would you like to select other decades? [Y or N]: <em>Y</em>

If the response is <em>Y </em>then return to the question “What 2 decades do you want to look at?  [1880 to 2010]: “.

If the response is <em>N</em> then terminate the program with the message: Thank you for using babiesQuery.




<h1>Error Checking</h1>




Error checking is extremely important when users are giving information to the program.  For all of the questions asked of the user, you must check that the input is exactly what was asked for. Let us examine the various responses requested from the user:

<ul>

 <li>What 2 decades do you want to look at? [1880 to 2010]:

  <ul>

   <li>The response must be two of 1880, 1890, 1900, 1910, 1920, 1930, 1940, 1950, 1960, 1970, 1980, 1990, 2000, or 2010, separated by at least one space. No other numbers are acceptable.  Both numbers cannot be the same.</li>

  </ul></li>

 <li>Would you like to see a rank, search for a name, or see the top 10? [rank, search, top]:

  <ul>

   <li>The user must type in rank or search or top – all lower case and all spelled correctly and in full.</li>

  </ul></li>

 <li>What rank do you wish to see? [1-200]:

  <ul>

   <li>Only numbers between 1 and 200 are acceptable.</li>

  </ul></li>

 <li>Would you like to see the male (0), female (1), or both (2) name(s)? [0-2]:

  <ul>

   <li>Only the numbers 0, 1, or 2 are acceptable.</li>

  </ul></li>

 <li>What name do you want to search for? [case sensitive]:

  <ul>

   <li>The requested string is to be treated as case sensitive (names in the files have the first letter in upper case and the rest in lower case). If they enter a name that does not follow this format, the string is to be accepted as input but the program is to do nothing to “fix” the case and thus the request will fail.</li>

  </ul></li>

 <li>Do you wish to search male (0), female (1), or both (2) name? [0-2]: o Only the numbers 0, 1, or 2 are acceptable.</li>

 <li>Do you want to ask another question about 1880 and 1980? [Y or N]:

  <ul>

   <li>The user is to respond with a single letter, either Y or N but it is to be treated in a case insensitive manner; i.e. y and n are acceptable.</li>

  </ul></li>

 <li>Would you like to select other decades? [Y or N]:

  <ul>

   <li>The user is to respond with a single letter, either Y or N but it is to be treated in a case insensitive manner; i.e. y and n are acceptable.</li>

  </ul></li>

</ul>




If the user makes an error, the program is to give an error message and then repeat the question.  The following are the error messages that are to be given:

<ul>

 <li>What 2 decades do you want to look at? [1880 to 2010]:

  <ul>

   <li>Acceptable decades are 1880, 1890, 1900, 1910, 1920, 1930, 1940, 1950, 1960, 1970, 1980, 1990, 2000, or 2010. No other numbers are acceptable.  You must enter 2 acceptable decades separated by a least one space.</li>

  </ul></li>

 <li>Would you like to see a rank, search for a name, or see the top 10? [rank, search, top]:

  <ul>

   <li>Please type in rank, search, or top exactly as requested.</li>

  </ul></li>

 <li>What rank do you wish to see? [1-200]:

  <ul>

   <li>Only numbers between 1 and 200 are acceptable.</li>

  </ul></li>

 <li>Would you like to see the male (0), female (1), or both (2) name(s)? [0-2]:

  <ul>

   <li>Only the numbers 0, 1, or 2 are acceptable.</li>

  </ul></li>

 <li>What name do you want to search for? [case sensitive]:

  <ul>

   <li>No error message is needed for this question.</li>

  </ul></li>

 <li>Do you wish to search male (0), female (1), or both (2) name? [0-2]: o Only the numbers 0, 1, or 2 are acceptable.</li>

 <li>Do you want to ask another question about 1880 and 1980? [Y or N]:

  <ul>

   <li>Only the single characters Y or N are acceptable. Would you like to select other decades? [Y or N]:</li>

   <li>Only the single characters Y or N are acceptable.</li>

  </ul></li>

</ul>


