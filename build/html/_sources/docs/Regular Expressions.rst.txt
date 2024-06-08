*Regular Expressions*
=====================
A regular expression (RE) is a language for specifying text search strings. RE helps us to match or find other strings or sets of strings, using a specialized syntax held in a pattern. Regular expressions are used to search texts in UNIX as well as in MS WORD in identical way. We have various search engines using a number of RE features.

*Properties of Regular Expressions*
***********************************
Followings are some of the important properties of RE −

* American Mathematician Stephen Cole Kleene formalized the Regular Expression language.

* RE is a formula in a special language, which can be used for specifying simple classes of strings, a sequence of symbols. In other words, we can say that RE is an algebraic notation for characterizing a set of strings.

* Regular expression requires two things, one is the pattern that we wish to search and other is a corpus of text from which we need to search.

Mathematically, A Regular Expression can be defined as follows −

* **ε** is a Regular Expression, which indicates that the language is having an empty string.

* **φ** is a Regular Expression which denotes that it is an empty language.

* If **X** and **Y** are Regular Expressions, then

       * **X**, **Y**

       * **X.Y(Concatenation of XY)**

       * **X+Y (Union of X and Y)**

       * **X*, Y* (Kleen Closure of X and Y)**

are also regular expressions.

If a string is derived from above rules then that would also be a regular expression.

*Examples of Regular Expressions*
*********************************
The following table shows a few examples of Regular Expressions −


          +----------------------------+---------------------------------------------------------+
          |Regular Expressions         |Regular Set                                              |
          +============================+=========================================================+
          |(0+10*)                     |{0,1,10,100,1000,10000,...}                              |
          +----------------------------+---------------------------------------------------------+
          |(0 * 10*)                   |{1, 01, 10, 010, 0010,...}                               |
          +----------------------------+---------------------------------------------------------+
          |(0 + ε)(1 + ε)              |{ε, 0, 1, 01}                                            |
          +----------------------------+---------------------------------------------------------+
          |(a+b)*                      |It would be set of strings of a’s and b’s of any length  | 
          |                            |which also includes the null string i.e.                 |
          |                            |{ε, a, b, aa , ab , bb , ba, aaa…….}                     |
          +----------------------------+---------------------------------------------------------+
          |(a+b)*abb                   |It would be set of strings of a’s and b’s ending with    | 
          |                            |the string abb i.e.                                      |
          |                            |{abb, aabb, babb, aaabb, ababb,....}                     |
          +----------------------------+---------------------------------------------------------+
          |(11)*                       |It would be set consisting of even number of 1’s which   | 
          |                            |also includes an empty string i.e.                       |
          |                            |{ε, 11, 1111, 111111,...}                                |
          +----------------------------+---------------------------------------------------------+
          |(aa) * (bb) * b             |It would be set of strings consisting of even number of  | 
          |                            |a’s followed by odd number of b’s i.e.                   |
          |                            |{b, aab, aabbb, aabbbbb, aaaab, aaaabbb, …………..}         |
          +----------------------------+---------------------------------------------------------+
          |(aa + ab + ba + bb)*        |It would be string of a’s and b’s of even length that can| 
          |                            |be obtained by concatenating any combination of the      |
          |                            |strings aa, ab, ba and bb including null i.e.            |
          |                            |{aa, ab, ba, bb, aaab, aaba, …………..}                     |
          +----------------------------+---------------------------------------------------------+


*Regular Sets & Their Properties*
*********************************
It may be defined as the set that represents the value of the regular expression and consists specific properties.

*Properties of regular sets*
****************************
* If we do the union of two regular sets then the resulting set would also be regula.

* If we do the intersection of two regular sets then the resulting set would also be regular.

* If we do the complement of regular sets, then the resulting set would also be regular.

* If we do the difference of two regular sets, then the resulting set would also be regular.

* If we do the reversal of regular sets, then the resulting set would also be regular.

* If we take the closure of regular sets, then the resulting set would also be regular.

* If we do the concatenation of two regular sets, then the resulting set would also be regular.
