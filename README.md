xor is a simple cmd-line (modeled after the base64 cmd) encryption utility written in go.


from "xor --help":

```
Usage: xor [OPTION]... [FILE]
Encrypt or decrypt the specified FILE, or standard input, to standard output.

If FILE is not specified, or if FILE is "-", read standard input.

  -d              Decrypt the input
  --key=<secret>  Use the supplied secret as the encryption or decryption key 
                  As many as three "--key=" args can supplied on the command line.
                  By default, xor will attempt to use the value in env var "XOR_KEY".
  -h --help       Display this help and exit
  -v --version    Print the version and exit

Based on the idea of a one-time pad (https://en.wikipedia.org/wiki/One-time_pad),
xor uses a hashing function to generate a pad from a supplied key
(or keys). A unique iv (https://en.wikipedia.org/wiki/Cryptographic_nonce)
is used for each encryption operation.
Please direct inquiries, bug reports, etc. to xor@terrybytes.io.

```

By default, xor will use all the cpu cores available to it. this can be limited by setting GOMAXPROCS to some smaller number. xor can encrypt data steams of any size (apparently) and it's memory use is constant.

Note that the output is binary so be sure to redirect stdout

Example usage:
date | xor --key=123 --key=234 | xor -d --key=234 --key=123


