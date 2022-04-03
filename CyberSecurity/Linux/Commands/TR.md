    

## NAME [top](https://man7.org/linux/man-pages/man1/tr.1p.html#top_of_page)

 tr — translate characters

## SYNOPSIS [top](https://man7.org/linux/man-pages/man1/tr.1p.html#top_of_page)

 tr **[**-c|-C**] [**-s**]** _string1 string2_

 tr -s **[**-c|-C**]** _string1_

 tr -d **[**-c|-C**]** _string1_

 tr -ds **[**-c|-C**]** _string1 string2_

## DESCRIPTION [top](https://man7.org/linux/man-pages/man1/tr.1p.html#top_of_page)

 The _tr_ utility shall copy the standard input to the standard
 output with substitution or deletion of selected characters. The
 options specified and the _string1_ and _string2_ operands shall
 control translations that occur while copying characters and
 single-character collating elements.

## OPTIONS [top](https://man7.org/linux/man-pages/man1/tr.1p.html#top_of_page)

 The _tr_ utility shall conform to the Base Definitions volume of
 POSIX.1‐2017, _Section 12.2_, _Utility Syntax Guidelines_.

 The following options shall be supported:

 **-c** Complement the set of values specified by _string1_.  See
 the EXTENDED DESCRIPTION section.

 **-C** Complement the set of characters specified by _string1_.
 See the EXTENDED DESCRIPTION section.

 **-d** Delete all occurrences of input characters that are
 specified by _string1_.

 **-s** Replace instances of repeated characters with a single
 character, as described in the EXTENDED DESCRIPTION
 section.

## OPERANDS [top](https://man7.org/linux/man-pages/man1/tr.1p.html#top_of_page)

 The following operands shall be supported:

 _string1_, _string2_
 Translation control strings. Each string shall
 represent a set of characters to be converted into an
 array of characters used for the translation. For a
 detailed description of how the strings are
 interpreted, see the EXTENDED DESCRIPTION section.

## STDIN [top](https://man7.org/linux/man-pages/man1/tr.1p.html#top_of_page)

 The standard input can be any type of file.

## INPUT FILES [top](https://man7.org/linux/man-pages/man1/tr.1p.html#top_of_page)

 None.

## ENVIRONMENT VARIABLES [top](https://man7.org/linux/man-pages/man1/tr.1p.html#top_of_page)

 The following environment variables shall affect the execution of
 _tr_:

 _LANG_ Provide a default value for the internationalization
 variables that are unset or null. (See the Base
 Definitions volume of POSIX.1‐2017, _Section 8.2_,
 _Internationalization Variables_ for the precedence of
 internationalization variables used to determine the
 values of locale categories.)

 _LC_ALL_ If set to a non-empty string value, override the values
 of all the other internationalization variables.

 _LC_COLLATE_
 Determine the locale for the behavior of range
 expressions and equivalence classes.

 _LC_CTYPE_ Determine the locale for the interpretation of
 sequences of bytes of text data as characters (for
 example, single-byte as opposed to multi-byte
 characters in arguments) and the behavior of character
 classes.

 _LC_MESSAGES_
 Determine the locale that should be used to affect the
 format and contents of diagnostic messages written to
 standard error.

 _NLSPATH_ Determine the location of message catalogs for the
 processing of _LC_MESSAGES_.

## ASYNCHRONOUS EVENTS [top](https://man7.org/linux/man-pages/man1/tr.1p.html#top_of_page)

 Default.

## STDOUT [top](https://man7.org/linux/man-pages/man1/tr.1p.html#top_of_page)

 The _tr_ output shall be identical to the input, with the exception
 of the specified transformations.

## STDERR [top](https://man7.org/linux/man-pages/man1/tr.1p.html#top_of_page)

 The standard error shall be used only for diagnostic messages.

## OUTPUT FILES [top](https://man7.org/linux/man-pages/man1/tr.1p.html#top_of_page)

 None.

