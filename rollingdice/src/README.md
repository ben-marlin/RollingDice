# GuessingGame

## Objectives

With this assignment, we aim to learn how to

- input from the command line using `Scanner`
- use the conditional `if` / `else` structure
- repeat using the `while` loop structure

## Model program

I'm going to try the idea of producing a working program for you that does similar things to the assignment. For today's example, it should input an integer, then determine whether it is even or odd. As I also want to show you how to use a loop structure, we will calculate the factorial of the integer.

Open `Main` and run it. Respond to the prompt. If you'd like, try to find ways to make the program fail. There is no way the program can get to the second `else`, but I wanted to provide an example of three possibilities.

Read the comments to figure out what it does. We'll discuss this briefly at the start of class.

## Comment out this program

Highlight everything from lines 8 to 35. Under `Edit`, choose `Toggle Block Comment`. Or you could just delete it. If you go that route, I'd suggest copying it into a Google Doc first, as you may want to refer back to it.

## Create a random integer and print it

Down towards the bottom of `main`, create a random number generator - as you did in the previous assignment. Don't forget the `import` that's necessary!

Use your random number generator to create a random integer from 1 to 5, saving it in a variable like `value`. Then print it to make sure that worked. Run this enough times to make sure it can get any value from 1 to 5.

## Input a value and print a calculation

Create a scanner as done on line 8 of the example program. Use a print statement to tell the user to guess an integer from 1 to 5, then input their guess into a variable named `guess`. Print this value to make sure this worked. 

## Use `if` to determine if guess is high

Use an `if` statement to test whether `guess > value`. In the code block, print a message indicating the guess was to high. Run this several times to make sure it prints when `guess > value`.

Alternately, you could temporarily set `value = 0` to make sure `guess > value`. But if you do this, remember to change it back later!

## Use `elseif` to determine if guess is low

After the block for the `if` statement, put `else if (guess < value) {}`, then insert code to print a message about the guess being too low. Run the code enough times to make sure it works when `guess < value`.

Again, you could set `value = 10` temporarily.

## Use `else` to determine if guess is correct

In math, we have something called the trichotomy principle. It says that for two numbers like `guess` and `value`, either `guess > value` or `guess < value` or `guess == value`. So our last possibility is that they are equal.

Insert an `else {}` and code the block to print that the guess was correct. Run this repeatedly until you know for certain the code can produce all three possibilities.

## Use `while` to repeat guessing

Enclose your code in a `while` loop. You'll need `value` and `guess` to be initialized to values that are not equal. Maybe initialize `value` like it already was, and set `guess` to 10. Then your `while` condition should be `while (guess != value)`. Enclose the rest of the code in the `while` block. 

You should be able to run this, and it should exit once you guess correctly. Make sure `value` is assigned $before$ the `while` loop so it doesn't change. If you get caught, you can go to the menu that appears in the upper left of your code window and hit the stop button.

## More interesting game

Now change the code so the game goes from 1 to 10 instead of 1 to 5. Or even 1 to 100?

The best strategy for playing the game is called $bisection$. Guess the half-way point, and you'll eliminate half the possible values. Repeat.

## Comments

Write appropriate comments about how each piece of the code works.

This should be enough for today. Remember: Save it, then commit it, then go to the Canvas assignment to tell me it's ready to grade.