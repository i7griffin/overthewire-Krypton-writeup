The base64 command encodes binary data into ASCII text or decodes it back. Syntax and behavior differ slightly between GNU/Linux and macOS/BSD versions, so I'll cover both.
Basic syntax (GNU/Linux, coreutils):
bashbase64 [OPTION]... [FILE]
If no file is given, it reads from standard input.
Core flags (GNU):

-d, --decode — decode the base64 input back to binary/original data
-i, --ignore-garbage — when decoding, ignore non-alphabet characters instead of erroring out
-w N, --wrap=N — wrap encoded lines after N characters (default is 76; use -w 0 to disable wrapping and output on one line)
--help — show usage info
--version — show version

Common usage examples:
Encode a string:
bashecho -n "Hello World" | base64
SGVsbG8gV29ybGQ=
(-n on echo avoids encoding a trailing newline)
Encode a file:
bashbase64 myfile.txt > myfile.b64
Decode a string:
bashecho "SGVsbG8gV29ybGQ=" | base64 -d
Decode a file:
bashbase64 -d myfile.b64 > myfile.txt
