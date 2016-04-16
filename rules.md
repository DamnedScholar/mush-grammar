These are general guidelines for me in making this grammar and also probably relevant to an end-user. They regard the general structure of MUSHcode and patterns in its syntax.

* "&" when used in an attribute is always at the start of a line. Conversely, "&" at the start of a line is always part of an attribute. If there's a ";" at the end of the line before that, the user should be alerted. It does occur in the middle of text, so caution should be taken in processing. It might end up at the head of some text that gets split off in demuxification, but then it should be after tabs.
* "@" at the start of the line is always a new command unless it is preceded by ";", then it is part of a command list.
* "think" at the start of the line is always a new command unless it is preceded by ";", then it is part of a command list.
* "@@" at the start of the line is a comment. "@@()" is a function. Some users might place @@ comments after tabs. This is probably bad practice, but should be supported.
* No function is going to be at the start of a line.
* "|" and "~" are commonly used as delimiters.
* "\" and % are both escape characters. They can escape each other. Inside functions that run through the parser, multiple escape characters may be needed to preserve colors or sequences that are supposed to be displayed literally. "s(s(%cmYar%cn))" will cut out the colors; they have to be escaped so that the outermost s() can process them.
* List of functions that invoke the parser: s(), parse(), get_eval(), iter(), u(), eval()
  * Should get verification about this from the MUS hivemind.
