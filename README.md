# Description

mkhash command generate a hash of specified field string, and insert after the field.
In direct mode, it doesn't keep the original string.
If the target filename is ommited, standard input will be used.

Supported hash type: md5 sha1 sha224 sha256 sha384 sha512

# Usage

mkhash [-d] type field [file]
    type    hash type
    field   target field number
    file    target filename
    -d      direct mode

# Examples

```
$ cat sample.txt
aaa hello xxx
bbb hello yyy
ccc piyo xxx
ddd hoge zzz

$ mkhash sha256 2 sample.txt
aaa hello 2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824 xxx
bbb hello 2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824 yyy
ccc piyo 0483e038b18bf5d4a63caa763ca7875e16e4d7ea8fc2605ee5154a5ff6a13761 xxx
ddd hoge ecb666d778725ec97307044d642bf4d160aabb76f56c0069c71ea25b1e926825 zzz

$ mkhash -d sha256 2 sample.txt
aaa 2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824 xxx
bbb 2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824 yyy
ccc 0483e038b18bf5d4a63caa763ca7875e16e4d7ea8fc2605ee5154a5ff6a13761 xxx
ddd ecb666d778725ec97307044d642bf4d160aabb76f56c0069c71ea25b1e926825 zzz

$ cat sample.txt | mkhash md5 3
aaa hello xxx f561aaf6ef0bf14d4208bb46a4ccb3ad
bbb hello yyy f0a4058fd33489695d53df156b77c724
ccc piyo xxx f561aaf6ef0bf14d4208bb46a4ccb3ad
ddd hoge zzz f3abb86bd34cf4d52698f14c0da1dc60
```