## EXTENDED DESCRIPTION [top](https://man7.org/linux/man-pages/man1/tr.1p.html#top_of_page)

 The operands _string1_ and _string2_ (if specified) define two arrays
 of characters. The constructs in the following list can be used
 to specify characters or single-character collating elements. If
 any of the constructs result in multi-character collating
 elements, _tr_ shall exclude, without a diagnostic, those multi-
 character elements from the resulting array.

 _character_ Any character not described by one of the conventions
 below shall represent itself.

 \_octal_ Octal sequences can be used to represent characters
 with specific coded values. An octal sequence shall
 consist of a <backslash> followed by the longest
 sequence of one, two, or three-octal-digit characters
 (01234567). The sequence shall cause the value whose
 encoding is represented by the one, two, or three-digit
 octal integer to be placed into the array. Multi-byte
 characters require multiple, concatenated escape
 sequences of this type, including the leading
 <backslash> for each byte.

 \_character_
 The <backslash>-escape sequences in the Base
 Definitions volume of POSIX.1‐2017, _Table 5-1_, _Escape_
 _Sequences and Associated Actions_ (**'\\'**, **'\a'**, **'\b'**,
 **'\f'**, **'\n'**, **'\r'**, **'\t'**, **'\v'**) shall be supported. The
 results of using any other character, other than an
 octal digit, following the <backslash> are unspecified.
 Also, if there is no character following the
 <backslash>, the results are unspecified.

 _c_-_c_ In the POSIX locale, this construct shall represent the
 range of collating elements between the range endpoints
 (as long as neither endpoint is an octal sequence of
 the form \_octal_), inclusive, as defined by the
 collation sequence. The characters or collating
 elements in the range shall be placed in the array in
 ascending collation sequence. If the second endpoint
 precedes the starting endpoint in the collation
 sequence, it is unspecified whether the range of
 collating elements is empty, or this construct is
 treated as invalid. In locales other than the POSIX
 locale, this construct has unspecified behavior.

 If either or both of the range endpoints are octal
 sequences of the form \_octal_, this shall represent the
 range of specific coded values between the two range
 endpoints, inclusive.

 [:_class_:] Represents all characters belonging to the defined
 character class, as defined by the current setting of
 the _LC_CTYPE_ locale category. The following character
 class names shall be accepted when specified in
 _string1_:

 **alnum   blank   digit   lower   punct   upper**
 **alpha   cntrl   graph   print   space   xdigit**

 In addition, character class expressions of the form
 [:_name_:] shall be recognized in those locales where the
 _name_ keyword has been given a **charclass** definition in
 the _LC_CTYPE_ category.

 When both the **-d** and **-s** options are specified, any of
 the character class names shall be accepted in _string2_.
 Otherwise, only character class names **lower** or **upper**
 are valid in _string2_ and then only if the corresponding
 character class (**upper** and **lower**, respectively) is
 specified in the same relative position in _string1_.
 Such a specification shall be interpreted as a request
 for case conversion. When [:_lower_:] appears in _string1_
 and [:_upper_:] appears in _string2_, the arrays shall
 contain the characters from the **toupper** mapping in the
 _LC_CTYPE_ category of the current locale. When [:_upper_:]
 appears in _string1_ and [:_lower_:] appears in _string2_,
 the arrays shall contain the characters from the
 **tolower** mapping in the _LC_CTYPE_ category of the current
 locale. The first character from each mapping pair
 shall be in the array for _string1_ and the second
 character from each mapping pair shall be in the array
 for _string2_ in the same relative position.

 Except for case conversion, the characters specified by
 a character class expression shall be placed in the
 array in an unspecified order.

 If the name specified for _class_ does not define a valid
 character class in the current locale, the behavior is
 undefined.

 [=_equiv_=] Represents all characters or collating elements
 belonging to the same equivalence class as _equiv_, as
 defined by the current setting of the _LC_COLLATE_ locale
 category. An equivalence class expression shall be
 allowed only in _string1_, or in _string2_ when it is being
 used by the combined **-d** and **-s** options. The characters
 belonging to the equivalence class shall be placed in
 the array in an unspecified order.

 [_x_*_n_]     Represents _n_ repeated occurrences of the character _x_.
 Because this expression is used to map multiple
 characters to one, it is only valid when it occurs in
 _string2_.  If _n_ is omitted or is zero, it shall be
 interpreted as large enough to extend the _string2_-based
 sequence to the length of the _string1_-based sequence.
 If _n_ has a leading zero, it shall be interpreted as an
 octal value.  Otherwise, it shall be interpreted as a
 decimal value.

 When the **-d** option is not specified:

 *  If _string2_ is present, each input character found in the
 array specified by _string1_ shall be replaced by the character
 in the same relative position in the array specified by
 _string2_.  If the array specified by _string2_ is shorter that
 the one specified by _string1_, or if a character occurs more
 than once in _string1_, the results are unspecified.

 *  If the **-C** option is specified, the complements of the
 characters specified by _string1_ (the set of all characters in
 the current character set, as defined by the current setting
 of _LC_CTYPE_, except for those actually specified in the
 _string1_ operand) shall be placed in the array in ascending
 collation sequence, as defined by the current setting of
 _LC_COLLATE_.

 *  If the **-c** option is specified, the complement of the values
 specified by _string1_ shall be placed in the array in
 ascending order by binary value.

 *  Because the order in which characters specified by character
 class expressions or equivalence class expressions is
 undefined, such expressions should only be used if the intent
 is to map several characters into one. An exception is case
 conversion, as described previously.

 When the **-d** option is specified:

 *  Input characters found in the array specified by _string1_
 shall be deleted.

 *  When the **-C** option is specified with **-d**, all characters
 except those specified by _string1_ shall be deleted. The
 contents of _string2_ are ignored, unless the **-s** option is also
 specified.

 *  When the **-c** option is specified with **-d**, all values except
 those specified by _string1_ shall be deleted. The contents of
 _string2_ shall be ignored, unless the **-s** option is also
 specified.

 *  The same string cannot be used for both the **-d** and the **-s**
 option; when both options are specified, both _string1_ (used
 for deletion) and _string2_ (used for squeezing) shall be
 required.

 When the **-s** option is specified, after any deletions or
 translations have taken place, repeated sequences of the same
 character shall be replaced by one occurrence of the same
 character, if the character is found in the array specified by
 the last operand. If the last operand contains a character class,
 such as the following example:

 tr -s '[:space:]'

 the last operand's array shall contain all of the characters in
 that character class. However, in a case conversion, as described
 previously, such as:

 tr -s '[:upper:]' '[:lower:]'

 the last operand's array shall contain only those characters
 defined as the second characters in each of the **toupper** or
 **tolower** character pairs, as appropriate.

 An empty string used for _string1_ or _string2_ produces undefined
 results.

