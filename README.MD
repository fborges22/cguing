# CGUI

C Graphical User Interface (CGUI) is a GUI toolkit for Allegro 4, originally by Christer Sandberg. It provides windows, menus, dialogs, list widgets, edit boxes, file browser widgets, tab controls, and other UI components for C applications.

This repository contains the CGUI source code, examples, build scripts for multiple toolchains, and generated/manual documentation.

## Version

- Library version: 2.1.0
- Public header version macros: `CGUI_VERSION_MAJOR`, `CGUI_VERSION_MINOR`, `CGUI_VERSION_PATCH`

## Features

- Cross-platform support through per-platform makefiles
- Widget set for classic desktop-style UI
- Example programs in `examples/` (from `00hello.c` through `30combo.c`, plus game demos)
- Documentation sources in `docs/` and generated docs in multiple formats

## Project Layout

- `src/`: CGUI library source files
- `include/`: public headers (`cgui.h`, config headers, and support headers)
- `examples/`: sample applications
- `lib/`: platform output libraries
- `obj/`: platform object output
- `docs/`: documentation sources
- `misc/`: common and platform-specific makefiles and helper tooling
- `resource/`: data resources used by the library
- `fix.sh` / `fix.bat`: platform setup scripts that generate the top-level `makefile`

## Requirements

1. Allegro 4.4.2 must be built and installed first.
2. GNU Make is required.
3. A supported C toolchain matching your target platform is required.

Supported platform/toolchain setups:

- DOS / DJGPP
- Linux / Unix (gcc)
- Cygwin
- Windows / MinGW32
- Windows / MSVC
- Mac OS X (legacy support in scripts)

## Quick Start

### 1. Configure for your platform

From the project root, run one of:

#### Linux / Unix

```sh
./fix.sh unix
```

#### Cygwin

```sh
./fix.sh cygwin
```

#### Mac OS X

```sh
./fix.sh mac
```

#### Windows (MinGW32)

```bat
fix.bat mingw32
```

#### Windows (MSVC)

```bat
fix.bat msvc
```

#### DOS (DJGPP)

```bat
fix.bat djgpp
```

This step writes the root `makefile` to include the proper platform file from `misc/`.

### 2. Build generated data tools (recommended before full build)

```sh
make dat2c
```

### 3. Build CGUI

```sh
make
```

### 4. Install

```sh
make install
```

On Unix-like systems you may need elevated permissions. You can override install prefix with:

```sh
make install SYSTEM_DIR=/your/prefix
```

## Common Build Targets

- `make` (default): build library, docs, and example outputs
- `make lib`: build only the library
- `make docs`: build only documentation
- `make clean`: remove rebuildable files
- `make veryclean`: remove rebuildable files including dependency files
- `make all`: build both optimized and debug variants
- `make installall`: install both optimized and debug variants
- `make help`: show makefile help text

## Optional Build Modes

### Debug build

```sh
make DEBUGMODE=1
```

Both standard and debug build in one run:

```sh
make all
```

### Static linking

To request static CGUI output where supported:

```sh
make STATICLINK=1
```

If you use static CGUI, ensure Allegro is also available in matching static form.

### MSYS note

For MSYS with MinGW target, set:

```sh
export UNIX_TOOLS=1
```

before install steps.

## Building and Running Examples

Examples are in `examples/` and are built by the default make flow on supported targets.

To inspect usage patterns, start with:

- `examples/00hello.c`
- `examples/01hellox.c`
- `examples/10lists.c`
- `examples/30combo.c`

## Documentation

- Main docs: `cgui.html`, `faq.html`, `changes.html`, `thanks.html`, `wishlist.html`
- Text docs: `readme.txt` and files under `docs/`

The make system can generate documentation artifacts in multiple formats depending on host tools.

## Environment Notes

- MSVC command-line environment must be initialized before running `make` (for example by invoking `vcvars32.bat`).
- Some developer targets (for example `dat`) rely on `ALLEGRO` pointing to an Allegro source tree.

## License

This project is distributed under the GNU General Public License v3. See `license.txt`.

## Contact / Origin

Original project information from bundled docs:

- Author: Christer Sandberg
- Homepage: http://cgui.sourceforge.net/
- Email: rya.christer@gmail.com
