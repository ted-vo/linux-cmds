# AWK

## What is AWK?

`awk` is a scripting language used for manipulating data and generating reports. The `awk` command programming language requires no compiling and allows the user to use variables, numeric functions, string functions, and logical operators.
a
`awk` is a utility that enables a programmer to write tiny but effective programs in the form of statements that define text patterns that are to be searched for in each line of a document and the action that is to be taken when a match is found within a line. Awk is mostly used for pattern scanning and processing. It searches one or more files to see if they contain lines that matches with the specified patterns and then perform the associated actions.
a
`awk` is abbreviated from the names of the developers – Aho, Weinberger, and Kernighan.

WHAT CAN WE DO WITH `AWK`?

1. `AWK` Operations:
   (a) Scans a file line by line
   (b) Splits each input line into fields
   (c) Compares input line/fields to pattern
   (d) Performs action(s) on matched lines

2. Useful For:
   (a) Transform data files
   (b) Produce formatted reports

3. Programming Constructs:
   (a) Format output lines
   (b) Arithmetic and string operations
   (c) Conditionals and loops

## GAWK

`gawk` command in Linux is used for pattern scanning and processing language. The `awk` command requires no compiling and allows the user to use variables, numeric functions, string functions, and logical operators. It is a utility that enables programmers to write tiny and effective programs in the form of statements that define text patterns that are to be searched for, in a text document and the action that is to be taken when a match is found within a line.

`gawk` command can be used to :

- Scans a file line by line.
- Splits each input line into fields.
- Compares input line/fields to pattern.
- Performs action(s) on matched lines.
- Transform data files.
- Produce formatted reports.
- Format output lines.
- Arithmetic and string operations.
- Conditionals and loops.

## AWK, NAWK and GAWK?

```plaintext
AWK is a programming language. There are several implementations of AWK (mostly in the form of interpreters). AWK has been codified in POSIX. The main implementations in use today are:

- nawk (“new awk”, an evolution of oawk, the original UNIX implementation), used on \*BSD and widely available on Linux;
- mawk, a fast implementation that mostly sticks to standard features;
- gawk, the GNU implementation, with many extensions;
  the Busybox (small, intended for embedded systems, not many features).
  If you only care about standard features, call awk, which may be Gawk or nawk or mawk or some other implementation. If you want the features in GNU awk, use gawk or Perl or Python.
```

Should I always use GAWK over AWK?

```plaintext
awk can refer to many things. There's awk-the-standard, and there's many different implementations, one of which is gawk.

Not using implementation-specific features means that you'll have a high(er) chance that your code will run unchanged on other implementations of awk-the-language.

gawk, being one implementation of awk-the-language, claims to conform to awk-the-standard, while adding some extra features.

$ man awk
…
DESCRIPTION
   Gawk is the GNU Project's implementation of the AWK programming
   language.  It conforms to the definition of the language in the
   POSIX 1003.1 Standard.  This version in turn is  based  on  the
   description in The AWK Programming Language, by Aho, Kernighan,
   and Weinberger.  Gawk provides the additional features found in
   the current version of Brian Kernighan's awk and  a  number  of
   GNU-specific extensions.
…
As for speed, using gawk as "plain" awk should make no difference – often, when gawk is installed, awk will just be a symlink to gawk which means they'll be exactly the same program.

However, using gawk-specific features will mean that you'll be locked in to that specific implementation – so if (hypothetically) you'd find a faster implementation, you'd probably have to adapt your script instead of just swapping out the binary. (There may be implementations that are faster, but I don't know of any as I've never had the need to make my awk scripts run faster.
```

# Workflows

        -----------------------------------------
       | Execute AWK commands from `BEGIN` block |
        -----------------------------------------
                           |
        -----------------------------------------
    .--|       Read a line from input stream     |
    |   -----------------------------------------
    |                      |
    |   -----------------------------------------
    |  |       Execute AWK commands on line      |
    |   -----------------------------------------
    |                      |
    |   -----------------------------------------
    |  |       Repeat if it not END OF FILE      |
    |   -----------------------------------------
     ----------------------|
        -----------------------------------------
       | Execute AWK commands from `END` block   |
        -----------------------------------------

Read
AWK reads a line from the input stream (file, pipe, or stdin) and stores it in memory.

Execute
All AWK commands are applied sequentially on the input. By default AWK execute commands on every line. We can restrict this by providing patterns.

Repeat
This process repeats until the file reaches its end.

## Program Structure

Let us now understand the program structure of AWK.

