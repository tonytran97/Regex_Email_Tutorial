# Regex Email Tutorial For Dummies

What is a regex (regular expression)? It is a text pattern that can be used to match strings of text with certain character combinations. These regular expressions can perform functions like replacing a particular character or sequence within a string or serve the purpose of checking for validation. The purpose of this tutorial is to deconstruct the regex for email matching.

## Summary

---

The expression below is an email matching-specific regex. At first look, this expression could seem ovewhelming and difficult to understand, but we will break it down into its component parts for both you and I to better understand.

    /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

## Table of Contents

- [Anchors](#anchors)
- [Grouping and Capturing](#grouping-and-capturing)
- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes)
- [Bracket Expressions](#bracket-expressions)
- [Putting it all Together](#putting-it-all-together)

## Regex Components

There are two ways to create a regex object in Javascript. For this tutorial, we will be using literal notation, which requires the designed pattern to be wrapped within the forward slash characters (/). We will be breaking down each of the regex components in more detail in the following bullet points.

- ### Anchors

  There are two characters which are designated to be the anchors of these regex expressions. These characters are ^ and $. They serve the purpose of marking either the start or end of the regex statement respectively.

  Let us take a look at our email matching regex.

        /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

  In this example, we see the ^ anchor indicating the start of the expressiong and the $ anchor indicating the end of the statement.

  In other words, this regex is searching for a string of text that matches the following pattern.

        ([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})

- ### Grouping and Capturing

  While some regex expressions are short and straightforward, others are lengthier and considerably more complex. As these expressions become more complex, we might need to verify that these different parts of the string each meet the criteria we are looking for. In order to separate and group our subsections, we would be using parentheses ( ).

  To better understand our email regex, our expression can be divided up into three subexpressions as seen below:

        /^ ([a-z0-9_\.-]+) @ ([\da-z\.-]+) \. ([a-z\.]{2,6}) $/

        1) ([a-z0-9_\.-]+)
        2) ([\da-z\.-]+)
        3) ([a-z\.]{2,6})

  Each of these subexpressions enclosed within the parenthesis have their different searches and criteria to find their matches.

- ### Bracket Expressions

  Bracket expressions are anything that lie within the brackets [ ]. These determine what character types are allowed to be used within an expression or subexpression. In our example, we have three different sets of bracket expressions. 
      
      /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

      1) ([a-z0-9_\.-]+)
      2) ([\da-z\.-]+)
      3) ([a-z\.]{2,6})

  In the first bracket expression, we have 
  
      [a-z0-9_\.-]

  Lets further break this down...

      [ a-z 0-9 _ \. -]

  I have separated each of the components inside of the bracket expression to hopefully better explain it. In the first part, we see a range of characters 'a-z'. In the second part, we see a range of numbers from '0-9'. Followed by a '_', a '\.', and a '-'. Putting this all together, it means that our subexpression before the '@' can contain any lowercase letter between a-z, any number between 0-9, or any of the following special characters, an underscore, a period, or a hyphen. Keep in mind that regex is case sensitive, so if we wanted to include uppcase characters, we would need to add to the expression to include [A-Z]. 

  The following two subexpressions follow the same concept as the first with ranges and special characters included. 

- ### Character Classes
  Character classes in a way can be thought of as a shortcut or shortkey. They definte a set of characters that can fulfill a match. One of the character classes used in this example is the '\d' in the second subexpression. 

      ([\da-z\.-]+)

      ([ \d a-z \. - ]+)

  '\d' allow for any Arabic numeral digit and is the equivalent to the bracket expression of [0-9]. 

  Another commonly used character class is the period special character which allows for any character except the newline character (\n). 

  You might be wondering why the period within the bracket expression has a backslash in front of it. The backslash allows for a character escape that would otherwise have been interpreted literally. For instance, with the backslash, we are only allowing for the period special character. However, without it, we would be allowing for matches with any of the characters. 

- ### Quantifiers

  Quantifiers, much like quantity, specify how many instances may be present in the input of our search. There are several types of quantifiers.

  In our example, we have two different types of quantifiers. We have

        + - Which matches the pattern one or more times AND
        {} - These curly brackets are often used to set the limits on the length of our matches, in a minimum to maximum character format.

  Were you able to find all of them? They are all located after the ends of the brackets!

        - ([a-z0-9_\.-]+)
        - ([\da-z\.-]+)
        - ([a-z\.]{2,6})

  The first two subexpressions have the + quantifier which means we have to match that specific pattern inside of the bracket at least one time. In the last subexpression, we see that there are two numbers enclosed within the curly brackets ({2,6}). This means that our matches are limited to a string consisting of between two and six characters long for that one subexpression.

### Putting it all Together
To wrap up this tutorial, I will be providing some examples of emails that will either show up as matches or not. 

      /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

      thalucky5@gmail.com
      tozinho@yahoo.com
      jp3bqerx@outlook.com

These three sample emails would all show matches with our current regex expression. However, the next three following emails would not work.

      DR.Dave61@hotmail.com
      hobkinson@Gmail.com
      abc.def@mail.c

Have you figured out why these three examples would not show up as matches with our regex?

Remember that regex expressions are case sensitive and because we did not include the ranges for uppercase letters, the first two examples would not match. Why would the last email not match? That is because in our last subexpression we have the curly bracket quantifier which determines the constraints around how short or long it must be. The string following the period must be between two and six characters long. 

## Author

- Tony Tran
  - [GitHub](https://github.com/tonytran97)
