# go-bmap
> Go version of the [bmap js library](https://github.com/rohenaz/bmap/) for working with OP_RETURN protocols

[![Release](https://img.shields.io/github/release-pre/BitcoinSchema/go-bmap.svg?logo=github&style=flat&v=3)](https://github.com/BitcoinSchema/go-bmap/releases)
[![Build Status](https://travis-ci.com/BitcoinSchema/go-bmap.svg?branch=master&v=3)](https://travis-ci.com/BitcoinSchema/go-bmap)
[![Report](https://goreportcard.com/badge/github.com/BitcoinSchema/go-bmap?style=flat&v=3)](https://goreportcard.com/report/github.com/BitcoinSchema/go-bmap)
[![codecov](https://codecov.io/gh/BitcoinSchema/go-bmap/branch/master/graph/badge.svg?v=3)](https://codecov.io/gh/BitcoinSchema/go-bmap)
[![Go](https://img.shields.io/github/go-mod/go-version/BitcoinSchema/go-bmap?v=3)](https://golang.org/)
[![Sponsor](https://img.shields.io/badge/sponsor-BitcoinSchema-181717.svg?logo=github&style=flat&v=3)](https://github.com/sponsors/BitcoinSchema)
[![Donate](https://img.shields.io/badge/donate-bitcoin-ff9900.svg?logo=bitcoin&style=flat&v=3)](https://gobitcoinsv.com/#sponsor)

<br/>

## Table of Contents
- [Installation](#installation)
- [Documentation](#documentation)
- [Examples & Tests](#examples--tests)
- [Benchmarks](#benchmarks)
- [Code Standards](#code-standards)
- [Usage](#usage)
- [Maintainers](#maintainers)
- [Contributing](#contributing)
- [License](#license)

<br/>

## Installation

**go-bmap** requires a [supported release of Go](https://golang.org/doc/devel/release.html#policy).
```shell script
go get -u github.com/bitcoinschema/go-bmap
```

<br/>

## Documentation
View the generated [documentation](https://pkg.go.dev/github.com/bitcoinschema/go-bmap)

[![GoDoc](https://godoc.org/github.com/bitcoinschema/go-bmap?status.svg&style=flat)](https://pkg.go.dev/github.com/bitcoinschema/go-bmap)

### Features
- [NewFromBob()](bmap.go)
- Supported Protocols:
    - [AIP](https://github.com/bitcoinschema/go-aip)
    - [B](https://github.com/bitcoinschema/go-b)
    - [BAP](https://github.com/bitcoinschema/go-bap)
    - [MAP](https://github.com/bitcoinschema/go-map)

<details>
<summary><strong><code>Package Dependencies</code></strong></summary>
<br/>

- [bitcoinschema/go-aip](https://github.com/bitcoinschema/go-aip)
- [bitcoinschema/go-b](https://github.com/bitcoinschema/go-b)
- [bitcoinschema/go-bap](https://github.com/bitcoinschema/go-bap)
- [bitcoinschema/go-bob](https://github.com/bitcoinschema/go-bob)
- [bitcoinschema/go-map](https://github.com/bitcoinschema/go-map)
</details>

<details>
<summary><strong><code>Library Deployment</code></strong></summary>
<br/>

[goreleaser](https://github.com/goreleaser/goreleaser) for easy binary or library deployment to Github and can be installed via: `brew install goreleaser`.

The [.goreleaser.yml](.goreleaser.yml) file is used to configure [goreleaser](https://github.com/goreleaser/goreleaser).

Use `make release-snap` to create a snapshot version of the release, and finally `make release` to ship to production.
</details>

<details>
<summary><strong><code>Makefile Commands</code></strong></summary>
<br/>

View all `makefile` commands
```shell script
make help
```

List of all current commands:
```text
all                    Runs multiple commands
clean                  Remove previous builds and any test cache data
clean-mods             Remove all the Go mod cache
coverage               Shows the test coverage
godocs                 Sync the latest tag with GoDocs
help                   Show this help message
install                Install the application
install-go             Install the application (Using Native Go)
lint                   Run the Go lint application
release                Full production release (creates release in Github)
release                Runs common.release then runs godocs
release-snap           Test the full release (build binaries)
release-test           Full production test release (everything except deploy)
replace-version        Replaces the version in HTML/JS (pre-deploy)
tag                    Generate a new tag and push (tag version=0.0.0)
tag-remove             Remove a tag if found (tag-remove version=0.0.0)
tag-update             Update an existing tag to current commit (tag-update version=0.0.0)
test                   Runs vet, lint and ALL tests
test-short             Runs vet, lint and tests (excludes integration tests)
test-travis            Runs all tests via Travis (also exports coverage)
test-travis-short      Runs unit tests via Travis (also exports coverage)
uninstall              Uninstall the application (and remove files)
vet                    Run the Go vet application
```
</details>

<br/>

## Examples & Tests
All unit tests and [examples](examples) run via [Travis CI](https://travis-ci.com/bitcoinschema/go-bmap) and uses [Go version 1.15.x](https://golang.org/doc/go1.15). View the [deployment configuration file](.travis.yml).

Run all tests (including integration tests)
```shell script
make test
```

Run tests (excluding integration tests)
```shell script
make test-short
```

<br/>

## Benchmarks
Run the Go benchmarks:
```shell script
make bench
```

<br/>

## Code Standards
Read more about this Go project's [code standards](CODE_STANDARDS.md).

<br/>

## Usage
Checkout all the [examples](examples)!
      
Mongo Insert Example:
```go
bmapData, err := bmap.NewFromString(bobData)

bsonData := bson.M{
  "tx":  bobData.Tx,
  "in":  bobData.In,
  "out": bobData.Out,
  "blk": bobData.Blk,
}

if bmapData.AIP != nil {
  bsonData["AIP"] = bmapData.AIP
}

if bmapData.BAP != nil {
  bsonData["BAP"] = bmapData.BAP
}

if bmapData.MAP != nil {
  bsonData["MAP"] = bmapData.MAP
}

_, err := conn.InsertOne(collectionName, bsonData)
```

<br/>

## Maintainers
| [<img src="https://github.com/rohenaz.png" height="50" alt="MrZ" />](https://github.com/rohenaz) | [<img src="https://github.com/mrz1836.png" height="50" alt="MrZ" />](https://github.com/mrz1836) |
|:---:|:---:|
| [Satchmo](https://github.com/rohenaz) | [MrZ](https://github.com/mrz1836) |

<br/>

## Contributing

View the [contributing guidelines](CONTRIBUTING.md) and follow the [code of conduct](CODE_OF_CONDUCT.md).

### How can I help?
All kinds of contributions are welcome :raised_hands:!
The most basic way to show your support is to star :star2: the project, or to raise issues :speech_balloon:.
You can also support this project by [becoming a sponsor on GitHub](https://github.com/sponsors/BitcoinSchema) :clap:
or by making a [**bitcoin donation**](https://gobitcoinsv.com/#sponsor) to ensure this journey continues indefinitely! :rocket:


### Credits
[Siggi](https://github.com/icellan) for creating [BAP](https://github.com/icellan/bap) :clap:

<br/>

## License

![License](https://img.shields.io/github/license/BitcoinSchema/go-bmap.svg?style=flat&v=3)