BEGIN block (optional)
The syntax of the BEGIN block is as follows −

Syntax

> BEGIN {awk-commands}

- This is optional
- The BEGIN block gets executed at program start-up and executes only once.
- This is good place to initialize variables. BEGIN is an AWK keyword and hence it must be in upper-case.

Body Block
The syntax of the body block is as follows −

Syntax

> /pattern/ {awk-commands}

- This is optional
- AWK executes commands on every line.
- We can restrict this by providing patterns

END Block (optional)
The syntax of the END block is as follows −

Syntax

> END {awk-commands}

- This is optional
- The END block executes at the end of the program and executes only once.
- This is good place to clear sometime after process if needed. END is an AWK keyword and hence it must be in upper-case.

## Basic Syntax

<details>
    <summary>AWK command line</summary>

> awk [options] file ...

```bash
echo > list.txt "line 1
line 2
line 3
line 4"
```

```bash
awk '{print}' list.txt
```

Output

```plaintext
line 1
line 2
line 3
line 4
```

</details>

<details>
    <summary>AWK program file</summary>

> awk [options] -f file ....

```bash
# create program file
echo "{print}" > command.awk
```

```bash
awk -f command.awk list.txt
```

Output

```plaintext
line 1
line 2
line 3
line 4
```

</details>

## Basic examples

```bash
echo > students.txt "1 James Male
2 Neko Male
3 David Male
4 Ana Female"
```

<details>
    <summary>Printing All Lines</summary>

```bash
# by default print all line
awk '{ print }' students.txt
```

```bash
# $0 aka all line
awk '{ print $0 }' students.txt
```

Output:

```plaintext
1 James Male
2 Neko Male
3 David Male
4 Ana Female
```

```bash
# add some format
awk '{ print " * " $0 }' students.txt
```

Output:

```plaintext
 * 1 James Male
 * 2 Neko Male
 * 3 David Male
 * 4 Ana Female
```

</details>

<details>
    <summary>Printing Column or Field</summary>

```bash
# 2 Neko Male
# $1  $2   $3
awk '{ print $2 "\t" $3 }' students.txt
```

Output:

```plaintext
James   Male
Neko    Male
David   Male
Ana     Female
```

```bash
# any order
awk '{ print $3 "\t" $2 }' students.txt
```

Output:

```plaintext
Male   James
Male   Neko
Male   David
Female Ana
```

</details>

<details>
    <summary>Fileter by pattern</summary>

```bash
awk '/Female/ { print }' students.txt
```

Output:

```plaintext
4 Ana Female
```

</details>

<details>
    <summary>Counting and Printing Matched Pattern</summary>

```bash
awk '/Female/ { ++count } END { print count }' students.txt
```

Output:

```plaintext
1
```

</details>

<details>
    <summary>Condition</summary>

```bash
awk '/Male/ { if ($2 == "David" ) print }' students.txt
```

Output:

```plaintext
3 David Male
```

</details>

<details>
    <summary>Pipline</summary>

```bash
awk '/Male/ { if ($2 == "David" ) print $2 | "tr [a-z] [A-Z]" }' students.txt
```

Output:

```plaintext
DAVID
```

</details>

## Advance examples

- [Operators](https://www.tutorialspoint.com/awk/awk_operators.htm)
- [Regular Expressions](https://www.tutorialspoint.com/awk/awk_regular_expressions.htm)
- [Arrays](https://www.tutorialspoint.com/awk/awk_arrays.htm)
- [Control flow](https://www.tutorialspoint.com/awk/awk_control_flow.htm)
- [Loops](https://www.tutorialspoint.com/awk/awk_loops.htm)
- [Built-in Function](https://www.tutorialspoint.com/awk/awk_built_in_functions.htm)
- [Define Functions](https://www.tutorialspoint.com/awk/awk_user_defined_functions.htm)
- [Pretty Printing](https://www.tutorialspoint.com/awk/awk_pretty_printing.htm)

# References

- https://www.geeksforgeeks.org/awk-command-unixlinux-examples/
- https://www.geeksforgeeks.org/gawk-command-in-linux-with-examples/
- https://unix.stackexchange.com/a/29583
- https://stackoverflow.com/a/29807182
- https://www.tutorialspoint.com/awk

# References

- https://www.geeksforgeeks.org/awk-command-unixlinux-examples/
- https://www.geeksforgeeks.org/gawk-command-in-linux-with-examples/
- https://unix.stackexchange.com/a/29583
- https://stackoverflow.com/a/29807182
- https://www.tutorialspoint.com/awk
