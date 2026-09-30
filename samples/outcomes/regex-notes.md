# Regular Expressions

## Quick History

Stephen Cole Kleene, math stuff

Ken Thompson, yes "Unix Ken" - damn that dude is a legend

## Resources Available

### Regex101.com

Interactive demonstration with description of regex

### Regexone.com

Interactive Tutorial

## What can they do?

Some really slick examples of the before and after of a few transforms, look at the examples in the migration page as a demo.

### Filtering for relevant info in log files

### Standardizing Whitespace

### Modifying text to change the semantics

### ViewSE GFX to XML hacking

## What we use

Search functions in VScode

https://code.visualstudio.com/docs/editor/codebasics#_find-and-replace

https://learn.microsoft.com/en-us/visualstudio/ide/using-regular-expressions-in-visual-studio?view=vs-2022 (not specifically vscode, but Visual Studio, though most functions should work)

## How to use regular expressions in VScode

* in single file
* across multiple files

# The basics of regular expression patterns

copy the following text:

``` markdown
sample text, tbd later
```

## Simple patterns

### literals

not any better than standard search and replace

actually worse! because . . . 

* abc…	Letters
* 123…	Digits

#### escaping regex specific stuff

characters that you need to escape:

* . match anything metacharacter
* (, ) subgroup capture
* {, } repetition iterator
* \, / escape characters
* [, ] custom metacharacter set
* ^ (beginning of line mark or negation mark)
* $ (end of line mark)
* + (1 or more repetition)
* * (0 or more repetition)
* ? (optional match)
* and probably others I've forgotten

## Anchors

^ Line Start
\$ Line End

Examples: 

* end of line spaces `` $``
* lines that start with divs ``^:::``

## metacharacters

* \d digit
* \w word
* \s whitespace

### set negation

* \D not digit
* \W not word
* \S not whitespace

### Custom metacharacter sets

[abc]	Only a, b, or c
[a-z]	Characters a to z
[0-9]	Numbers 0 to 9

### Custom metacharacter set negation

[^abc]	Not a, b, nor c

## Capture Groups

### Basic Group Usage

(…)	Capture Group
(.*)	Capture all

Using capture groups as output
$1, $2

### Optional Capture Groups

(abc|def)	Matches abc or def

### Nested Capture Groups (sub-groups)

(a(bc))	Capture Sub-group

## Repetition

### Repetitions

#### Single Character

{m}	m Repetitions
{m,n}	m to n Repetitions

#### Character Sets

*	Zero or more repetitions
+	One or more repetitions
?	Optional character


### Basic Group Usage

(…)	Capture Group
(.*)	Capture all

Using capture groups as output
$1, $2

### Optional Capture Groups

(abc|def)	Matches abc or def

### Nested Capture Groups (sub-groups)

(a(bc))	Capture Sub-group

## Some useful examples

### Remove empty list lines

Sometimes you want to remove list items that do not have text.

``\s`` matches any whitespace character. The lines below have four spaces and then a hyphen for the list item. Using a simple regex, we can replace those lines with NOTHING.

#### Before

``` markdown
70% required for passing the test (and course)
    - Test will be completed in Microsoft Forms (online w/Office 365 Account)
Course and instructor evaluation
    - 
        -
    - 
```

#### After

``` markdown
70% required for passing the test (and course)
    - Test will be completed in Microsoft Forms (online w/Office 365 Account)
Course and instructor evaluation
```

#### Regular Expression

search: ``^\s\s\s\s-\s\n``
\
replace: ``(empty textbox)``

This is good for first depth level, but what about at ANY level

Try this instead

search: ``^\s*-\s*?\n``
\
replace: ``(empty textbox)``

### Replace exported slide blocks with ``rau-slide-plain`` blocks

#### Before

``` markdown
::: {.slide #slide-2}

::: {.title #title}

Course Overview

:::

:::
```

#### After

``` markdown
::: rau-slide-plain

::: {.title #title}

Course Overview

:::

:::
```

#### Regular expression

