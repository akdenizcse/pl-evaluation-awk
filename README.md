# AWK Language

AWK is a scripting language used for manipulating data and generating reports. The awk command programming language requires no compiling, and allows the user to use variables, numeric functions, string functions, and logical operators.

## History

AWK was created at Bell Labs in the 1970s, and its name is derived from the surnames of its authors: Alfred Aho, Peter Weinberger, and Brian Kernighan. 

AWK was significantly revised and expanded in 1985–88, resulting in the GNU AWK implementation written by Paul Rubin, Jay Fenlason, and Richard Stallman, released in 1988. GNU AWK may be the most widely deployed version because it is included with GNU-based Linux packages.

## Reason

According to Kernighan, one of the goals of AWK was to have a tool that would easily manipulate both numbers and strings. AWK was also inspired by Marc Rochkind's programming language that was used to search for patterns in input data, and was implemented using yacc.

## When/Why shall you use it? 

AWK is most useful when handling text files that are formatted in a predictable way. For instance, it is excellent at parsing and manipulating tabular data. It operates on a line-by-line basis and iterates through the entire file.

You can use it when you need to do some simple string operations on a text file. You can encounter some situations like you have to do same processes on every lines of a text file, you can easily automate this process.

## Environment

Generally, AWK is available by default on most GNU/Linux distributions. You can use which command to check whether it is present on your system or not. In case you don’t have AWK, here is the installation process.

### GNU/Linux

First we are starting with downloading our package information from our configured sources. Second command downloads gawk (GNU AWK). On Debian based Linux, do the following:

```
sudo apt update

sudo apt install gawk
```

Similarly, to install AWK on RPM based GNU/Linux, use Yellowdog Updator Modifier yum package manager.

```
yum install awk
```

After installation, ensure that AWK is accessible via command line.

```
which awk
```

On executing the above code, you get the following result. 

```
/usr/bin/awk
```

### Windows

On Windows operating system you can simply go to this site and download it.

http://gnuwin32.sourceforge.net/packages/gawk.htm

If you want to run it on every path on your system, you should add it to your PATH environment variable.

```
> Go to Control Panel 
> System
> Advanced

set your PATH environment variable to include "C:\Program Files (x86)\GnuWin32\bin" at the end 

(separated by a semi-colon) from previous entry.

```

## Examples

#### Syntax:

```
awk options 'selection _criteria {action }' input-file > output-file
```

#### Options:

```
-f program-file : Reads the AWK program source from the file 
                  program-file, instead of from the 
                  first command line argument.
-F fs            : Use fs for the input field separator
```

The easiest and most commonly used service that awk provides is selecting specific fields from files or from data that is piped to it. With the default of using white space as a field separator, this is very simple.

```
$ echo apple strawberry banana orange pomegranate | awk ‘{print $4}’

orange
```

AWK can also pull text from files by just adding the name of the file after the awk command.

```
$ awk '{print $1,$5,$NF}' HelenKellerQuote

The beautiful heart.
```

In this case, awk has picked out the first, fifth and last words in the single line of test. The $NF specification in the command picks the last piece of text on each line. 

Not all input is going to be separated by white space. If your text is separated by some other character (e.g., commas, colons or semicolons), you can inform awk by using the -F (input separator).

```
$ cat testfile

a:b:c,d:e

$ awk -F : '{print $2,$3}' testfile

b c,d
```

Here's a more useful example – pulling a field from the colon-separated /etc/passwd file:

```
$ awk -F: '{print $1}' /etc/passwd | head -11
root
daemon
bin
sys
sync
games
man
lp
mail
news
uucp
```
