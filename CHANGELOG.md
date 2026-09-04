# Changelog

## 0.2.0

- Rename package manifests, source files, imports, automation, and documentation from Mog to Kelvra; require Kelvra 0.2.0 or newer.

- Correct the minimum supported runtime to Kelvra 0.1.4, the first release that
  embeds its configured package-compatibility version correctly.
- Add pinned CI/release automation with tag checks, 0.1.4/current-runtime tests,
  checksummed archives, and automated action updates.
- Preserve POSIX, Windows drive-absolute, drive-relative, and UNC lexical roots.
- Make rooted children replace the base in `join`.
- Return the normalized target from `relative` when roots differ and compare
  Windows paths using ASCII case-insensitive semantics.
- Add `isAbsolute` and document the package's host-independent lexical model.
- Expand tests for absolute children, drive paths, UNC shares, root mismatch,
  dirname behavior, and case comparison.
- Correct manifest license metadata to `GPL-3.0-only` to match `LICENSE`.

## 0.1.1

- Require Kelvra runtime 0.1.1 or newer for string slicing and character inspection.
- Add complete package publication metadata.

## 0.1.0

- Initial foundation package contract.