search: ``\{\.slide #slide-\d*\}``
\
replace: rau-slide-plain

Now, what if we wanted to keep the slide number with the slide plain marker? That's not too hard with a capture group. 

search: ``\{\.slide (#slide-\d*)\}``
\
replace: ``{.rau-slide-plain $1}``

### Replace titles ``{.title #title}`` with a heading

#### Before

``` markdown
::: {.title #title}

Course Overview

:::
```

#### After

``` markdown
## Course Overview
```

#### Regular expression

This regular expression uses a matched group, in parenthesis, and uses that match on the replace line.

search: ``::: \{.title #title\}[\n]+(.*)[\n]+:::``
\
replace: ## $1

We could expand this to make it better - as it doesn't capture this character sequence that it probably should:

```markdown

::: {.subtitle #subtitle}

*End of Presentation*

:::

```

search: ``^::: \{.[^\n]*title #.*title\}[\n]+(.*)[\n]+:::``
\
replace: ``## $1``

How would you rewrite the regex to capture this text as well?

```markdown
::: {.center-title #rectangle}

FactoryTalk Transaction Manager Overview

:::
```

Keep in mind that the 'more loose' you make your regexes, the more likely they are to match things that you don't want to match on.

### Create leading blank line before list

#### Before

``` markdown
4 Day Class
    - ~3.5 days of instruction and/or labs
    - ~0.5 days for review and test
    - 17 labs (plus 2 extra optional labs for Oracle OCI)
    - Mini project
Take breaks as needed and inform instructor of any absences needed
    - Lunch will be ~12:00PM-1PM each day
```

#### After

``` markdown
4 Day Class

    - ~3.5 days of instruction and/or labs
    - ~0.5 days for review and test
    - 17 labs (plus 2 extra optional labs for Oracle OCI)
    - Mini project
Take breaks as needed and inform instructor of any absences needed

    - Lunch will be ~12:00PM-1PM each day
```

#### Regular expression

search: ``^([^\s].*)\n    -``
\
replace: ``$1\n\n    -``

again, what if for some reason someone was crazy and started with an indented list? We can fix that to match patterns more accurately!

search: ``^([^\s].*)\n(\s*?)-``
\
replace: ``$1\n\n$2-``

### Create trailing blank line after list

#### Before

``` markdown
4 Day Class

    - ~3.5 days of instruction and/or labs
    - ~0.5 days for review and test
    - 17 labs (plus 2 extra optional labs for Oracle OCI)
    - Mini project
Take breaks as needed and inform instructor of any absences needed

    - Lunch will be ~12:00PM-1PM each day
```

#### After

``` markdown
4 Day Class

    - ~3.5 days of instruction and/or labs
    - ~0.5 days for review and test
    - 17 labs (plus 2 extra optional labs for Oracle OCI)
    - Mini project

Take breaks as needed and inform instructor of any absences needed

    - Lunch will be ~12:00PM-1PM each day
```

#### Regular expression

This regex uses two pattern groups. They are numbered in the order they occur in the regex.

search: ``\s\s\s\s-\s(.*)\n^([^\s\n])``
\
replace: ``    - $1\n\n$2``

Again, more accurate matching for any (or no) indentation:

search: ``(\s*?)-\s(.*)\n^([^\s\n])``
\
replace: ``$1- $2\n\n$3``

### Remove default indention for lists

#### Before

``` markdown
    - ~3.5 days of instruction and/or labs
    - ~0.5 days for review and test
    - 17 labs (plus 2 extra optional labs for Oracle OCI)
    - Mini project
```

#### After

``` markdown
- ~3.5 days of instruction and/or labs
- ~0.5 days for review and test
- 17 labs (plus 2 extra optional labs for Oracle OCI)
- Mini project
```

#### Regular expression

This one uses the line start anchor ``^``. It matches the *beginning* of a line.

search: ``^\s\s\s\s-``
\
replace: ``-``

This doesn't work well with indentation levels though! We need a different way:

search: ``^(\s{4})(\s*)-(.*)$``
\
replace: ``$2-$3``

### Empty notes sections

#### Before

``` markdown
::: {.notes #notes-2}

`content is empty`

:::
```

#### After

``` markdown
```

(nothing!)

#### Regular expression

search: ``::: \{.notes\s#notes-\d*\}\n\n^`content\sis\sempty`\n\n:::\n``
\
replace: ```` (empty textbox)

If you look at the file, you'll notice there are also some empty content blocks that look like this:

```markdown

::: {.object #content-placeholder}

`content is empty`

:::

```

We can clean those up too! Actually, we can create a regex that will get the above notes AND any empty content blocks:

search: ``::: \{..*\s#.*\}\n\n^`content\sis\sempty`\n\n:::\n``
\
replace: ```` (empty textbox)

This second regex is kind of lazy - it can match a lot of things, but it at least requires the content body to ONLY be `content-is-empty`.