## EXIT STATUS [top](https://man7.org/linux/man-pages/man1/tr.1p.html#top_of_page)

 The following exit values shall be returned:

 0    All input was processed successfully.

 >0    An error occurred.

## CONSEQUENCES OF ERRORS [top](https://man7.org/linux/man-pages/man1/tr.1p.html#top_of_page)

 Default.

 _The following sections are informative._

## APPLICATION USAGE [top](https://man7.org/linux/man-pages/man1/tr.1p.html#top_of_page)

 If necessary, _string1_ and _string2_ can be quoted to avoid pattern
 matching by the shell.

 If an ordinary digit (representing itself) is to follow an octal
 sequence, the octal sequence must use the full three digits to
 avoid ambiguity.

 When _string2_ is shorter than _string1_, a difference results
 between historical System V and BSD systems. A BSD system pads
 _string2_ with the last character found in _string2_.  Thus, it is
 possible to do the following:

 tr 0123456789 d

 which would translate all digits to the letter **'d'**.  Since this
 area is specifically unspecified in this volume of POSIX.1‐2017,
 both the BSD and System V behaviors are allowed, but a conforming
 application cannot rely on the BSD behavior. It would have to
 code the example in the following way:

 tr 0123456789 '[d*]'

 It should be noted that, despite similarities in appearance, the
 string operands used by _tr_ are not regular expressions.

 Unlike some historical implementations, this definition of the _tr_
 utility correctly processes NUL characters in its input stream.
 NUL characters can be stripped by using:

 tr -d '\000'

