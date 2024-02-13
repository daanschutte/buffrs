<!-- markdownlint-disable-next-line -->
<div align="center">

<img src="https://github.com/helsing-ai/buffrs/assets/37018485/76c51445-b5a6-4f4e-a39c-7de7e31a0613" onerror="this.style.display='none'" />
<br/>

# Buffrs

**Modern protobuf package management**

[![Helsing](https://img.shields.io/badge/helsing-open%20source-black.svg)](https://helsing.ai)
[![Buffrs Crate](https://img.shields.io/crates/v/buffrs.svg)](https://crates.io/crates/buffrs)
[![Buffrs Book](https://img.shields.io/badge/book-latest-blueviolet.svg)](https://helsing-ai.github.io/buffrs)
[![Buffrs Docs](https://img.shields.io/badge/docs-latest-blue.svg)](https://docs.rs/buffrs)

![GitHub Actions Workflow Status](https://img.shields.io/github/actions/workflow/status/helsing-ai/buffrs/nix_ci_mac.yml?logo=nixos&label=mac%20build)
![GitHub Actions Workflow Status](https://img.shields.io/github/actions/workflow/status/helsing-ai/buffrs/nix_ci_ubuntu.yml?logo=nixos&label=ubuntu%20build)


</div>

## Quickstart

```bash,ignore
$ cargo install buffrs
$ buffrs login
$ buffrs init --api
$ buffrs add <dependency>
$ buffrs install
```

Useful resources:

- [The Buffrs Book](https://helsing-ai.github.io/buffrs)
- [Crate Documentation](https://docs.rs/buffrs)
- [Announcement Post](https://blog.helsing.ai/buffrs-a-package-manager-for-protocol-buffers-1-2-aaf7c00153d2)
- `buffrs help`

## Synopsis

```text,ignore
Modern protobuf package management

Usage: buffrs <COMMAND>

Commands:
  init       Initializes a buffrs setup
  lint       Check rule violations for this package
  add        Adds dependencies to a manifest file
  remove     Removes dependencies from a manifest file
  package    Exports the current package into a distributable tgz archive
  publish    Packages and uploads this api to the registry
  install    Installs dependencies
  uninstall  Uninstalls dependencies
  list       Lists all protobuf files managed by Buffrs to stdout
  generate   Generate code from installed buffrs packages
  login      Logs you in for a registry
  logout     Logs you out from a registry
  help       Print this message or the help of the given subcommand(s)

Options:
  -h, --help     Print help
  -V, --version  Print version
```

## Motivation

Protocol buffers are agreeably a great way to define fully typed,
language-independent API schemas with strong backward compatibility guarantees.
They offer a neat experience for API consumers through generated bindings. *The
biggest problem associated with Protocol Buffers is their distribution.*

- How do you consume the raw protobuf files of one project reliably in another
  one?
- How do you prevent transitive dependencies?
- How do you publish to a unified registry with package format across
  languages?

One obvious way is to generate code bindings in the repository containing the
Protocol Buffers and publish the generated bindings, but this is associated
with problems such as language lock-in. You need to proactively publish
bindings for any possible language your API consumers may use. Also, in
strongly typed languages like Rust, it is hard to extend the behavior of
generated code in consuming projects due to _the orphan rule_. Summing up: this
approach works somehow but hurts frequently.

This is where Buffrs comes in: Buffrs solves this by defining a strict,
package-based distribution mechanism and treats Protocol Buffers as a
first-class citizen.

*This allows you to publish Buffrs packages to a registry and properly depend
on them in other projects.*


## Roadmap

- [x] Support project manifests and dependency declaration
- [x] Support package distribution via Artifactory
- [x] Support tonic as code generation backend
- [x] Support protoc as code generation backend
- [ ] Implement `buffrs-registry`, a self-hostable, S3-based registry.
- [ ] Supply tooling around Protocol Buffers, such as bindgen, linting, validation and
  formatting.
