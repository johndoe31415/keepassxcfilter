# keepassxcfilter
[KeepassXC](https://keepassxc.org/) is a nice password manager for all kinds of
platforms which also allows adding custom data (e.g., specific tags) to
individual password entries. keepassxcfilter is a small utility that reads a
database and only exports those entries in a separate database which have
specific tags set. The purpose is to have one main master database, but flag
down specific passwords as "export" passwords that are distributed as a
separate file.

## Dependencies
keepassxcfilter requires at least KeepassXC 2.5.0. It uses Python3.

## Usage
Usage is pretty straightforward:

```
usage: keepassxcfilter [-h] [-t tag] [-f] [--tempdir path]
                       [--keepass-cli-binary path]
                       infile outfile

Filter a KeepassXC database.

positional arguments:
  infile                Input KeepassXC database file
  outfile               Output KeepassXC database file

optional arguments:
  -h, --help            show this help message and exit
  -t tag, --tag tag     Include only those entries in the filtered database
                        which have the tag present. Can be specified multiple
                        times.
  -f, --force           Overwrite output filename if it exists.
  --tempdir path        Temporary directory in which unencrypted files will
                        need to be stored. Ideally on a drive that is in-
                        memory only (ramdisk or tmpfs). Defaults to /dev/shm.
  --keepass-cli-binary path
                        Name (and maybe path) of the KeepassXC CLI binary.
                        Defaults to keepassxc-cli.
```

Let's say you've created export tags that you called "exportme" for specific
entries. Then you can simply:

```
$ ./keepassxcfilter -t exportme input_database.kdbx output_database_kdbx
Database passphrase: 
Exported 14 of 325 entries.
```

## License
GNU GPL-3.
