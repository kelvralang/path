# moglang/path

Cross-platform lexical path manipulation for POSIX and Windows path strings.

## Install and import

```sh
mog add github.com/moglang/path@v0.2.0
```

```mog
const path = @import("github.com/moglang/path")

print(path.normalize("/srv/app/../data")) // /srv/data
print(path.join("C:/work", "src/main.mog")) // C:/work/src/main.mog
print(path.relative("/srv/app", "/srv/test")) // ../test
```

The canonical import is `github.com/moglang/path`; `package.api.mog` is the
complete public contract.

## Lexical model

These functions manipulate strings only. They do not access the filesystem,
resolve symlinks, expand a home directory, or check whether a path exists.

- Both `/` and `\` are accepted as input separators. Output uses `/`.
- POSIX roots (`/`), Windows drive-absolute roots (`C:/`), drive-relative roots
  (`C:work`), and UNC roots (`//server/share`) are preserved.
- A rooted child passed to `join` replaces the base. This includes a child on a
  different drive or UNC share.
- `relative` returns the normalized target unchanged when roots differ, because
  no lexical relative path can cross those roots.
- Windows drive, UNC root, and component comparisons in `relative` are ASCII
  case-insensitive. POSIX comparisons are case-sensitive.
- Two leading separators followed by a name are interpreted as a UNC path.

`normalize("")` returns `"."`, and attempts to walk above an absolute root are
clamped at that root. `extension` returns the final suffix including `.`, while
a leading-only dot such as `.gitignore` is not an extension.

## Compatibility

Version 0.2.0 requires Mog runtime `^0.1.4`. This source package has no native
build dependency and behaves the same on every host operating system; the path
syntax is determined from the input string. It is licensed under GPL-3.0-only;
see `LICENSE`.
