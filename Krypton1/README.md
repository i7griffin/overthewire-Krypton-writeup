tr command:
bashecho "Hello World" | tr 'A-Za-z' 'N-ZA-Mn-za-m'
tr (short for "translate") is a simple Unix utility that performs character-by-character substitution on text from standard input. It takes two character sets as arguments and maps each character in the first set to the character in the same position in the second set.
Breaking down 'A-Za-z' and 'N-ZA-Mn-za-m':

A-Za-z is the source alphabet: uppercase A through Z, followed by lowercase a through z (52 characters total).
N-ZA-Mn-za-m is the rotated target alphabet, built in four pieces: N-Z (uppercase N through Z, 13 letters), A-M (uppercase A through M, 13 letters), n-z (lowercase n through z, 13 letters), a-m (lowercase a through m, 13 letters).

So tr walks through the source set position by position and substitutes the matching character from the target set. Position 1 of the source (A) maps to position 1 of the target (N), position 2 (B) maps to O, and so on, wrapping around after Z/M back to the start. Since the alphabet is split exactly into two 13-letter halves and shifted, applying the same command twice returns the original text.
tr only works on single characters mapped one-to-one; it has no concept of words, case-sensitivity logic, or anything beyond direct substitution, which is exactly why ROT13 (a simple fixed substitution) is such a natural fit for it.
perl command:
bashecho "Hello World" | perl -pe 'tr/A-Za-z/N-ZA-Mn-za-m/'
This uses Perl's own built-in tr/// operator, which works almost identically in concept to the Unix tr utility (translate characters from one set to another) but is part of Perl's syntax rather than a separate program. The flags before it control how Perl processes the input:

-p tells Perl to wrap your code in an implicit loop that reads each line from input, runs your code on it, and prints the result automatically. This mimics how a typical shell text filter behaves.
-e lets you supply the Perl code directly on the command line as a string, rather than writing a separate .pl script file.
tr/A-Za-z/N-ZA-Mn-za-m/ is Perl's transliteration operator, syntactically using slashes instead of tr's quoted arguments, but performing the exact same character-range mapping as the standalone tr command.

The practical difference between the two: the Unix tr utility is simpler and more universally available with minimal syntax, while Perl's tr/// is useful if you're already writing a larger Perl script and want ROT13 as one step in a bigger text-processing pipeline, since you get access to Perl's full language (regex, variables, control flow) around it
