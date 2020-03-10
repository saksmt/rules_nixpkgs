# Change Log

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/).

## [Unreleased]

[Unreleased]: https://github.com/tweag/rules_nixpkgs/compare/v0.6.0...HEAD

### Added

- Define `rules_nixpkgs_dependencies` in `//nixpkgs:repositories.bzl`.
- Define `nixpkgs_go_configure` in `//nixpkgs:toolchains/go.bzl`

## [0.6.0] - 2019-11-14

[0.6.0]: https://github.com/tweag/rules_nixpkgs/compare/v0.5.2...0.6.0

### Added

- Check `nix_file_deps` and fail on undeclared dependencies (breaking change).
  See [#76][#76] and [#86][#86].
- Define a `nixpkgs` platform constraint. See [#97][#97].
- Define `nixpkgs_python_configure`. See [#97][#97].
- Define `nixpkgs_sh_posix_configure` to generate [`rules_sh`][rules_sh] POSIX
  toolchain. See [#95].

[#76]: https://github.com/tweag/rules_nixpkgs/pull/76
[#86]: https://github.com/tweag/rules_nixpkgs/pull/86
[#97]: https://github.com/tweag/rules_nixpkgs/pull/97
[#95]: https://github.com/tweag/rules_nixpkgs/pull/95
[rules_sh]: https://github.com/tweag/rules_sh

### Changed

- Hide Nix output, following Bazel best practices for a quiet build.
- Disable implicit `nixpkgs` configuration loading (breaking change).
  See [#83](https://github.com/tweag/rules_nixpkgs/pull/83).

### Fixed

- Improve distributed caching by not leaking user specific Bazel cache
  directory, see [#67](https://github.com/tweag/rules_nixpkgs/pull/67).

## [0.5.2] - 2019-01-28

### Added
- `nixpkgs_package` now has a new optional argument `fail_not_supported`
  allowing the rule to _not_ fail on Windows (when set to `False`)
- `nixpkgs_cc_configure` now has a new optional argument `nixopts` which
  propagates extra arguments to the `nix-build` calls.

### Fixed
- The `nixpkgs_package` is now a no-op on non nixpkgs-supported platforms
  instead of throwing an error.

## [0.5.1] - 2018-12-18

### Changed

- `nixpkgs_package` now has a new optional argument `nixopts`
  allowing to pass extra arguments to the `nix-build` calls

### Fixed

- The various `nix_*` rules are now only triggered when one of their dependency
  has changed and not each time the `WORKSPACE` is modified
- The `nixpkgs_cc_configure` macro is now much faster
- `nixpkgs_cc_configure` is now a no-op on non nixpkgs-supported platforms
  instead of throwing an error
- The `lib` filegroup provided in the default `BUILD` file for
  `nixpkgs_package` now also works on MacOS

## [0.4.1] - 2018-11-17

### Added

* `nixpkgs_cc_configure` rule to tell Bazel to configure a toolchain
  from tools found in the given Nixpkgs repository, instead of from
  tools found in the ambient environment.
* `nixpkgs_local_repository` rule. Works like `nixpkgs_git_repository`
  but takes a checked-in Nix file or Nix expression as input.

### Changed

* The `repository` attribute is no longer deprecated. Most rules
  support both `repository` and `repositories` as attributes.

### Fixed

* Short repository labels work again. That is, you can say `repository
  = "@nixpkgs"` as a short form for `repository =
  "@nixpkgs//:default.nix"`.

## [0.3.1] - 2018-10-24

### Fixed

* `repositories` is no longer a required argument to `nixpkgs_package`.

## [0.3] - 2018-10-23

### Added

* `nixpkgks_package` now supports referencing arbitrarily named nix
  files. A bug previously only made it possible to reference
  `default.nix` files.

### Removed

* The `path` attribute has been removed. See `Migration` section
  in `README.md` for instructions.

### Changed

* `nixpkgs_packages` does not accept implicit `<nixpkgs>` version. See
   [#25](https://github.com/tweag/rules_nixpkgs/pull/25).

## [0.2.3] - 2018-07-01

### Added

* `sha256` attribute to `nixpkgs_git_repository`.
* Ability to point to a Nixpkgs fork via the new `remote` attribute to
  `nixpkgs_git_repository`.

## [0.2.2] - 2018-04-30

## [0.2.1] - 2018-03-18

## [0.2] - 2018-03-18

## [0.1] - 2018-02-21

## [0.1.1] - 2017-12-27
