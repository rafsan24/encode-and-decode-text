# Encoding and Decoding Text

## Introduction

The goal of this project is to learn about UNIX filters, as well as get some insight into ASCII characters and abstract C programming.

I have created an encoding program and a decoding program. Both of these programs behave as UNIX filters; they read character input from standard input (stdin), and write character output to standard output (stdout). Any messages designed for human consumption are written to standard error (stderr). That allows us to use UNIX standard input and output redirection, and we can create invocations such as:

```bash
>./encode key <raw.txt >encoded.txt # Read input from raw.txt and write encoded output to encoded.txt
>./decode key <encoded.txt # Read input from encoded.txt and write results to the screen
>/.encode key <raw.txt | ./decode key # Read input from raw.txt, encode it, decode it, and write results to the screen
```

The basic ground rules are as follows:

1. My algorithms must read ASCII text as input, and produce ASCII text as output.

2. My algorithms should accept a key, an ASCII blank delimited "word" as a parameter. Different keys should produce different enciphered text. We are assuming that the key is known by both the sender (encipherer) and receiver (decipherer) of the message.

3. No command line parameters other than the key command line parameter should be required to run either encode or decode.

4. The output of the encode program must not match the input. The output of the encode program should not indicate the original text message.

5. If I encipher input text with a specific key, and then I must use that same key to decipher the result, the result should match the original input text, where "matching" is defined as follows:

   1. Alphabetic characters must match, but the case (upper case or lower case) does not need to be maintained. For example, if the input text is "Testing", then the output result can be "testing" or "TESTING" or "tESTING".
   2. Any white-space character or string of characters, such as blanks, tabs, or newlines, should match.
   3. Any numeric ASCII characters such as '1' or '7' should match.
   4. Any character that is not alphabetic, white space, or numeric, such a punctuation or symbols may match, or may be translated to '*'

6. If I encipher input text with a specific key, and then I must use a *different* key to decipher the result, the results should **not** match the original input text.
