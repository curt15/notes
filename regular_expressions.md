Links: [[PROGRAMMING]] - [[TECHNOLOGY]]

--- 
**Identifiers**:  
	
.       - Any Character Except New Line
\\d      - Digit (0-9)
\\D      - Not a Digit (0-9)
\\w      - Word Character (a-z, A-Z, 0-9, \_)
\\W      - Not a Word Character
\\s      - Whitespace (space, tab, newline)
\\S      - Not Whitespace (space, tab, newline)
  
\\b      - Word Boundary
\\B      - Not a Word Boundary
^       - Beginning of a String
$       - End of a String
  
\[\]      - Matches Characters in brackets
\[^ \]    - Matches Characters NOT in brackets
|       - Either Or (e.g. r'(Mr|Ms|Mrs)')
( )     - Group
	
	
**Quantifiers**:
	
\*       - Match 0 or More
+       - Match 1 or More
?       - Match 0 or One
{3}     - Exact Number expected
{3,4} - Range of Numbers (Minimum, Maximum) expected
	
	
**White Space Characters**:

\\n       - new line
\\s       - space
\\t       - tab
\\e       - escape
\\f       - form feed
\\r       - return
  

  
\\       - Escape Character
	
	
IF YOU WANT TO FIND THESE YOU MUST ESCAPE:
. + \* ? \[ \] $ ^ ( ) { } | \\