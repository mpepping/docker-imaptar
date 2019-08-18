# imaptar

[imaptar](https://github.com/XS4ALL/imaptar/) is a utility to dump an entire IMAP-mailbox, INBOX and all folders, in maildir format to a tar file.

## Usage

```bash
Usage: imaptar <flags>

Flags:
    -s, --server <name>   IMAPS server name
    -u, --user <name>     username
    -t, --tar <file>      tar output filename

Optional flags:
    -p, --port <port>     IMAPS server port (default 993)
    -P, --pass <pass>     password
    -E, --envpass VAR     get password from environment var $VAR
    -z, --gzip            compress the output
```

If you do not supply the -P or -E option, you will be prompted
for the password.

## Example

To run `imaptar` and write a `.tgz` file to a local backup directory:

```bash
export IMAPPASS="foo"
docker run -ti --rm -e IMAPPASS -v $PWD/backup:/backup mpepping/imaptar \
  -s imap.xs4all.nl -u myuser -E IMAPPASS -z -t /backup/maildir.tar.gz
```

## BUGS

Only works on IMAP servers where "/" is the folder seperator.

## References

* <https://github.com/XS4ALL/imaptar/>
* <https://hub.docker.com/mpepping/imaptar>
* <https://github.com/mpepping/docker-imaptar>
