    

NAME         top

cat — concatenate and print files

SYNOPSIS         top

cat [-u] [file...]

DESCRIPTION         top

The cat utility shall read files in sequence and shall write

their contents to the standard output in the same sequence.

OPTIONS         top

The cat utility shall conform to the Base Definitions volume of

POSIX.1‐2017, Section 12.2, Utility Syntax Guidelines.

  

The following option shall be supported:

  

-u Write bytes from the input file to the standard output

without delay as each is read.

OPERANDS         top

The following operand shall be supported:

  

file A pathname of an input file. If no file operands are

specified, the standard input shall be used. If a file

is '-', the cat utility shall read from the standard

input at that point in the sequence. The cat utility

shall not close and reopen standard input when it is

referenced in this way, but shall accept multiple

occurrences of '-' as a file operand.

STDIN         top

The standard input shall be used only if no file operands are

specified, or if a file operand is '-'. See the INPUT FILES

section.

INPUT FILES         top

The input files can be any file type.

ENVIRONMENT VARIABLES         top

The following environment variables shall affect the execution of

cat:

  

LANG Provide a default value for the internationalization

variables that are unset or null. (See the Base

Definitions volume of POSIX.1‐2017, Section 8.2,

Internationalization Variables for the precedence of

internationalization variables used to determine the

values of locale categories.)

  

LC_ALL If set to a non-empty string value, override the values

of all the other internationalization variables.

  

LC_CTYPE Determine the locale for the interpretation of

sequences of bytes of text data as characters (for

example, single-byte as opposed to multi-byte

characters in arguments).

  

LC_MESSAGES

Determine the locale that should be used to affect the

format and contents of diagnostic messages written to

standard error.

  

NLSPATH Determine the location of message catalogs for the

processing of LC_MESSAGES.

ASYNCHRONOUS EVENTS         top

Default.

STDOUT         top

The standard output shall contain the sequence of bytes read from

the input files. Nothing else shall be written to the standard

output. If the standard output is a regular file, and is the

same file as any of the input file operands, the implementation

may treat this as an error.

STDERR         top

The standard error shall be used only for diagnostic messages.

OUTPUT FILES         top

None.

EXTENDED DESCRIPTION         top

None.

EXIT STATUS         top

The following exit values shall be returned:

  

0 All input files were output successfully.

  

>0 An error occurred.

CONSEQUENCES OF ERRORS         top

Default.

  

The following sections are informative.

APPLICATION USAGE         top

The -u option has value in prototyping non-blocking reads from

FIFOs. The intent is to support the following sequence:

  

mkfifo foo

cat -u foo > /dev/tty13 &

cat -u > foo

  

It is unspecified whether standard output is or is not buffered

in the default case. This is sometimes of interest when standard

output is associated with a terminal, since buffering may delay

the output. The presence of the -u option guarantees that

unbuffered I/O is available. It is implementation-defined whether

the cat utility buffers output if the -u option is not specified.

Traditionally, the -u option is implemented using the equivalent

of the setvbuf() function defined in the System Interfaces volume

of POSIX.1‐2017.

EXAMPLES         top

The following command:

  

cat myfile

  

writes the contents of the file myfile to standard output.

  

The following command:

  

cat doc1 doc2 > doc.all

  

concatenates the files doc1 and doc2 and writes the result to

doc.all.

  

Because of the shell language mechanism used to perform output

redirection, a command such as this:

  

cat doc doc.end > doc

  

causes the original data in doc to be lost before cat even begins

execution. This is true whether the cat command fails with an

error or silently succeeds (the specification allows both

behaviors). In order to append the contents of doc.end without

losing the original contents of doc, this command should be used

instead:

  

cat doc.end >> doc

  

The command:

  

cat start - middle - end > file

  

when standard input is a terminal, gets two arbitrary pieces of

input from the terminal with a single invocation of cat. Note,

however, that if standard input is a regular file, this would be

equivalent to the command:

  

cat start - middle /dev/null end > file

  

because the entire contents of the file would be consumed by cat

the first time '-' was used as a file operand and an end-of-file

condition would be detected immediately when '-' was referenced

the second time.