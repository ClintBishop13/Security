    

NAME top

pwd — return working directory name

SYNOPSIS top

pwd [-L|-P]

DESCRIPTION top

The pwd utility shall write to standard output an absolute

pathname of the current working directory, which does not contain

the filenames dot or dot-dot.

OPTIONS top

The pwd utility shall conform to the Base Definitions volume of

POSIX.1‐2017, Section 12.2, Utility Syntax Guidelines.

  

The following options shall be supported by the implementation:

  

-L If the PWD environment variable contains an absolute

pathname of the current directory and the pathname does

not contain any components that are dot or dot-dot, pwd

shall write this pathname to standard output, except

that if the PWD environment variable is longer than

{PATH_MAX} bytes including the terminating null, it is

unspecified whether pwd writes this pathname to

standard output or behaves as if the -P option had been

specified. Otherwise, the -L option shall behave as the

-P option.

  

-P The pathname written to standard output shall not

contain any components that refer to files of type

symbolic link. If there are multiple pathnames that the

pwd utility could write to standard output, one

beginning with a single <slash> character and one or

more beginning with two <slash> characters, then it

shall write the pathname beginning with a single

<slash> character. The pathname shall not contain any

unnecessary <slash> characters after the leading one or

two <slash> characters.

  

If both -L and -P are specified, the last one shall apply. If

neither -L nor -P is specified, the pwd utility shall behave as

if -L had been specified.

OPERANDS top

None.

STDIN top

Not used.

INPUT FILES top

None.

ENVIRONMENT VARIABLES top

The following environment variables shall affect the execution of

pwd:

  

LANG Provide a default value for the internationalization

variables that are unset or null. (See the Base

Definitions volume of POSIX.1‐2017, Section 8.2,

Internationalization Variables the precedence of

internationalization variables used to determine the

values of locale categories.)

  

LC_ALL If set to a non-empty string value, override the values

of all the other internationalization variables.

  

LC_MESSAGES

Determine the locale that should be used to affect the

format and contents of diagnostic messages written to

standard error.

  

NLSPATH Determine the location of message catalogs for the

processing of LC_MESSAGES.

  

PWD An absolute pathname of the current working directory.

If an application sets or unsets the value of PWD, the

behavior of pwd is unspecified.

ASYNCHRONOUS EVENTS top

Default.

STDOUT top

The pwd utility output is an absolute pathname of the current

working directory:

  

"%s\n", <directory pathname>

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

If an error is detected, output shall not be written to standard

output, a diagnostic message shall be written to standard error,

and the exit status is not zero.

  

The following sections are informative.

APPLICATION USAGE top

If the pathname obtained from pwd is longer than {PATH_MAX}

bytes, it could produce an error if passed to cd. Therefore, in

order to return to that directory it may be necessary to break

the pathname into sections shorter than {PATH_MAX} and call cd on

each section in turn (the first section being an absolute

pathname and subsequent sections being relative pathnames).