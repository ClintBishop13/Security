    

NAME top

touch — change file access and modification times

SYNOPSIS top

touch [-acm] [-r ref_file|-t time|-d date_time] file...

DESCRIPTION top

The touch utility shall change the last data modification

timestamps, the last data access timestamps, or both.

  

The time used can be specified by the -t time option-argument,

the corresponding time fields of the file referenced by the -r

ref_file option-argument, or the -d date_time option-argument, as

specified in the following sections. If none of these are

specified, touch shall use the current time.

  

For each file operand, touch shall perform actions equivalent to

the following functions defined in the System Interfaces volume

of POSIX.1‐2017:

  

1. If file does not exist:

  

a. The creat() function is called with the following

arguments:

  

-- The file operand is used as the path argument.

  

-- The value of the bitwise-inclusive OR of S_IRUSR,

S_IWUSR, S_IRGRP, S_IWGRP, S_IROTH, and S_IWOTH is

used as the mode argument.

  

b. The futimens() function is called with the following

arguments:

  

-- The file descriptor opened in step 1a.

  

-- The access time and the modification time, set as

described in the OPTIONS section, are used as the

first and second elements of the times array

argument, respectively.

  

2. If file exists, the utimensat() function is called with the

following arguments:

  

a. The AT_FDCWD special value is used as the fd argument.

  

b. The file operand is used as the path argument.

  

c. The access time and the modification time, set as

described in the OPTIONS section, are used as the first

and second elements of the times array argument,

respectively.

  

d. The flag argument is set to zero.

OPTIONS top

The touch utility shall conform to the Base Definitions volume of

POSIX.1‐2017, Section 12.2, Utility Syntax Guidelines.

  

The following options shall be supported:

  

-a Change the access time of file. Do not change the

modification time unless -m is also specified.

  

-c Do not create a specified file if it does not exist. Do

not write any diagnostic messages concerning this

condition.

  

-d date_time

Use the specified date_time instead of the current

time. The option-argument shall be a string of the

form:

  

YYYY-MM-DDThh:mm:SS[.frac][tz]

  

or:

  

YYYY-MM-DDThh:mm:SS[,frac][tz]

  

where:

  

* YYYY are at least four decimal digits giving the

year.

  

* MM, DD, hh, mm, and SS are as with -t time.

  

* T is the time designator, and can be replaced by a

single <space>.

  

* [.frac] and [,frac] are either empty, or a <period>

('.') or a <comma> (',') respectively, followed by

one or more decimal digits, specifying a fractional

second.

  

* [tz] is either empty, signifying local time, or the

letter 'Z', signifying UTC. If [tz] is empty, the

resulting time shall be affected by the value of

the TZ environment variable.

  

If the resulting time precedes the Epoch, the behavior

is implementation-defined. If the time cannot be

represented as the file's timestamp, touch shall exit

immediately with an error status.

  

-m Change the modification time of file. Do not change

the access time unless -a is also specified.

  

-r ref_file

Use the corresponding time of the file named by the

pathname ref_file instead of the current time.

  

-t time Use the specified time instead of the current time. The

option-argument shall be a decimal number of the form:

  

[[CC]YY]MMDDhhmm[.SS]

  

where each two digits represents the following:

  

MM The month of the year [01,12].

  

DD The day of the month [01,31].

  

hh The hour of the day [00,23].

  

mm The minute of the hour [00,59].

  

CC The first two digits of the year (the century).

  

YY The second two digits of the year.

  

SS The second of the minute [00,60].

  

Both CC and YY shall be optional. If neither is given,

the current year shall be assumed. If YY is specified,

but CC is not, CC shall be derived as follows:

  

┌──────────┬─────────────┐

│If YY is: │ CC becomes: │

├──────────┼─────────────┤

│ [69,99] │ 19 │

│ [00,68] │ 20 │

└──────────┴─────────────┘

Note: It is expected that in a future version of this

standard the default century inferred from a

2-digit year will change. (This would apply to

all commands accepting a 2-digit year as input.)

  

The resulting time shall be affected by the value of

