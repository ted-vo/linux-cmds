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

## AWK and GAWK?

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

## Examples

<details>
    <summary>Scans a file line by line</summary>

```bash
cd awk
awk '{ print }' employee.txt

# ajay manager account 45000
# sunil clerk account 25000
# varun manager sales 50000
# amit manager account 47000
# tarun peon sales 15000
# deepak clerk sales 23000
# sunil peon sales 13000
# satvik director purchase 80000
```

</details>

## Ref

    - https://www.geeksforgeeks.org/awk-command-unixlinux-examples/
    - https://www.geeksforgeeks.org/gawk-command-in-linux-with-examples/
    - https://unix.stackexchange.com/a/29583
    - https://stackoverflow.com/a/29807182
