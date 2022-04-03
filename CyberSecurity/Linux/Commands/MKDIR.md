NAME top

mkdir — make directories

SYNOPSIS top

mkdir [-p] [-m mode] dir...

DESCRIPTION top

The mkdir utility shall create the directories specified by the

operands, in the order specified.

  

For each dir operand, the mkdir utility shall perform actions

equivalent to the mkdir() function defined in the System

Interfaces volume of POSIX.1‐2017, called with the following

arguments:

  

1. The dir operand is used as the path argument.

  

2. The value of the bitwise-inclusive OR of S_IRWXU, S_IRWXG,

and S_IRWXO is used as the mode argument. (If the -m option

is specified, the value of the mkdir() mode argument is

unspecified, but the directory shall at no time have

permissions less restrictive than the -m mode option-

argument.)

OPTIONS top

The mkdir utility shall conform to the Base Definitions volume of

POSIX.1‐2017, Section 12.2, Utility Syntax Guidelines.

  

The following options shall be supported:

  

-m mode Set the file permission bits of the newly-created

directory to the specified mode value. The mode option-

argument shall be the same as the mode operand defined

for the chmod utility. In the symbolic_mode strings,

the op characters '+' and '-' shall be interpreted

relative to an assumed initial mode of a=rwx; '+' shall

add permissions to the default mode, '-' shall delete

permissions from the default mode.

  

-p Create any missing intermediate pathname components.

  

For each dir operand that does not name an existing

directory, before performing the actions described in

the DESCRIPTION above, the mkdir utility shall create

any pathname components of the path prefix of dir that

do not name an existing directory by performing actions

equivalent to first calling the mkdir() function with

the following arguments:

  

1. A pathname naming the missing pathname component,

ending with a trailing <slash> character, as the

path argument

  

2. The value zero as the mode argument

  

and then calling the chmod() function with the

following arguments:

  

1. The same path argument as in the mkdir() call

  

2. The value (S_IWUSR|S_IXUSR|~filemask)&0777 as the

mode argument, where filemask is the file mode

creation mask of the process (see the System

Interfaces volume of POSIX.1‐2017, umask(3p))

  

Each dir operand that names an existing directory shall

be ignored without error.

OPERANDS top

The following operand shall be supported:

  

dir A pathname of a directory to be created.

STDIN top

Not used.

INPUT FILES top

None.

ENVIRONMENT VARIABLES top

The following environment variables shall affect the execution of

mkdir:

  

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

Not used.

STDERR top

The standard error shall be used only for diagnostic messages.

OUTPUT FILES top

None.

EXTENDED DESCRIPTION top

None.

EXIT STATUS top

The following exit values shall be returned:

  

0 All the specified directories were created successfully, or

the -p option was specified and all the specified

directories either already existed or were created

successfully.

  

>0 An error occurred.

CONSEQUENCES OF ERRORS top

Default.

  

The following sections are informative.

APPLICATION USAGE top

The default file mode for directories is a=rwx (777 on most

systems) with selected permissions removed in accordance with the

file mode creation mask. For intermediate pathname components

created by mkdir, the mode is the default modified by u+wx so

that the subdirectories can always be created regardless of the

file mode creation mask; if different ultimate permissions are

desired for the intermediate directories, they can be changed

afterwards with chmod.

  

Note that some of the requested directories may have been created

even if an error occurs.