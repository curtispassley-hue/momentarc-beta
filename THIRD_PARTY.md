# Third-party inventory

Direct ranges are in pyproject.toml. Versions below were resolved during M01
validation on Python 3.12.14; transitive versions describe that environment rather
than additional direct requirements. Recheck this inventory when dependencies
change. Upstream project metadata and installed license files were inspected.

For MIT entries, preserve the license and copyright notice. BSD entries also
retain their conditions/disclaimer; BSD-3 adds a non-endorsement condition.
PSF entries retain the PSF terms/notices. Apache entries require review and
retention of applicable license/NOTICE material and modification notices.
These notes do not replace the actual license files.

## Windows Beta 1 distribution review

Owner-approved packaging uses a minimal pinned environment in `packaging/windows/requirements.txt`.
Runtime versions match the inventory below. Actual full installed runtime license files are
copied to `THIRD_PARTY_NOTICES`, including NumPy native-library notices. Python 3.12.14's complete
Windows LICENSE.txt includes interpreter/embedded third-party/Microsoft redistributable conditions,
retained unchanged. The freeware license preserves third-party rights and Microsoft runtime-only
restrictions. SQLite's unmodified public-domain DLL is included with this Python runtime.

| Build dependency | Pinned version | Purpose / license | Upstream / redistribution | ARM64 |
|---|---|---|---|---|
| PyInstaller | 6.22.3 | Freeze app / GPL-2.0 bootloader commercial-distribution exception; some Apache-2.0 | [License](https://pyinstaller.org/en/stable/license.html); unmodified bootloader; preserve COPYING.txt voluntarily; application/dependency licenses still apply | Linux aarch64 upstream; only Windows x64 tested here |
| pyinstaller-hooks-contrib | 2026.8 | Freeze hooks / GPL-2.0 exception; runtime hooks Apache-2.0 | [Source](https://github.com/pyinstaller/pyinstaller-hooks-contrib); retain installed LICENSE; build-only hooks excluded | Pure Python, target hooks vary |
| altgraph | 0.17.5 | Dependency graph / MIT | [Source](https://github.com/ronaldoussoren/altgraph); build-only, retain notices if redistributed | Pure Python |
| pefile | 2024.8.26 | PE inspection / MIT | [Source](https://github.com/erocarrera/pefile); build-only | Pure Python |
| pywin32-ctypes | 0.2.3 | Windows freeze adapter / BSD-3-Clause | [Source](https://github.com/enthought/pywin32-ctypes); build-only, never a core requirement | Native ARM64 not validated |
| Inno Setup | 6.7.3 | Per-user installer / custom permissive | [License](https://jrsoftware.org/files/is/license.txt); official compiler Authenticode Pyrsys B.V. verified, not redistributed; setup retains notices and included license. Upstream requests commercial purchase, not mandatory in published license | Supports x64/ARM64 targets; beta restricts native x64 |

APPROVED scoped unmodified beta runtime/build use with notices. No application dependency added.
Setuptools/packaging/pip remain build-only. OCR/models, fonts and game assets excluded. No signing
key or paid service installed. Complete Python LICENSE.txt supplies bundled third-party notices;
full NumPy license includes OpenBLAS and its native notices. Python's Windows license covers PSF,
Microsoft, bzip2 and legacy notices but does not contain every embedded library notice; the builder
therefore requires the separate reviewed license snapshots below as well.

| Embedded runtime component | Observed version / notice source | License / purpose / upstream | Redistribution / ARM64 |
|---|---|---|---|
| OpenSSL | 3.5.8 observed via ssl.OPENSSL_VERSION | Apache-2.0 / Python TLS/hash DLLs / [source](https://github.com/openssl/openssl/tree/openssl-3.5.8) | Full LICENSE retained; upstream tag has no NOTICE file; unchanged DLLs; upstream ARM64, local x64 only |
| Expat | 2.8.3 observed via pyexpat.EXPAT_VERSION | MIT / XML parser / [source](https://github.com/libexpat/libexpat/tree/R_2_8_3) | Full COPYING retained; portable upstream, local x64 only |
| zlib | 1.3.2 observed via zlib.ZLIB_VERSION | zlib / compression / [source](https://github.com/madler/zlib/tree/v1.3.2) | Full LICENSE retained; portable upstream, local x64 only |
| libffi | Runtime DLL's version unavailable; notice snapshot v3.5.2 (not a version claim) | MIT / Python ctypes / [source](https://github.com/libffi/libffi/tree/v3.5.2) | Full upstream LICENSE and copyrights retained; unmodified Python DLL; target-specific ARM64 ABI not tested |
| liblzma | Embedded version unavailable; notice snapshot XZ v5.8.3 (not a version claim) | 0BSD/public-domain library / Python lzma / [source](https://github.com/tukaani-project/xz/tree/v5.8.3) | COPYING/0BSD retained; no GPL CLI/build scripts shipped; portable upstream, local x64 only |

These permissive embedded-runtime notice snapshots are retrieved explicitly by the build operator,
not the app; URL/content hashes are retained in the build manifest. They do not assert unknown
native versions or introduce a new API/runtime package. All copied license texts were inspected.

FFmpeg/FFprobe 9.0.2 Gyan essentials GPLv3 remains external, not bundled/rehosted. Owner explicitly
approved unchecked user-consented provider download. Pinned URL/hash are in `setup.iss`; full
archive/license/README are retained, unpacked by Python after a second hash and bounded path checks.
Only the authenticated temporary ZIP is deleted after success. Uninstall targets three exact
tool executables, never recursively removing folders or `.momentarc`/source media. Offline
binary distribution remains REVIEW:
an FFmpeg source link does not establish complete source for all static libraries. See
[provider](https://www.gyan.dev/ffmpeg/builds/) and [legal requirements](https://ffmpeg.org/legal.html).
This is not codec/patent legal clearance; a commercial offline bundle needs separate review.

The release operator may use GitHub CLI 2.102.0 (MIT, [source](https://github.com/cli/cli)) as a
developer tool, not shipped. Publication uses existing credentials in memory, never source/logs.

## Runtime

| Dependency | Range / resolved | Purpose | License | Upstream | Redistribution | Linux ARM64 assessment |
|---|---|---|---|---|---|---|
| Pydantic | >=2.12,<3 / 2.13.5 | Strict models and JSON Schema | MIT | [Pydantic](https://github.com/pydantic/pydantic) | Preserve MIT notices | Python layer; depends on native core below |
| NumPy | >=2,<3 / 2.5.3 | Bounded-memory array operations for signal streams and primitives | BSD-3-Clause | [NumPy](https://github.com/numpy/numpy) | Preserve BSD license and copyright notices | CPython 3.12 Linux aarch64 wheels available; isolate behind NumPy signal adapter |
| pydantic-core | Pydantic-selected / 2.46.5 | Model validation engine | MIT | [Source](https://github.com/pydantic/pydantic/tree/main/pydantic-core) | Preserve MIT and bundled notices | CPython 3.12 Linux aarch64 wheel verified on [PyPI](https://pypi.org/project/pydantic_core/2.46.5/#files) |
| annotated-types | transitive / 0.8.0 | Constraint metadata | MIT | [Source](https://github.com/annotated-types/annotated-types) | Preserve MIT notices | Pure Python |
| typing-extensions | transitive / 4.16.0 | Typing compatibility | PSF-2.0 | [Source](https://github.com/python/typing_extensions) | Preserve PSF notices | Pure Python |
| typing-inspection | transitive / 0.4.4 | Runtime typing inspection | MIT | [Source](https://github.com/pydantic/typing-inspection) | Preserve MIT notices | Pure Python |

## Build and development only

These tools are not application runtime dependencies and are not bundled by M01.

| Dependency | Range / resolved | Purpose | License | Upstream | Redistribution | Linux ARM64 assessment |
|---|---|---|---|---|---|---|
| setuptools | >=75,<83; 82.0.1 assessed | Build backend | MIT | [Source](https://github.com/pypa/setuptools) | Preserve notices if redistributed | Universal Python wheel |
| pytest | >=8,<10 / 9.1.1 | Tests | MIT | [Source](https://github.com/pytest-dev/pytest) | Preserve MIT notices | Pure Python |
| pytest-cov | >=6,<8 / 7.1.0 | Coverage tooling | MIT | [Source](https://github.com/pytest-dev/pytest-cov) | Preserve MIT notices | Pure Python |
| Ruff | >=0.11,<1 / 0.16.7 | Lint and formatting | MIT | [Source](https://github.com/astral-sh/ruff) | Preserve MIT and bundled notices | Linux aarch64 [wheel verified](https://pypi.org/project/ruff/0.16.7/#files) |
| mypy | >=1.15,<2 / 1.20.2 | Static typing | MIT | [Source](https://github.com/python/mypy) | Preserve MIT notices | Linux aarch64 and pure Python [wheels verified](https://pypi.org/project/mypy/1.20.2/#files) |
| mypy-extensions | transitive / 1.1.0 | mypy support | MIT | [Source](https://github.com/python/mypy_extensions) | Preserve MIT notices | Pure Python |
| librt | transitive / 0.15.0 | mypy compiled runtime | MIT | [Source](https://github.com/mypyc/librt) | Preserve MIT notices | CPython 3.12 Linux aarch64 [wheel verified](https://pypi.org/project/librt/0.15.0/#files) |
| pathspec | transitive / 1.1.1 | mypy path matching | MPL-2.0 | [Source](https://github.com/cpburnz/python-pathspec) | REVIEW before redistribution; development only | Pure Python |
| coverage | transitive / 7.16.0 | Test coverage | Apache-2.0 | [Source](https://github.com/coveragepy/coveragepy) | Retain applicable license/NOTICE material | Linux aarch64 and pure Python [wheels verified](https://pypi.org/project/coverage/7.16.0/#files) |
| iniconfig | transitive / 2.3.0 | pytest config parser | MIT | [Source](https://github.com/pytest-dev/iniconfig) | Preserve MIT notices | Pure Python |
| packaging | transitive / 26.3 | Tool version parsing | Apache-2.0 OR BSD-2-Clause | [Source](https://github.com/pypa/packaging) | Preserve chosen license and notices | Pure Python |
| pluggy | transitive / 1.6.0 | pytest hooks | MIT | [Source](https://github.com/pytest-dev/pluggy) | Preserve MIT notices | Pure Python |
| Pygments | transitive / 2.21.0 | pytest output | BSD-2-Clause | [Source](https://github.com/pygments/pygments) | Preserve BSD notices | Pure Python |
| colorama | Windows transitive / 0.4.6 | pytest terminal colors | BSD-3-Clause | [Source](https://github.com/tartley/colorama) | Preserve BSD notices | Pure Python; not required by pytest on Linux |
| pip | environment tool / 25.0.1 | Environment installation | MIT | [Source](https://github.com/pypa/pip) | Not bundled; review vendored notices if redistributed | Pure Python |
| RapidOCR ONNX Runtime | optional semantic-dev / 1.4.4 | Local OCR for explicit Development-only League detector runs | Apache-2.0 | [Source](https://github.com/RapidAI/RapidOCR) | Retain Apache license/NOTICE material; not bundled by default | Python package is portable; ONNX Runtime wheel availability controls execution and missing support yields typed abstention |
| ONNX Runtime | RapidOCR transitive / 1.30.0 assessed | Local OCR model execution | MIT | [Source](https://github.com/microsoft/onnxruntime) | Preserve MIT and bundled third-party notices | Linux aarch64 wheels are published; hardware/provider support varies and the adapter retains a fallback |
| OpenCV Python | RapidOCR transitive / 5.0.0.93 assessed | OCR image preparation | Apache-2.0 | [Source](https://github.com/opencv/opencv-python) | Retain Apache license/NOTICE material | Wheel availability varies by platform; isolated behind the optional OCR adapter |
| PyClipper | RapidOCR transitive / 1.4.0 assessed | OCR polygon processing | MIT | [Source](https://github.com/fonttools/pyclipper) | Preserve MIT notices | Native wheels vary; absence disables only the optional Development detector |
| Shapely | RapidOCR transitive / 2.1.2 assessed | OCR geometry operations | BSD-3-Clause | [Source](https://github.com/shapely/shapely) | Preserve BSD license and copyright notices | Linux aarch64 wheels are published; isolated behind the optional OCR adapter |
| Pillow | RapidOCR transitive / 12.3.0 assessed | OCR image handling | HPND | [Source](https://github.com/python-pillow/Pillow) | Preserve the Pillow license and notices | Linux aarch64 wheels are published; optional Development use only |
| PyYAML | RapidOCR transitive / 6.0.3 assessed | OCR model configuration | MIT | [Source](https://github.com/yaml/pyyaml) | Preserve MIT notices | Linux aarch64 wheels are published; optional Development use only |
| protobuf | ONNX Runtime transitive / 7.36.2 assessed | ONNX model metadata | BSD-3-Clause | [Source](https://github.com/protocolbuffers/protobuf) | Preserve BSD license and copyright notices | Linux aarch64 wheels are published; optional Development use only |

The Python runtime (3.12+) and its stdlib sqlite3, argparse and tomllib are not
additional PyPI dependencies. Python uses the PSF license family; SQLite upstream
is public domain. A future bundled interpreter still needs a complete notice
review. See [Python licensing](https://docs.python.org/3/license.html) and
[SQLite copyright](https://sqlite.org/copyright.html).

GitHub Actions checkout v4 and setup-python v5 are CI-only, MIT-licensed upstream
actions ([checkout](https://github.com/actions/checkout),
[setup-python](https://github.com/actions/setup-python)); retain their notices
if redistributing them. Hosted CI use does not add application dependencies.

FFmpeg/FFprobe: optional external executables, no version requirement for M01,
not bundled, **REVIEW** before redistribution. License/build/codec combinations
vary; consult [FFmpeg legal](https://ffmpeg.org/legal.html). The fixture generator
uses a fresh output directory and generated color/sine inputs only.

Wheel availability is not an ARM64 execution claim. The local M01 run was on
Windows x86_64; Linux CI and injected Linux/aarch64 adapter tests cover the
portable design. Hardware acceleration and Edge deployment remain future work.
