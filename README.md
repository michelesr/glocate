# glocate

`glocate` is a minimalist, simple, Bash implementation of the `locate` utility
for finding files using a filename database, consisting of:

- `find` for db generation
- `gzip` for db compression
- `zcat` for on the fly decompression
- `grep` for searching filenames inside the db

The idea came from [this
article](http://jvns.ca/blog/2015/03/05/how-the-locate-command-works-and-lets-rewrite-it-in-one-minute/)
by *Julia Evans*.

## Installation

To load the utility, source the `glocate` file:

```
$ source glocate
```

Add the line to your `.bashrc`, `.zshrc`, `.bash_profile` or `.zprofile` to make
the script available every time.

## Configuration

Configuration is performed by editing `glocate` script.

### Database file

Set the database filename in the `DB_FILE` variable:

```
DB='~/.mydb'
```

### Compression

The `gzip` and `zcat` commands are used to perform compression and decompression
of the database file.

You can change them with your preferred tools, for example `xz` and `xzcat`. To
disable compression, you can replace both the commands with `cat`.

## Usage

### Generate the database

To generate the database:

```
$ updatedb
```
This will use `sudo` internally, because superuser privileges are required in
order to generate a complete list.

You can use `updatedb` to recreate the db when is obsolete.

### Search files

To search files:

```
$ locate [OPTIONS] PATTERN
```

`OPTIONS` and `PATTERN` syntax are those of `grep` command.
