xor is a simple cmd-line (modeled after the base64 cmd) encryption utility written in go.


from "xor --help":

```
Usage: xor [OPTION]... [FILE]
Encrypt or decrypt the specified FILE, or standard input, to standard output.

If FILE is not specified, or if FILE is "-", read standard input.

  -d              decrypt the input
  --key=<secret>  use the supplied secret key
                  If a the --key arg is not supplied, xor will attempt to use
                  the value of env var: "XOR_KEY".
  --help          display this help and exit
  --version       output version information and exit

Originally based on the idea of a one-time pad (https://en.wikipedia.org/wiki/One-time_pad),
xor uses a cryptographic hashing function to generate a pad from a supplied key
(or keys). A unique nonce (https://en.wikipedia.org/wiki/Cryptographic_nonce)
is used for each encryption operation.
Please direct inquiries, bug reports, etc. to xor@terrybytes.io.
```

By default, xor will use all the cpu cores available to it. this can be limited by setting GOMAXPROCS to some smaller number. xor can encrypt data steams of any size (apparently) and it's memory use is constant. xor seems to be very similar to the chacha20 cypher. xor also seem to perform pretty well; 1.5s/1G on an 8-core system.

note that the output is binary so be sure to redirect stdout

Example usage:

date | xor --key=123 | xor -d --key=123


