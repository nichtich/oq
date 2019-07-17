# oq

[![Built with Crystal](https://img.shields.io/badge/built%20with-crystal-000000.svg?style=flat-square)](https://crystal-lang.org/)
[![Build Status](https://travis-ci.org/Blacksmoke16/oq.svg?branch=master)](https://travis-ci.org/Blacksmoke16/oq)
[![Latest release](https://img.shields.io/github/release/Blacksmoke16/oq.svg?style=flat-square)](https://github.com/Blacksmoke16/oq/releases)
[![oq](https://snapcraft.io/oq/badge.svg)](https://snapcraft.io/oq)

A performant, portable `jq` wrapper thats facilitates the consumption and output of formats other than JSON; using `jq` filters to transform the data.

* Compiles to a single binary for easy portability.
* Performant, similar performance with JSON data compared to `jq`.  Slightly longer execution time when going to/from a non-JSON format.  

## Installation

### Linux via `snap`:

For more on installing & using `snap` with your Linux distribution, see the [official documentation](https://docs.snapcraft.io/installing-snapd).

```bash
snap install oq
```

### MacOS: (Soon)

```bash
brew install oq
```

### From Source:

If building from source, `jq` will need to be installed separately. Installation instructions can be found in the [official documentation](https://stedolan.github.io/jq/).

Requires Crystal to be installed, see the [installation documentation](https://crystal-lang.org/reference/installation/).

```bash
git clone https://github.com/Blacksmoke16/oq.git
cd oq/
shards build --production
```

The built binary will be available as `./bin/oq`.  This can be relocated elsewhere on your machine; be sure it is in your `PATH` to access it as `oq`.

## Usage

### CLI

Use the `oq` binary, with a few optional custom arguments.  All other arguments get passed to `jq`.

```bash
Usage: oq [--help] [oq-arguments] [jq-arguments] jq_filter [file [files...]]
    --help                          Show this help message.
    -i FORMAT, --input FORMAT       Format of the input data. Supported formats: json, yaml.
    -o FORMAT, --output FORMAT      Format of the output data. Supported formats: json, yaml, xml.
    --xml-root ROOT                 Name of the root XML element if converting to XML.
    --indent NUMBER                 Use the given number of spaces for indentation (JSON/XML only).
```

### Serialization

Crystal applications can `require "oq/to_xml"` in order to use the `#to_xml` method to serialize objects to XML.

```crystal
require "oq/to_xml"

hash = {"name": "Jim"}

puts hash.to_xml
# <?xml version="1.0" encoding="UTF-8"?>
# <root>
#   <name>Jim</name>
# </root>
```

## Roadmap

Plans for `1.0.0`:

* XML input format
* Address bugs/issues that arise
* Small feature requests
* Possibly additional formats

## Contributing

1. Fork it (<https://github.com/Blacksmoke16/oq/fork>)
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request

## Contributors

- [Blacksmoke16](https://github.com/Blacksmoke16) Blacksmoke16 - creator, maintainer
- [sprngr](https://github.com/sprngr) Michael Springer - contributor
