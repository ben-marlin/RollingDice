# RollingDice

## Objectives

Today's project gets us going with a few basic things that show up *everywhere* in coding. I'll try not to turn this into a math class, but there's a little math involved. We'll learn about

- variable names
- variable types
- producing random numbers
- arithmetic operators
- operator precedence
- concatenation

## Variables

Java lets us store values for later use. You should be used to doing this from basic algebra with variables like $x$. Generally, we want to be more descriptive with our variables. If you're storing the distance to the store, you should name it something like `distanceToTheStore`. That will seem cumbersome at first, but you'll see that VSCode gives you autocomplete suggestions and remembers every variable you've declared. Also note the weird thing I do when typing - I start variable names with a lower case letter and then capitalize each word after that. This is called camel case - it's not required, but a lot of people use it.

So go over to Main and declare your first variable and print it like this

``` 
int x = 1; 

System.out.println("x is " + x);
```

Run it to make sure this works. Read any error messages and try to correct them. That should go without saying, and I won't repeat it for later uses!

First note that `int` at the start of the line. It tells Java you're using an integer. We named it `x`, which isn't very descriptive - let's fix that!

Double click the `x`. Right click to get the context menu. One of the choices should mention changing all occurrences - choose that. Now rename your variable `firstInt`. Pretty neat? When there are only 3 occurrences, it's not a big deal. When there are 300, this is a life saver!

Now notice the `= 1;` That assigns the value of 1 to x. When assigning a value, the variable getting the value goes to the left of the assignment operator. You could also have accomplished the same thing like this

``` 
int x;
x = 1; 
```

but that seems bulky. Quick note: variable names have to start with a letter and can include numerals, or _ in them. Avoid other special characters.

## Generating a random integer

If we had to assign every variable manually, the computer wouldn't be saving us much time. Let's get Java to produce a random integer from 1 to 6, as though we were rolling a die. 

It is worth noting that the numbers produced by a computer are not truly random, but pseudorandom. The difference is not important for our purposes.

To start your random number generator, we first need to tell Java to give us access to the code that handles them. Go to the part of the code after the package statement but before the class name and insert a blank line. (Put it after your comment with your name and assignment number!) On that line, put the following code.

```
import java.util.Random;
```

Putting it outside the class will allow any other classes you create in the same file to access it. As for what it is, `java.util.Random` is a pre-made library containing a lot of methods that deal with random numbers. Try Googling java.util.Random and leafing through them. (Right now, that's not helpful, but later you'll learn to read the documentation to find out how to do things.) The `import` command just connects the library to your program.

Now, create an instance of the random number generator and change your variable assignment like so.

```
Random rand = new Random();
int firstInt = rand.nextInt(1,6);
```

The first line of this creates an "object" - which is an abstraction for a chunk of code you can use over and over again - by first saying it is defined by the `Random` library, then giving it the name `rand`, and then assigning it a `new Random()`. This last part is an example of a "constructor" - more about those later!

The second line contains `rand.nextInt()` - which asks the object named `rand` to get an integer from a huge list it has available. But we didn't want just any integer, we wanted something from 1 to 6, so we used `rand.nextInt(1,6)`. If we had only said `rand.nextInt(6)`, it might have chosen a 0. VSCode should supply the words `origin` and `bound`.

Run this over and over. Do you ever get a 6? You shouldn't. That's because - and this is annoying, but at least Java is consistent in being annoying - `nextInt` will only choose numbers *less than* the bound. So... what we really want is `rand.nextInt(1,7)`.

Now that you have the idea, do the same thing for `secondInt`, but for the values 1 through 8 inclusive.

## Mixing variable types

Next, make a line to output `"integer sum is " + firstInt + secondInt`. Run it. What's wrong? Insert a comment line to explain your observation.

Create another line where we'll fix this. This time, print `"integer sum is " + (firstInt + secondInt)`. Why did that fix the problem? Insert a comment line to explain.

So far we've used integers. Java offers numbers with decimals as either `float` or `double` - but everyone just uses `double`. These are "floating point" or "double precision" numbers. Floating point means that you can get numbers like 0.56610051 and also 0.566 - and these are different numbers with a different number of digits after the decimal. Java doesn't force you to see 0.56600000. Any time the last digit is a zero, it drops it in the display - thus the position of the decimal "floats". Floats have up to 8 digits after the decimal and doubles have up to 16 digits. Actually... they're represented internally in binary, but that's beyond our scope here.

You'll create a random double like so.

```
    double firstDouble = rand.nextDouble();
```

Add a line to print it and run it. You will always get a value from 0 to 1. The probability of ever getting exactly 0 or 1 is vanishingly small. But if you would like to produce numbers from 0 to 6, you can multiply by 6 (the multiplication operator is `*`). Make this change and run it several times to make sure it's giving you what you expect. (It is very unlikely that you will get any integers here.)

Add another line for `secondDouble`, but produce it with `rand.nextDouble(6)`. Just another way to do the same thing.

Now add a line that produces the sum of these two doubles. Then add a line that produces the sum of `firstInt` and `firstDouble`. Run this several times.

## Types and operators

When you do arithmetic with Java, it will default a calculation to the type which is more accurate. Between an int and a double, it will store the result as a double. You actually saw this happen before, as adding a String and an int resulted in a String, which is how we printed. The operation `"firstInt is " + firstInt` added a String and an int, so it converted the int to a String. Adding in Strings just fastens them together - the technical word is concatenation.

This also explains why `"integer sum is " + firstInt + secondInt` resulted in something weird. It concatenated `firstInt` onto the String, then it converted `secondInt` into a String and did the same thing.

One more weirdness you should find out. Declare a double named `quotient`. Use it to store `firstInt / secondInt`. Run this several times. Is it giving you what you expect? Write a comment to explain your answer.

Now insert another line setting `quotient` to `firstDouble / secondDouble`. Run this several times. How is this different? Write a comment.

If you have time and feel motivated, experiment with dividing with parentheses in various configurations and using `(int)` and `(double)` to convert and see what different values you get.

Finally, let's look at a common error. Try changing the declaration for `quotient` to be an int. This should give you an error on one of the calculations. Which one? What's the error? What does it mean? Insert a comment.

You can fix the error by putting `(int)` in front of the division, but you'll have to put parentheses around it. What do you think `(int)` does? Why do you think the parentheses around the division are necessary? Insert a comment.

## Maximums, minimums, and sums

It is often necessary to sum or multiply several values. It is also common to need to find the minimum or maximum. Unfortunately, the function `Math.min(a,b)` only takes two values (same for `max`), so we can't solve this just by listing them all.

The following is a trick we'll expand on later.

Generate random values for `firstInt` and `secondInt` again. Then declare and generate `thirdInt` and `fourthInt` the same way as before. Run this to make sure it's working before you proceed.

Now declare integers called `min`, `max`, and `sum`. Assign `min` to be a number larger than 6 (e.g. 100), assign `max` to be a number less than 1 (e.g. -10), and assign `sum` to be 0. Then insert the following code.

```
    min = Math.min(min,firstInt);
    max = Math.min(max,firstInt);
    sum += firstInt;

    System.out.println("min = " + min);
    System.out.println("max = " + max);
    System.out.println("sum = " + sum);
```

After this executes, `min`, `max`, and `sum` should all contain the value of `firstInt`. Now insert new lines of code before the print statements that replace `firstInt` with `secondInt`. Run the code several times to make sure it's printing the right minimum, maximum, and sum.

Finally, make the additions for `thirdInt` and `fourthInt`. 

This should be enough for today. Remember: Save it, then commit it, then go to the Canvas assignment to tell me it's ready to grade.