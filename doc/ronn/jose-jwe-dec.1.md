jose-jwe-dec(1) -- Decrypts a JWE using the supplied JWKs
=========================================================

## SYNOPSIS

`jose jwe dec` -i JWE [-I CT] -k JWK [-p] [-O PT]

## OVERVIEW

The `jose jwe dec` command decrypts a JWE using one or more JWK (`-k`) or
password (`-p`). Decryption succeeds if any key is able to perform decryption.

If the JWE is a detached JWE, meaning that the ciphertext is stored in
binary form external to the JWE itself, the ciphertext can be loaded using
the `-I` parameter.

Please note that, when specifying the `-O` option to output the plaintext,
plaintext output begins before ciphertext validation. Therefore,
you must check the return value of the command before using the data.

## OPTIONS

* `-i` _JSON_, `--input`=_JSON_ :
  Parse JWE from JSON

* `-i` _FILE_, `--input`=_FILE_ :
  Read JWE from FILE

* `-i` -, `--input`=- :
  Read JWE from standard input

* `-I` _FILE_, `--detached`=_FILE_ :
  Read decoded ciphertext from FILE

* `-I` -, `--detached`=- :
  Read decoded ciphertext from standard input

* `-p`, `--password` :
  Prompt for a decryption password, if necessary

* `-k` _FILE_, `--key`=_FILE_ :
  Read JWK(Set) from FILE

* `-k` -, `--key=-` :
  Read JWK(Set) from standard input

* `-O` _JSON_, `--detach`=_JSON_ :
  Parse JWE from JSON

* `-O` _FILE_, `--detach`=_FILE_ :
  Read JWE from FILE

* `-O` -, `--detach`=- :
  Read JWE from standard input

## EXAMPLES

Decrypt a JWE with a JWK:

    $ jose jwe dec -i msg.jwe -k rsa.key -O msg.txt

Decrypt a JWE with a password:

    $ jose jwe dec -i msg.jwe -p -O msg.txt
    Please enter decryption password:

Decrypt a JWE with either of two JWKs:

    $ jose jwe dec -i msg.jwe -k ec.jwk -k rsa.jwk -O msg.txt

## AUTHOR

Nathaniel McCallum &lt;npmccallum@redhat.com&gt;

## SEE ALSO

`jose-jwe-enc`(1),
`jose-jwe-fmt`(1)
