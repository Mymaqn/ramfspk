# ramfspk
Tool for easier creation of ramfs filesystems for Linux (cpio)

## Why this tool?
I get tired of remembering all the cpio commands for packing linux initramfs'. I just want a simple tool where I can specify directories and it packs it for me

This is not some "fancy" tool. It's a python script which uses subprocess to call cpio and find after changing directory a couple of times.

## Dependencies
`python3`
`cpio`
`find`
If you somehow do not already have these tools, on debian based distributions you can run the following to install them
```
sudo apt install cpio findutils python3
``` 

## How it works
The tool is built around a "tar like" approach.

The first file given is the output archive name and subsequent files and folders are the items to pack.

If a folder is given, the folder becomes the equivalent of the root directory and the foldername is omitted.

Eg. if you have a folder structure which looks like this:

```
to_pack
├── file1
└── file2
```

and you run your command like this:
```sh
ramfspk initramfs.cpio to_pack
```

The cpio archive structure will be like this:
```
file1
file2
```

If a file (not a directory) is provided to ramfspk, the file will  be placed in the root of the cpio archive.

## Usage examples

```
ramfspk initramfs.cpio dir1 dir2 file1 file2 dir3
```

```
ramfspk initramfs.cpio dir1
```

```
ramfspk initramfs.cpio dir1 file1
```