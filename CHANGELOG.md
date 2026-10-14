# Changelog

All notable changes are documented here, following
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/) and
[Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added
- The conformance gate of the get-sybers standard (DX_DFIR
  `docs/reference/build-and-test.md`): `make conform` (gofmt, vet, build,
  shuffled tests with coverage, `go mod tidy -diff`, Windows and macOS
  cross-compiles, a `go:generate` drift check and `scripts/structlint.sh`),
  `make lint` (golangci-lint v2, `.golangci.yml`) and `make vuln`
  (govulncheck), run by the `CI` workflow on pull requests and `main` — on
  amd64 and arm64 — with `all_green` as the one required status check. It
  replaces the `Build` workflow.
- Repository hygiene: `.editorconfig`, `.gitattributes`, `.shellcheckrc`,
  Dependabot (actions and Go modules, weekly, grouped), `CODEOWNERS`, a
  security policy and a pull-request template.

### Changed
- The `Test` workflow (the MemProcFS integration tests against a real memory
  dump) pins its actions by commit, scopes its permissions, and runs only
  where the `GCS_MEMDUMP_PATH` variable and the Google Cloud secrets are
  configured; elsewhere it is skipped instead of failing.

### Fixed
- `NewVmm` returned a nil `*Vmm` with a nil error when the native functions
  could not be bound, and ignored a failure to convert an initialisation
  argument (the gate's `ineffassign` finding). Both now return the error.
- gofmt on nine files; a test variable's dead initial value; comment
  spellings.

## [0.2.0] - 2026-10-04

The custody release: the module path moves to `github.com/Get-Sybers/gomemprocfs`
and the `go` directive to 1.27.1. Earlier tags are the upstream history; see
the git log.

## [0.1.3] - 2026-05-04

## [0.1.2] - 2026-03-28

## [0.1.1] - 2026-03-24

[Unreleased]: https://github.com/Get-Sybers/gomemprocfs/compare/v0.2.0...HEAD
[0.2.0]: https://github.com/Get-Sybers/gomemprocfs/compare/v0.1.3...v0.2.0
[0.1.3]: https://github.com/Get-Sybers/gomemprocfs/compare/v0.1.2...v0.1.3
[0.1.2]: https://github.com/Get-Sybers/gomemprocfs/compare/v0.1.1...v0.1.2
[0.1.1]: https://github.com/Get-Sybers/gomemprocfs/releases/tag/v0.1.1
