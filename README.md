# alpine-pkg-leveldb

[![CircleCI](https://img.shields.io/circleci/project/sgerrand/alpine-pkg-leveldb/master.svg)](https://circleci.com/gh/sgerrand/alpine-pkg-leveldb)

This is [LevelDB][leveldb] as an Alpine Linux package.

## Releases

See the [releases page][releases] for the latest download links.

## Installing

The current installation method for these packages is to pull them in using
`wget` or `curl` and install the local file with `apk`:

```
apk --no-cache add ca-certificates
wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://raw.githubusercontent.com/sgerrand/alpine-pkg-leveldb/master/sgerrand.rsa.pub
wget https://github.com/sgerrand/alpine-pkg-leveldb/releases/download/1.18-r0/leveldb-1.18-r0.apk
apk --allow-untrusted add leveldb-1.18-r0.apk
```

[leveldb]: http://leveldb.org
[releases]: https://github.com/sgerrand/alpine-pkg-leveldb/releases/
