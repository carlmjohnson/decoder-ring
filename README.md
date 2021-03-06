# decoder-ring [![GoDoc](https://godoc.org/github.com/carlmjohnson/decoder-ring?status.svg)](https://godoc.org/github.com/carlmjohnson/decoder-ring) [![Go Report Card](https://goreportcard.com/badge/github.com/carlmjohnson/decoder-ring)](https://goreportcard.com/report/github.com/carlmjohnson/decoder-ring)

Decoder-ring is a CLI tool for decoding/encoding from common formats.

## Installation

First install [Go](http://golang.org).

If you just want to install the binary to your current directory and don't care about the source code, run

```bash
GOBIN="$(pwd)" go install github.com/carlmjohnson/decoder-ring@latest
```


## Screenshots
```bash
$ decoder-ring -h
Usage of decoder-ring v0.21.1:

    decoder-ring [-encode] <MODE>

MODE choices are base32, base32-crockford, base32-hex, base64, base64-url,
codepoint*, go, hex, hex-extended*, html, json, qp, rot13, url-path, url-query,
or an IANA encoding name. Modes marked with * are encode only.

As a convenience feature, when this executable is symlinked as 'encoder-ring', -e defaults to true.

  -e    shortcut for -encode
  -emit
        emit trailing newline (UTF-8) (default true)
  -encode
        encode rather than decode
  -s    shortcut for -strip (default true)
  -strip
        strip trailing newlines from input (default true)
  -t    shortcut for -emit (default true)


$ echo 'Hello, World!' | decoder-ring -e base64
SGVsbG8sIFdvcmxkIQ==

$ echo SGVsbG8sIFdvcmxkIQ== | decoder-ring base64
Hello, World!

$ echo 'Hello, World!' | decoder-ring rot13
Uryyb, Jbeyq!

$ echo 'Hello, World!' | decoder-ring -e ebcdic-cp-us | decoder-ring -e hex-extended
00000000  c8 85 93 93 96 6b 40 e6  96 99 93 84 5a           |.....k@.....Z|

$ echo 'Hello, こんにちはワールド!' | decoder-ring -e codepoint
U+0048  H       LATIN CAPITAL LETTER H
U+0065  e       LATIN SMALL LETTER E
U+006C  l       LATIN SMALL LETTER L
U+006C  l       LATIN SMALL LETTER L
U+006F  o       LATIN SMALL LETTER O
U+002C  ,       COMMA
U+0020          SPACE
U+3053  こ      HIRAGANA LETTER KO
U+3093  ん      HIRAGANA LETTER N
U+306B  に      HIRAGANA LETTER NI
U+3061  ち      HIRAGANA LETTER TI
U+306F  は      HIRAGANA LETTER HA
U+30EF  ワ      KATAKANA LETTER WA
U+30FC  ー      KATAKANA-HIRAGANA PROLONGED SOUND MARK
U+30EB  ル      KATAKANA LETTER RU
U+30C9  ド      KATAKANA LETTER DO
U+0021  !       EXCLAMATION MARK
```

## Endorsements

> Useful

— [barryzxb](https://www.reddit.com/r/golang/comments/86ewvx/decoderring_a_cli_tool_for_decodingencoding_from/dw4vmdy/)
