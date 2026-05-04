# Studio 1

## Function and Class Templates

This studio focuses on how function and class templates impose requirements on the types with which they are parameterized, and how those requirements define the domains in which interface polymorphism can support the Liskov Substitution Principle. It also explores how non-template functions and classes can impose their own requirements on the types they use.

## Recording Answers

Record your exercise answers in `ANSWERS.md`. Include the names of everyone who worked on the studio in your first answer, and number your responses so they are easy to match to the exercises.

## Working Style

You may complete this studio individually or in a small group.

## Reference

If you need a refresher on the environment setup steps from the previous studio, see [Studio 0](https://github.com/cse4208-wustl/studio0).

## Exercises

1. List the names of the people who worked together on this studio.

2. SSH into `shell.cec.wustl.edu` using your WUSTL Key credentials, then use `qlogin` to log into one of the Linux Lab machines and confirm that the version of `g++` there is correct, as you did in [Studio 0](https://github.com/cse4208-wustl/studio0).

   Then `cd` into your course directory, create a new subdirectory for this studio, and `cd` into it.

   Copy the `Makefile` from your previous studio into that directory. As you work on this studio, update the `Makefile` as needed so that it builds an executable program called `studio1` from the files in that directory.

   Add a header file and a source file to your directory. In them, declare and define a struct that has:

   - a single public member variable of type `int`
   - a public constructor that takes an `int` and uses a base/member initializer list to initialize that member variable

   Add a source file containing `main` so that it:

   - constructs two objects of the struct type with different `int` values
   - prints their member variables with a space in between to `cout`
   - returns a descriptively named symbol with value `0` to indicate success

   Compile and run the program. In your answers, show:

   - your code
   - the output the program produced

3. In your struct declaration, try adding `=delete` declarations that suppress the compiler's synthesis of the:

   - copy constructor
   - copy assignment operator
   - destructor

   Add each one at a time, try to build your program, and if it will not compile, comment out that particular `=delete` declaration so you can see which ones the `main` function requires and which it does not.

   In your answers, show the lines of code you added for this exercise. For any lines that had to be commented out, explain briefly why the program could not be compiled.

4. In your struct declaration, comment out any lines from the previous exercise that are not already commented out.

   In `main`, after printing the objects' member variables, pass the objects themselves into a call to the `std::swap` function template and then print the objects' member variables again to show that their values have been reversed.

   Compile and run your program. In your answers, show the output produced before and after the swap.

5. In your struct declaration, try uncommenting the `=delete` declarations for the:

   - copy constructor
   - copy assignment operator
   - destructor

   Again, do this one at a time, trying to build your program each time. If it does not compile, comment out that particular `=delete` declaration again so you can see which ones are required and which are not.

   In your answers, show all the `=delete` declarations, including those that remained commented out and those that did not. Based on which ones had to be commented out, explain whether `std::swap` imposes additional requirements on the struct type beyond those imposed by `main`, and if so, what those requirements are.

6. Modify the declaration and definition of your struct so that it becomes a struct template with a single parameterized type that defaults to `int`. Then modify `main` so that it declares its objects with empty type parameter lists.

   Modify the header and source files for your struct template so that the header file includes the source file, and modify your `Makefile` so that it treats the source file as a template source file and does not try to compile it directly.

   Compile and run your program, and ensure that it produces the same output as before. In your answers, show your code with those modifications.

7. Modify the declaration and definition of your template so that it is a class instead of a struct, its member variable is private, and all of its member functions are public.

   In the header and source files for the class template, declare and define a template for a left shift operator, `operator<<`, that:

   - takes a reference to an `ostream`
   - takes a `const` reference to an object of the class type
   - inserts the object's private member variable into the `ostream`
   - returns a reference to the `ostream`

   Be sure to include the necessary library header file and add a `using std::ostream;` statement.

   In your class, declare that operator to be a friend of the class so that it can access the object's private member variable.

   Add any forward declarations of the class template or the left shift operator that are needed in the header file so that your code will compile.

   Build and run your program and confirm that it produces the same output as before. In your answers, show the code in the header file.
