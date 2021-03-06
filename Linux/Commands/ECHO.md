    

NAME top

echo — write arguments to standard output

SYNOPSIS top

echo [string...]

DESCRIPTION top

The echo utility writes its arguments to standard output,

followed by a <newline>. If there are no arguments, only the

<newline> is written.

OPTIONS top

The echo utility shall not recognize the "--" argument in the

manner specified by Guideline 10 of the Base Definitions volume

of POSIX.1‐2017, Section 12.2, Utility Syntax Guidelines; "--"

shall be recognized as a string operand.

  

Implementations shall not support any options.

OPERANDS top

The following operands shall be supported:

  

string A string to be written to standard output. If the first

operand is -n, or if any of the operands contain a

<backslash> character, the results are implementation-

defined.

  

On XSI-conformant systems, if the first operand is -n,

it shall be treated as a string, not an option. The

following character sequences shall be recognized on

XSI-conformant systems within any of the arguments:

  

\a Write an <alert>.

  

\b Write a <backspace>.

  

\c Suppress the <newline> that otherwise follows

the final argument in the output. All

characters following the '\c' in the arguments

shall be ignored.

  

\f Write a <form-feed>.

  

\n Write a <newline>.

  

\r Write a <carriage-return>.

  

\t Write a <tab>.

  

\v Write a <vertical-tab>.

  

\\ Write a <backslash> character.

  

\0num Write an 8-bit value that is the zero, one,

two, or three-digit octal number num.

STDIN top

Not used.

INPUT FILES top

None.

ENVIRONMENT VARIABLES top

The following environment variables shall affect the execution of

echo:

  

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

ASYNCHRONOUS EVENTS top

Default.

STDOUT top

The echo utility arguments shall be separated by single <space>

characters and a <newline> character shall follow the last

argument. Output transformations shall occur based on the escape

sequences in the input. See the OPERANDS section.

STDERR top

The standard error shall be used only for diagnostic messages.

OUTPUT FILES top

None.

EXTENDED DESCRIPTION top

None.

EXIT STATUS top

The following exit values shall be returned:

  

0 Successful completion.

  

>0 An error occurred.

CONSEQUENCES OF ERRORS top

Default.

  

The following sections are informative.

APPLICATION USAGE top

It is not possible to use echo portably across all POSIX systems

unless both -n (as the first argument) and escape sequences are

omitted.

  

The printf utility can be used portably to emulate any of the

traditional behaviors of the echo utility as follows (assuming

that IFS has its standard value or is unset):

  

* The historic System V echo and the requirements on XSI

implementations in this volume of POSIX.1‐2017 are equivalent

to:

  

printf "%b\n$*"

  

* The BSD echo is equivalent to:

  

if [ "X$1" = "X-n" ]

then

shift

printf "%s$*"

else

printf "%s\n$*"

fi

  

New applications are encouraged to use printf instead of echo.