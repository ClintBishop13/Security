NAME         top
       strings — find printable strings in files
SYNOPSIS         top
       strings [-a] [-t format] [-n number] [file...]
DESCRIPTION         top
       The strings utility shall look for printable strings in regular
       files and shall write those strings to standard output. A
       printable string is any sequence of four (by default) or more
       printable characters terminated by a <newline> or NUL character.
       Additional implementation-defined strings may be written; see
       localedef.

       If the first argument is '-', the results are unspecified.
OPTIONS         top
       The strings utility shall conform to the Base Definitions volume
       of POSIX.1‐2017, Section 12.2, Utility Syntax Guidelines, except
       for the unspecified usage of '-'.

       The following options shall be supported:

       -a        Scan files in their entirety. If -a is not specified,
                 it is implementation-defined what portion of each file
                 is scanned for strings.

       -n number Specify the minimum string length, where the number
                 argument is a positive decimal integer. The default
                 shall be 4.

       -t format Write each string preceded by its byte offset from the
                 start of the file. The format shall be dependent on the
                 single character used as the format option-argument:

                 d     The offset shall be written in decimal.

                 o     The offset shall be written in octal.

                 x     The offset shall be written in hexadecimal.
OPERANDS         top
       The following operand shall be supported:

       file      A pathname of a regular file to be used as input. If no
                 file operand is specified, the strings utility shall
                 read from the standard input.
STDIN         top
       See the INPUT FILES section.
INPUT FILES         top
       The input files named by the utility arguments or the standard
       input shall be regular files of any format.
ENVIRONMENT VARIABLES         top
       The following environment variables shall affect the execution of
       strings:

       LANG      Provide a default value for the internationalization
                 variables that are unset or null. (See the Base
                 Definitions volume of POSIX.1‐2017, Section 8.2,
                 Internationalization Variables for the precedence of
                 internationalization variables used to determine the
                 values of locale categories.)

       LC_ALL    If set to a non-empty string value, override the values
                 of all the other internationalization variables.

       LC_CTYPE  Determine the locale for the interpretation of
                 sequences of bytes of text data as characters (for
                 example, single-byte as opposed to multi-byte
                 characters in arguments and input files) and to
                 identify printable strings.

       LC_MESSAGES
                 Determine the locale that should be used to affect the
                 format and contents of diagnostic messages written to
                 standard error.

       NLSPATH   Determine the location of message catalogs for the
                 processing of LC_MESSAGES.
ASYNCHRONOUS EVENTS         top
       Default.
STDOUT         top
       Strings found shall be written to the standard output, one per
       line.

       When the -t option is not specified, the format of the output
       shall be:

           "%s", <string>

       With the -t o option, the format of the output shall be:

           "%o %s", <byte offset>, <string>

       With the -t x option, the format of the output shall be:

           "%x %s", <byte offset>, <string>

       With the -t d option, the format of the output shall be:

           "%d %s", <byte offset>, <string>
STDERR         top
       The standard error shall be used only for diagnostic messages.
OUTPUT FILES         top
       None.
EXTENDED DESCRIPTION         top
       None.
EXIT STATUS         top
       The following exit values shall be returned:

        0    Successful completion.

       >0    An error occurred.
CONSEQUENCES OF ERRORS         top
       Default.

       The following sections are informative.
APPLICATION USAGE         top
       By default the data area (as opposed to the text, ``bss'', or
       header areas) of a binary executable file is scanned.
       Implementations document which areas are scanned.

       Some historical implementations do not require NUL or <newline>
       terminators for strings to permit those languages that do not use
       NUL as a string terminator to have their strings written.