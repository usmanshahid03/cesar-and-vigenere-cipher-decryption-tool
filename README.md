
Cipher Decryption Suite
Two C++ programs that decrypt Caesar and Vigenère ciphers using brute-force key search and dictionary-based validation.

Programs
1. Caesar Cipher Decryptor (cesar_cipher.txt)
Decrypts text encrypted with the Caesar cipher by trying all 26 possible shift keys and checking the result against a word dictionary.
How it works:

Accepts a single ciphertext string from the user
Iterates through all 26 shift values (0–25)
For each key, decrypts the text and checks every word against wordlist.txt
Returns the first decryption where all words are valid dictionary entries

Limitations:

Only works for single-word or simple multi-word inputs
Stops at the first valid match, which may not always be the intended plaintext


2. Vigenère Cipher Decryptor (vigenere_cipher.txt)
Decrypts text encrypted with the Vigenère cipher by testing all 26 single-character keys and scoring each result for dictionary accuracy.
How it works:

Accepts a ciphertext string (spaces removed, converted to uppercase internally)
Tries each letter A–Z as a repeating single-character key
Scores each decryption by the proportion of words found in wordlist.txt
Returns the decryption with the highest accuracy score

Limitations:

Only supports single-character keys (not full keyword-based Vigenère)
Accuracy depends heavily on the quality and size of the dictionary file


Requirements

Compiler: g++ with C++11 or later
OS: Linux / Unix (uses sleep() from <unistd.h>)
Dictionary: A file named wordlist.txt in the same directory as the executable, with one word per line


Compilation
bash# Caesar Cipher
g++ -o cesar_decrypt cesar_cipher.cpp

# Vigenère Cipher
g++ -o vigenere_decrypt vigenere_cipher.cpp

Usage
bash# Run Caesar decryptor
./cesar_decrypt

# Run Vigenère decryptor
./vigenere_decrypt
Each program will prompt you to enter the ciphertext and display the decrypted plaintext along with the key used.

Dictionary File
Both programs require a wordlist.txt file. You can use any standard English word list. A common source is the Unix system wordlist:
bashcp /usr/share/dict/words wordlist.txt

Notes

The Caesar program is case-preserving; the Vigenère program converts all input to uppercase before processing.
Neither program currently supports multi-word Vigenère keys or keys longer than one character for brute-force purposes.
The sleep(5) calls are cosmetic delays simulating a brute-force wait.
