# fig parser

Hacky scripts to investigate the `.fig` file format.

## Format

There are two formats of `.fig` file floating around. The older one has: 4 sections:
- Header
- kiwib schema (zlib deflated)
- data (zlib deflated)
- PNG thumbnail

Each section (except the header) consist of 2 fields:
- 4 byte length (little endian)
- data (length bytes)

The newer format is just a zip file containing:
- canvas.fig - A fig file of the older format except without the trailing PNG thumbnail
- thumbnail.png - The thumbnail that used to be embedded in the .fig
- meta.json - A bunch of boring metadata
- images/ - A folder that I've never seen populated but presumably contains... images

## Installing
You'll need a relatively recent ruby (e.g. 2.7) and node + npm.

- Firstly install npm packages with `npm install`.
- Secondly, go grab a .fig file from figma
- Thirdly, run `./figunpack <file>`

The unpacked contents will be output to a directory called `<file>.out/`.

In addition to unpacking and inflating the file contents we convert the kiwi encoded data in to JSON and write this to `data.json`. If you're only interested in the figma data itself, this is the interesting bit.
