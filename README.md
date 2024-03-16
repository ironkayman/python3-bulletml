# python3-bulletml

> _BulletML for Python3_

BulletML is the Bullet Markup Language. BulletML can describe the barrage of bullets in shooting games. (For example Progear, Psyvariar, Gigawing2, G DARIUS, XEVIOUS, ...) This module parses and executes BulletML scripts in Python. All data structures in it are renderer-agnostic. A sample renderer for Pygame is included. The full API documentation is contained in its Python docstrings.

In addition to the standard BulletML XML format, this module supports an equivalent YAML format. For convenience, two simple collision routines are provided, `bulletml.overlaps` for stationary circles and `bulletml.collides` for moving circles.

More information is available at [the BulletML homepage](http://www.asahi-net.or.jp/~cs8k-cyu/bulletml/index_e.html), or [the python-bulletml homepage](https://yukkurigames.com/python-bulletml/).

```sh
./demo/bulletml-runner-pygame.py examples/*/*.xml
# or
./demo/bulletml-runner-arcade.py examples/*/*.xml
```

Use Page Up and Page Down to switch between bullet definitions, S to
respawn the bullet pattern, and Enter to restart it.

## Installing

> Why pyodide?
> Python has multiple ways of building/installing a packages, like setuptools, distutils with, regulary, a wheel/`.whl` as an output, since this fork is created solely for a personal project, I am more than fine building in a fast-and-loose manner, a wheel without any need to dive again into mentioned above native solutions. It may change in the future but currently it is more of an overhead for _my_ needs.

**Prerequisites**:

- python 3.10+
- poetry
- [taskfile](https://taskfile.dev) (optional, see tasks' commands within their appropriate `cmd` sections)

**First-time environment setup**:

```sh
poetry shell
git clone https://github.com/emscripten-core/emsdk.git
cd emsdk
PYODIDE_EMSCRIPTEN_VERSION=$(pyodide config get emscripten_version)
./emsdk install ${PYODIDE_EMSCRIPTEN_VERSION}
./emsdk activate ${PYODIDE_EMSCRIPTEN_VERSION}
source emsdk_env.sh
task build/release
# or
task build/debug
```

Once installed, a regular pipeline consists of:

```sh
poetry shell
cd emsdk
source emsdk_env.sh
task build/release
# or
task build/debug
```

## Usage

Since _Pyodide packages_ are as of currently (12.03.2024) while remaining as wheels, are not compatible with PyPi so you need to clone this repo retro-style and add local path to the repo dists built earlier:

### Poetry

Poetry's config snippet, add the following lines if abscent:

```toml
[tool.poetry.dependencies]
python = "^3.10"
bulletml = {file = "bulletml/dist/release/bulletml-0.1.0-py3-none-any.whl"}
```

where `= "bulletml/` is this a path to this repo's cloned directory.

Then regenerate `poetry.lock` file:

```sh
poetry lock
poetry install
```

> **NOTE:** Python 3.10+ herein is a strict requirement due to specificity of pyodide/emscripten build pipeline

## License

The BulletML specification is the work of Kenta Cho.

All example BulletML files in the examples folder are released into
the public domain. Everything else is covered by the following
license:

Copyright 2010 Joe Wreschnig

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
