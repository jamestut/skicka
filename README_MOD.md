# Modifications Done to Skicka

## ls

For `ls` in `skicka`, an option `-s` has been added. This option must be used in conjunction with either `-l` or `-ll` to be activated. If this option is invoked, `ls` will print in the following format:

```
<permstring> <filesize> <md5> <timestamp> <filename>	
```

Where:

- `<permstring>`
  Unix-style permission string (`drwxrwxrwx`).
- `<filesize>`
  File size of the file, always in bytes. 0 if file is a directory or not a regular file.
- `<md5>`
  The MD5 of the file (or all `-` if not available).
- `<timestamp>`
  Local timestamp of the object in RFC3339 format.
- `<filename>`
  Name of the object. No trailing `/` is added even if the object is a directory.

## download

The `-use-file-list` option has been added. If this option is specified for the `download` command, then the usage of the command becomes:

```
skicka download -use-file-list [-ignore-times] [-dry-run] file_list local_path
```

Where:

- `file_list`
  A text file containing list of files in Drive to be downloaded, separated by newline, relative to the root of the Drive's directory.
- `local_path`
  The folder to store the downloaded files.

Only regular files can be specified inside `file_list`. The specified file must not be a multi version file or Google Apps file.

The file will be downloaded with the full directory hierarchy with respect to the root folder of the Drive inside `local_path`.