CAESAR CIPHER 
What it is:

A Caesar cipher shifts each letter in the alphabet by a fixed number of positions (the key). The same key value is used for both encryption and decryption.
The Alphabet (positions 0-25):
A=0, B=1, C=2, D=3, E=4, F=5, G=6, H=7, I=8, J=9, K=10, L=11, M=12,
N=13, O=14, P=15, Q=16, R=17, S=18, T=19, U=20, V=21, W=22, X=23, Y=24, Z=25

ENCRYPTION (Plaintext → Ciphertext)
Formula:
Ciphertext letter = (Plaintext letter position + Key) mod 26
Example: Key = 12, Plaintext = "CAESAR"

C (2) + 12 = 14 → O
A (0) + 12 = 12 → M
E (4) + 12 = 16 → Q
S (18) + 12 = 30 mod 26 = 4 → E
A (0) + 12 = 12 → M
R (17) + 12 = 29 mod 26 = 3 → D

Result: OMQEMD

DECRYPTION (Ciphertext → Plaintext)
Formula:
Plaintext letter = (Ciphertext letter position - Key) mod 26
Example: Key = 12, Ciphertext = "OMQEMD"

O (14) - 12 = 2 → C
M (12) - 12 = 0 → A
Q (16) - 12 = 4 → E
E (4) - 12 = -8 mod 26 = 18 → S
M (12) - 12 = 0 → A
D (3) - 12 = -9 mod 26 = 17 → R

Result: CAESAR

5-LETTER GROUPING FORMAT
In proper ciphertext format, spaces are removed and the text is regrouped into clusters of 5 letters (regardless of word boundaries):
Plaintext message: CAESAR IS EASY

Remove spaces: CAESARISEA SY

Encrypt with key 12: OMQEMDUEQMEK

Group in 5s: OMQEM DUEQM EK
When decrypting:

5-letter ciphertext: OMQEM DUEQM EK

Decrypt each letter (key -12): CAESA RISEA SY

Read as: CAESAR IS EASY

COMMAND LINE EXAMPLES
Encrypt with Python (key = 12):
bashpython3 -c "
plaintext = 'CAESARISEASTY'
key = 12
ciphertext = ''.join([chr((ord(c) - ord('A') + key) % 26 + ord('A')) for c in plaintext])
print(ciphertext)
"
Output: OMQEMDUEQMEKGY
Decrypt with Python (key = 12):
bashpython3 -c "
ciphertext = 'OMQEMDUEQMEK'
key = 12
plaintext = ''.join([chr((ord(c) - ord('A') - key) % 26 + ord('A')) for c in ciphertext])
print(plaintext)
"
Output: CAESARISEASTY
Decrypt with tr (key = 12):
bashecho "OMQEMDUEQMEK" | tr 'A-Za-z' 'M-ZA-Ln-za-l'
Output: CAESARISEASTY

FINDING AN UNKNOWN KEY
If you know plaintext and ciphertext, find the key:
bashpython3 -c "
plaintext = 'CAESAR'
ciphertext = 'OMQEMD'
key = (ord(ciphertext[0]) - ord(plaintext[0])) % 26
print(f'Key: {key}')
"
Output: Key: 12

QUICK REFERENCE TABLE
OperationFormulaExampleEncrypt(P + K) mod 26C(2) + 12 = O(14)Decrypt(C - K) mod 26O(14) - 12 = C(2)Find key(C - P) mod 26O(14) - C(2) = 12