the TZ environment variable. If the resulting time

value precedes the Epoch, the behavior is

implementation-defined. If the time is out of range for

the file's timestamp, touch shall exit immediately with

an error status. The range of valid times past the

Epoch is implementation-defined, but it shall extend to

at least the time 0 hours, 0 minutes, 0 seconds,

January 1, 2038, Coordinated Universal Time. Some

implementations may not be able to represent dates

beyond January 18, 2038, because they use signed int as

a time holder.

  

The range for SS is [00,60] rather than [00,59] because

of leap seconds. If SS is 60, and the resulting time,

as affected by the TZ environment variable, does not

refer to a leap second, the resulting time shall be one

second after a time where SS is 59. If SS is not given

a value, it is assumed to be zero.

  

If neither the -a nor -m options were specified, touch shall

behave as if both the -a and -m options were specified.

OPERANDS top

The following operands shall be supported:

  

file A pathname of a file whose times shall be modified.

STDIN top

Not used.

INPUT FILES top

None.

ENVIRONMENT VARIABLES top

The following environment variables shall affect the execution of

touch:

  

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

  

TZ Determine the timezone to be used for interpreting the

time option-argument. If TZ is unset or null, an

unspecified default timezone shall be used.

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

  

0 The utility executed successfully and all requested changes

were made.

  

>0 An error occurred.

CONSEQUENCES OF ERRORS top

Default.

  

The following sections are informative.

APPLICATION USAGE top

The interpretation of time is taken to be seconds since the Epoch

(see the Base Definitions volume of POSIX.1‐2017, Section 4.16,

Seconds Since the Epoch). It should be noted that

implementations conforming to the System Interfaces volume of

POSIX.1‐2017 do not take leap seconds into account when computing

seconds since the Epoch. When SS=60 is used, the resulting time

always refers to 1 plus seconds since the Epoch for a time when

SS=59.

  

Although the -t time option-argument specifies values in 1969,

the access time and modification time fields are defined in terms

of seconds since the Epoch (00:00:00 on 1 January 1970 UTC).

Therefore, depending on the value of TZ when touch is run, there

is never more than a few valid hours in 1969 and there need not

be any valid times in 1969.

  

If the T time designator is replaced by a <space> for the -d

date_time option-argument, the <space> must be quoted to prevent

the shell from splitting the argument.

EXAMPLES top

Create or update a file called dwc; the resulting file has both

the last data modification and last data access timestamps set to

November 12, 2007 at 10:15:30 local time:

  

touch -d 2007-11-12T10:15:30 dwc

  

Create or update a file called nick; the resulting file has both

the last data modification and last data access timestamps set to

November 12, 2007 at 10:15:30 UTC:

  

touch -d 2007-11-12T10:15:30Z nick

  

Create or update a file called gwc; the resulting file has both

the last data modification and last data access timestamps set to

November 12, 2007 at 10:15:30 local time with a fractional second

timestamp of .002 seconds:

  

touch -d 2007-11-12T10:15:30,002 gwc

  

Create or update a file called ajosey; the resulting file has

both the last data modification and last data access timestamps

set to November 12, 2007 at 10:15:30 UTC with a fractional second

timestamp of .002 seconds:

  

touch -d "2007-11-12 10:15:30.002Z" ajosey

  

Create or update a file called cathy; the resulting file has both

the last data modification and last data access timestamps set to

November 12, 2007 at 10:15:00 local time:

  

touch -t 200711121015 cathy

  

Create or update a file called drepper; the resulting file has

both the last data modification and last data access timestamps

set to November 12, 2007 at 10:15:30 local time:

  

touch -t 200711121015.30 drepper

  

Create or update a file called ebb9; the resulting file has both

the last data modification and last data access timestamps set to

November 12, 2007 at 10:15:30 local time:

  

touch -t 0711121015.30 ebb9

  

Create or update a file called eggert; the resulting file has the

last data access timestamp set to the corresponding time of the

file named mark instead of the current time. If the file exists,

the last data modification time is not changed:

  

touch -a -r mark eggert