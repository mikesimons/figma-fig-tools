# fig parser

Hacky scripts to investigate the `.fig` file format.

## Format

`.fig` files have 4 sections:
- Header
- kiwib schema (zlib deflated)
- data (zlib deflated)
- PNG thumbnail

Each section (except the header) consist of 2 fields:
- 4 byte length (little endian)
- data (length bytes)

## Installing
You'll need a relatively recent ruby (e.g. 2.7) and node + npm.

- Firstly install npm packages with `npm install`.
- Secondly, go grab a .fig file from figma
- Thirdly, run `./figunpack <file>`

The unpacked contents will be output to a directory called `<file>.out/`.

In addition to unpacking and inflating the file contents we convert the kiwi encoded data in to JSON and write this to `data.json`. If you're only interested in the figma data itself, this is the interesting bit.
