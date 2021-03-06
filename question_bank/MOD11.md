# Module 11: Text Manipulation

## Table of Contents
- [**M11001. Word Unscrambler (★★★★)**](#m11001-word-unscrambler)
- [**M11002. Word Finder Puzzle - Multiple Words: String Array (★★★)**](#m11002-word-finder-puzzle-multiple-words-string-array)
- [**M11003. Work Evaluations (★★★)**](#m11003-work-evaluations)
- [**M11004. Reverse the Words and Letters of a String (★★)**](#m11004-reverse-the-words-and-letters-of-a-string)
- [**M11005. Cipher Encoder (★★★★)**](#m11005-cipher-encoder)
- [**M11006. String Email Address Generation (★★★)**](#m11006-string-email-address-generation)
- [**M11007. Cipher Decoder (★★★)**](#m11007-cipher-decoder)

## M11001. Word Unscrambler (★★★★)
A variable named 'words_100' is a 1 x 100 string array and each element contains a word. A variable named 'scram_words_100' is also a string array generated from 'words_100' by randomly shuffling the order of words as well as the order of characters inside each word. Thus, all words in 'words_100' are also in 'scram_words_100' but their word and characters positions are different. 

'words_100' and 'scram_words_100' are given in the beginning. 'scaram_words_100' is created after changing the order of the words and scrambling the positions of each chracter in each word. 
Here is an example of a scrambled and unscrambled variables (when rng(10) is used).

The first three words 'scram_words_100' are

```matlab
>> scram_words_100(1:3)

ans = 

  1×3 string array

    "nbdoguni"    "ioitnncfe"    "iscmooetn"
 ```
 
Their original words are "bounding", "infrection", and "economist", which are located at 88, 65, and 92 in 'words_100', respectively.
The goal of this task is to make a function to  unscramble each word in 'scram_words_100'. 
Note:  We are keeping the order of the words in 'unscram_words_100' as the one in 'scram_words_100', and we are just fixing the character positions in each word.

Create a function named UnscrWord, which accepts for two inputs named  'scram_words_100' and 'words_100' and one output named 'unscram_words_100'. 

```matlab
function unscram_words_100 = UnscrWord(scram_words_100, words_100)
```

The function should unscramble each word in 'scam_words_100' using the words in 'words_100'.
The unscrambeled words are stored in 'unscram_words_100', which is a 1 x 100 string array. 
For the case of the example above, the first three words in 'unscram_words_100' should be "bounding", "infrection", and "economist".
Note that each scarambled word only has a unique unscrambled (original) word. This means that given scrambled words cannot become the more than one word in the 'words_100' string array. 


**Solution**
Please watch this:
[**https://youtu.be/mY2fjUi-DNo?t=1256**](https://youtu.be/mY2fjUi-DNo?t=1256)



## M11002. Word Finder Puzzle - Multiple Words: String Array (★★★)
In this problem, you will create a new 'Word Finder Puzzle - Multiple' script. However, this time your script must be able to solve for the locations of mutliple words with different lengths! The words you will search for are given in a string array called 'words'. The words are inserted either horizontally or vertically. The word will also not read backwards (down to up or right to left). 

```matlab
words = ["matlab", "mechanics", "circuits", "studio", "calculus", "summer", "university"];
```

Write a script that creates 'word_loc', which is a 1x7 cell array, with each element of the cell array corresponding to each of the words. Inside each element of the cell array is a matrix containing the row and column locations of where each lettter in one of the words is located in the puzzle. Each row is a different letter, and the first column contains the row number location and the second column contains the column number location.
For example, word_loc{1} produces a 6x2 matrix with the locations in the puzzle of each letter in "matlab". 
word_loc{2} is a 9 x 2 matrix and word_loc{2}(4,:) produces a 1 x 2 vector with the row and column location of the 'h' in "mechanics".
The code for priniting the words that you found is in the learner template so you can check your answer. 
Note that you can use 'strfind' function in MATLAB.

**Solution**
Please watch this:
[**https://youtu.be/WybZTRqNxsU?t=664**](https://youtu.be/WybZTRqNxsU?t=664)


## M11003. Work Evaluations (★★★)
A large company does performance reviews on their employees every 6 months. After each meeting, their performance is summarized into a single word summary: there are seven options are:

```matlab
evaluations = ["Unsatisfactory", "Marginal", "Satisfactory", "Good", "Very Good", "Excellent", "Outstanding"];
```

The cell array 'emp_evals' contains the evaluations for all employees. 
'emp_evals' is a cell variable, where each element indicates a set of evaluations of each employee received during work period. 
The 5th element in 'emp_evals' corresponds to the evaluation for Employee 5. 
The element in each cell contain a string array including evaluations. 
Since the work period of each employee is different, the size of the string array in each cell is different. 

Below is the script to generate 'emp_evals'.


```matlab
evaluations = ["Unsatisfactory" "Marginal" "Satisfactory" "Good" ...
    "Very Good" "Excellent" "Outstanding"];

num_emp = randi([50 150]); % Company will have a random number of employees between 50 and 150
                          
emp_evals = cell(1, num_emp); % Each cell contains an evaluation array corresponding employee
                             
for ii = 1:num_emp
    num_work_terms = randi([4 70]); % Employee will have between 4 and 70 work terms
                            
    idx = randi(7,1, num_work_terms); % Generate random numbers between 1 and 7
                                      % as indices for 'evaluations' (generating
                                      % what performance reviews the employee will
                                      % get). Note these numbers can repeat!
                              
    indiv_evals = evaluations(idx); % 1 X num_work_terms string arrays of evalutions
    emp_evals{ii} = indiv_evals'; % Assign the employees evaluations to
                                  % location ii in the cell. Transpose to
                                  % turn the row vector of strings into a
                                  % column vector strings
end
```

Create functions named:
(a) TermFinder, which accepts the data 'emp_evals' as an input and produces an output variable named as 'terms_all' which is the number of performance reviews (terms) each employee has had. 'terms_all' is a 1 x 'num_emp' row vector. 


```matlab
function terms_all = TermFinder(emp_evals)
```

(b) RatingChecker, which determines the total number of an inputted rating for each employee. RatingChecker accepts two inputs. The first is the data 'emp_evals' and the second is the desired rating, specified as a string. The function outputs a 1 x 'num_emp' row vector containing the number of times each employee recieved that rating. 


```matlab
function num_ratings= RatingChecker(emp_evals, rating)
```

If you want to know how many "Outstanding" evaluations are received in each empolyee, you will run 

```matlab
num_rating_outstand = RatingChecker(emp_evals, 'Outstanding');
```

(c) ExcellentEmployee, which finds the number of employees who have at least 3 evaluations of 'excellent' or 'outstanding' during all terms. The output named 'emp_nums' is a scalar variable. If no employees meet the condition, 0 is assigned to 'emp_nums'.


```matlab
function emp_nums = ExcellentEmployee(emp_evals)
```

(d) AveragePoint, which finds the average point for all employees. The average should be taken over all employees. Please note that it does not mean that you should take the average of every individual employer, and then sum those values and thendivide by the total number of employees. The point schemes are provided below:
Outstanding is worth 7 Points
Excellent is worth 6 Points
Very Good is worth 5 Points
Good is worth 4 Points
Satisfactory is worth 3 Points
Marginal is worth 2 Point
Unsatisfactory is worth 1 Points

'avg_evals' is a scalar variable. 


```matlab
function avg_evals = AveragePoint(emp_evals)
```

**Solution**
```matlab
evaluations = ["Unsatisfactory" "Marginal" "Satisfactory" "Good" ...
    "Very Good" "Excellent" "Outstanding"];

num_emp = randi([50 150]); % Company will have a random number of employees between 50 and 150
                          
emp_evals = cell(1, num_emp); % Each cell contains an evaluation array corresponding employee
                             
for ii = 1:num_emp
    num_work_terms = randi([4 70]); % Employee will have between 4 and 70 work terms
                            
    idx = randi(7,1, num_work_terms); % Generate random numbers between 1 and 7
                                      % as indices for 'evaluations' (generating
                                      % what performance reviews the employee will
                                      % get). Note these numbers can repeat!
                              
    indiv_evals = evaluations(idx); % 1 x num_work_terms string arrays of evalutions
    emp_evals{ii} = indiv_evals'; % Assign the employees evaluations to
                                  % location ii in the cell. Transpose to
                                  % turn the row vector of strings into a
                                  % column vector strings
end

% Script Testing
% (a)
num_terms_test = TermFinder(emp_evals);

% (b)
num_ratings_test  = cell(1,7);
for ii = 1:7
    num_ratings_test{ii} = RatingChecker(emp_evals, evaluations(ii));
end

% (c)
emp_nums_test = ExcellentEmployee(emp_evals);

% (d)
avg_evals_test = AveragePoint(emp_evals);

% please design four functions to test the above script. 

% (a) TermFinder, which accepts the data 'emp_evals' and outputs the 
% number of performance reviews (terms) each employee has had in the form of a 
% row vector.

function terms_all = TermFinder(emp_evals)

terms_all = zeros(1, numel(emp_evals));
for ii = 1:length(emp_evals)
    employee_data = emp_evals{ii};
    terms_all(ii) = numel(employee_data);
end

end

% (b) RatingChecker, which determines the total number of an inputted
% rating for each employee. RatingChecker accepts two inputs. The first is
% the data 'emp_evals' and the second is the desired rating, specified as a
% string. The function outputs a 1 x 'num_emp' vector containing
% the number of times each employee recieved that rating.


function num_ratings= RatingChecker(emp_evals, rating)

num_emp = length(emp_evals);
num_ratings = zeros(1,num_emp);
for ii = 1:num_emp
    employee = emp_evals{ii};
    rating_comp = (rating == employee);
    num_same = sum(rating_comp);
    num_ratings(ii) = num_same;
end

end

% (c) ExcellentEmployee, which finds the employee numbers who average at
% least 1 excellent rating every 3 evaluations. ExcellentEmployee accepts
% the rating data 'emp_evals' and outputs the employee numbers who meet the
% condition described above in a row vector. If no employees meet the
% condition, then a 1x0 double vector should be returned.

function emp_nums = ExcellentEmployee(emp_evals)

num_excellent = RatingChecker(emp_evals, "Excellent");
num_outstanding = RatingChecker(emp_evals, "Outstanding");

good_evals = num_excellent + num_outstanding;

emp_nums = sum(good_evals >= 3);

end


% (d) AveragePoint, find an average point for all employees. The point schems are prvoided below:

% Outstanding is worth 7 Points
% Excellent is worth 6 Points
% Very Good is worth 5 Points
% Good is worth 4 Points
% Satisfactory is worth 3 Points
% Marginal is worth 2 Point
% Unsatisfactory is worth 1 Points


% 'avg_evals' is a scalar variable. 


function avg_evals = AveragePoint(emp_evals)
evaluations = ["Unsatisfactory" "Marginal" "Satisfactory" "Good" ...
    "Very Good" "Excellent" "Outstanding"];
points = 1:7;

num_terms = TermFinder(emp_evals);

total_points = 0;
for ii = 1:length(evaluations)
    num_rating = RatingChecker(emp_evals, evaluations(ii));
    num_points = num_rating * points(ii);
    total_points = total_points + num_points;

end


total_sum = sum(total_points);

avg_evals = total_sum / sum(num_terms);


end
```


## M11004. Reverse the Words and Letters of a String (★★)
Create a function named 'RvsWordChar' that accepts for one input string array named 'in_str' and one output string array named 'out_str'. 

```matlab
function out_str = RvsWordChar(in_str)
```

This function is to reverse the words in 'in_str' in a reverse order AND to reverse letters (characters) in each word. 

Example 1:

```matlab
in_str = ["AEG123", "is", "the", "best"];
out_str = RvsWordChar(in_str);
```

Then, 'out_str' is 

```matlab
out_str = 

  1×4 string array

    "tseb"    "eht"    "si"    "321GEA"
```

Example 2:

```matlab
in_str = ["University", "of", "Waterloo"];
out_str = RvsWordChar(in_str)
```

Then, 'out_str' is 

```matlab
out_str = 

  1×3 string array

    "oolretaW"    "fo"    "ytisrevinU"
```

**Solution**
Please watch this:
[**https://youtu.be/WybZTRqNxsU?t=5**](https://youtu.be/WybZTRqNxsU?t=5)


## M11005. Cipher Encoder (★★★★)
You undertake a task that send a cipher to your allies. 
You are going to design a cipher encoder function called 'CphEncd' to encode the message (convert it to be unreadable!). 

```matlab
function new_str = CphEncd(str)
```

The input for this function named 'str' is a character vector that includes alphabet, symbols, and space. 
The encoding rule is that lower case letter (except for 'z'') is converted to the upper case of the next letter and the upper case letter (except for 'Z) is converted to the lower case of the next letter. 
Also, as a special case,  'z' and 'Z' becomes 'A' and 'a', respectively (because next letters are not alphabet). The other symbols or space remains the same. 

```matlab
>> CphEncd('abc')

ans =

    'BCD'

>> CphEncd('ABC')

ans =

    'bcd'

>> CphEncd('zZa')

ans =

    'AaB'

>> CphEncd('AGE 121!')

ans =

    'bhf 121!'
```

Please design the cipher encoding function called 'CphEncd'. 

**Solution**
Please watch this:
[**https://youtu.be/mY2fjUi-DNo?t=5**](https://youtu.be/mY2fjUi-DNo?t=5)


## M11006. String Email Address Generation (★★★)
There are 14 students in a class. They came from different civil engineering programs and cohorts. (This is the same data used in TUT09.)
They submitted four assignments and took a midterm and final exam. The information is stored in the following excel file. 

![M11006](https://github.com/chulminy/AE_ENVE_GEOE_121/blob/master/question_bank/M11006(1).png)

Then, the data is imported to a cell-type variable named 'class_data'. 

![M11006](https://github.com/chulminy/AE_ENVE_GEOE_121/blob/master/question_bank/M11006(2).png)

```matlab
load tut09.mat class_data
```

This script is meant to import (load) 'class_data' stored in 'tut09.mat'. 
Note that all text data is stored as character vectors, not string scalar.

Our teaching team would like to send a group email to all students in the class. We know that student email addresses have the following format: <Username>@uwaterloo.ca.
To send a group emails, we need to generate text that includes all the email addresses separated by a comma (,). 
Please write a script to generate a string scalar that includes all emails address separated by comma. 
The output string is stored in 'email_group'. 
In other words, your script is to generate the following string and assign it to 'email_group'.
  
```matlab  
>> email_group

email_group = 

    "cmyeum@uwaterloo.ca,x97gao@uwaterloo.ca,jpconnelly@uwaterloo.ca,vafierastrau@uwaterloo.ca,jpark@uwaterloo.ca,max.midwin@uwaterloo.ca,rs2ajaj@uwaterloo.ca,jsmith@uwaterloo.ca,jjohnson@uwaterloo.ca,rwilliams@uwaterloo.ca,mbrowns@uwaterloo.ca,ddavis@uwaterloo.ca,rlopez@uwaterloo.ca,jlee@uwaterloo.ca"
```

You should not manually assign the values to the output variable. There should have a programming logic. 

**Solution**

```matlab
load tut09.mat class_data
class_data(1,:) = []; % remove header

email_group = "";

n_st = size(class_data, 1);
for ii=1:n_st
   email_group = email_group + string(class_data{ii,3}) + "@uwaterloo.ca,";
end

email_group{1}(end) = [];
```

## M11007. Cipher Decoder (★★★)
In TUT11, we designed a "CphEcd" function (Please take a look at the problem of "Cipher Encoder" in TUT11). 
In this problem, you are going to design a cipher decoder function called 'CphDcd' to decode the message. 

```matlab
function org_str = CphDcd(new_str)
```

The input for this function named 'new_str' is a character vector which contains an encoded message. 
The encoding rule is exactly same as the one in TUT11 (Here is a copy of the text):
The encoding rule is that lower case letters (except for 'z' and 'Z') is converted to the upper case of the next letter and the upper case letter is converted to the lower case of the next letter. Also, as a special case,  'z' and 'Z' becomes 'A' and 'a', respectively. The other symbols or space remains the same. 
Here, 'new_str' includes the message that is encoded using the rules mentions above. 
Your CphDcd function is to decode 'new_str' to obtain the original message that was sent to us, named as 'org_str'. 
Here are some examples:

```matlab
>> new_str = CphEncd('abc'); % encode your original message of 'abc'
>> new_str

new_str =

    'BCD'

>> org_str = CphDcd('BCD'); % decode the encoded message of 'BCD'. Then, we can obtain what's the original message.
>> org_str

ans =

    'abc'
    
>> CphEncd('AGE 121!')

ans =

    'bhf 121!'
    
>> CphDcd('bhf 121!')

ans =

    'AGE 121!'    
```
Please design the cipher decoder function called CphDcd. 

**Solution**

```matlab
char_vec = 'Students in AEG 121 are amazing!';
en_char_vec = CphEncd(char_vec);
org_char_vec = CphDcd(en_char_vec);

% Hint: If your CphDcd is working correctly, 'org_char_vec' must be the same as 'char_vec'. 

% please deisgn your function called CphDcd
function org_str = CphDcd(new_str)

char_db = double(new_str);

lg_up = and(65 <= char_db, char_db <=90); % lower case 
lg_lw = and(97 <= char_db, char_db <=122); % upper case
lg_up_a = char_db == 65; % 'A'
lg_lw_a = char_db == 97; % 'a'

org_str_db = char_db;
org_str_db(lg_up) = org_str_db(lg_up) + 31;
org_str_db(lg_lw) = org_str_db(lg_lw) - 33;
org_str_db(lg_up_a) = double('z');
org_str_db(lg_lw_a) = double('Z');

org_str = char(org_str_db);

end

function new_char_vec = CphEncd(char_vec)

char_db = double(char_vec);

lg_up = and(65 <= char_db, char_db <=89); % lower case 
lg_lw = and(97 <= char_db, char_db <=121); % upper case
lg_up_z = char_db == 90; % 'Z'
lg_lw_z = char_db == 122; % 'z'

new_char_db = char_db;
new_char_db(lg_up) = new_char_db(lg_up) + 33;
new_char_db(lg_lw) = new_char_db(lg_lw) - 31;
new_char_db(lg_up_z) = double('a');
new_char_db(lg_lw_z) = double('A');

new_char_vec = char(new_char_db);

end
```
