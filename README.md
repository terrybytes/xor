xor is a simple cmd-line encryption utility written in go.


from "xor --help":

```
Usage: xor [OPTION]... [FILE]
Encrypt or decrypt the specified FILE, or standard input, to standard output.

If FILE is not specified, or if FILE is "-", read standard input.

  -d              decrypt the input
  --key=<secret>  use the supplied secret key
                  If not supplied, xor will attempt to use the env var: "XOR_KEY".
                  Note more than one "--key=" arg can supplied on the command
                  line and their ordering is not significant.
  -h --help       display this help and exit
  -v --version    output version information and exit

Based on the idea of a one-time pad (https://en.wikipedia.org/wiki/One-time_pad),
xor uses a hashing function to generate a pad from a supplied key
(or keys). A unique nonce (https://en.wikipedia.org/wiki/Cryptographic_nonce)
is used for each encryption operation.
Please direct inquiries, bug reports, etc. to xor@terrybytes.io.

```


note that the output is binary so be sure to redirect stdout

Example usage:

date | xor --key=123 | xor -d --key=123