## EXAMPLES [top](https://man7.org/linux/man-pages/man1/tr.1p.html#top_of_page)

 1. The following example creates a list of all words in **file1**
 one per line in **file2**, where a word is taken to be a maximal
 string of letters.

 tr -cs "[:alpha:]" "[\n*]" <file1 >file2

 2. The next example translates all lowercase characters in **file1**
 to uppercase and writes the results to standard output.

 tr "[:lower:]" "[:upper:]" <file1

 3. This example uses an equivalence class to identify accented
 variants of the base character **'e'** in **file1**, which are
 stripped of diacritical marks and written to **file2**.

 tr "[=e=]" "[e*]" <file1 >file2

## RATIONALE [top](https://man7.org/linux/man-pages/man1/tr.1p.html#top_of_page)

 In some early proposals, an explicit option **-n** was added to
 disable the historical behavior of stripping NUL characters from
 the input. It was considered that automatically stripping NUL
 characters from the input was not correct functionality.
 However, the removal of **-n** in a later proposal does not remove
 the requirement that _tr_ correctly process NUL characters in its
 input stream. NUL characters can be stripped by using _tr_ **-d**
 '\000'.

 Historical implementations of _tr_ differ widely in syntax and
 behavior. For example, the BSD version has not needed the bracket
 characters for the repetition sequence. The _tr_ utility syntax is
 based more closely on the System V and XPG3 model while
 attempting to accommodate historical BSD implementations. In the
 case of the short _string2_ padding, the decision was to unspecify
 the behavior and preserve System V and XPG3 scripts, which might
 find difficulty with the BSD method.  The assumption was made
 that BSD users of _tr_ have to make accommodations to meet the
 syntax defined here. Since it is possible to use the repetition
 sequence to duplicate the desired behavior, whereas there is no
 simple way to achieve the System V method, this was the correct,
 if not desirable, approach.

 The use of octal values to specify control characters, while
 having historical precedents, is not portable. The introduction
 of escape sequences for control characters should provide the
 necessary portability. It is recognized that this may cause some
 historical scripts to break.

 An early proposal included support for multi-character collating
 elements.  It was pointed out that, while _tr_ does employ some
 syntactical elements from REs, the aim of _tr_ is quite different;
 ranges, for example, do not have a similar meaning (``any of the
 chars in the range matches'', _versus_ ``translate each character
 in the range to the output counterpart''). As a result, the
 previously included support for multi-character collating
 elements has been removed. What remains are ranges in current
 collation order (to support, for example, accented characters),
 character classes, and equivalence classes.

 In XPG3 the [:_class_:] and [=_equiv_=] conventions are shown with
 double brackets, as in RE syntax. However, _tr_ does not implement
 RE principles; it just borrows part of the syntax.  Consequently,
 [:_class_:] and [=_equiv_=] should be regarded as syntactical
 elements on a par with [_x_*_n_], which is not an RE bracket
 expression.

 The standard developers will consider changes to _tr_ that allow it
 to translate characters between different character encodings, or
 they will consider providing a new utility to accomplish this.

 On historical System V systems, a range expression requires
 enclosing square-brackets, such as:

 tr '[a-z]' '[A-Z]'

 However, BSD-based systems did not require the brackets, and this
 convention is used here to avoid breaking large numbers of BSD
 scripts:

 tr a-z A-Z

 The preceding System V script will continue to work because the
 brackets, treated as regular characters, are translated to
 themselves.  However, any System V script that relied on **"a‐z"**
 representing the three characters **'a'**, **'-'**, and **'z'** have to be
 rewritten as **"az-"**.

 The ISO POSIX‐2:1993 standard had a **-c** option that behaved
 similarly to the **-C** option, but did not supply functionality
 equivalent to the **-c** option specified in POSIX.1‐2008.

 The earlier version also said that octal sequences referred to
 collating elements and could be placed adjacent to each other to
 specify multi-byte characters. However, it was noted that this
 caused ambiguities because _tr_ would not be able to tell whether
 adjacent octal sequences were intending to specify multi-byte
 characters or multiple single byte characters. POSIX.1‐2008
 specifies that octal sequences always refer to single byte binary
 values when used to specify an endpoint of a range of collating
 elements.

 Earlier versions of this standard allowed for implementations
 with bytes other than eight bits, but this has been modified in
 this version.