# PROJECT_LOG.md

Append-only development history for this GLU working tree.

## 2026-05-31

- Added an interpolating gauge-fixing path selected by `GFTYPE = INTERPOLATING`.
- Introduced `GF_EPSILON` as the temporal derivative weight: `1.0` recovers the Landau gauge condition, and `0.0` removes the temporal derivative term in the new global solver path.
- Threaded the epsilon value through input parsing, gauge-fixing dispatch, weighted derivative tests, weighted functionals, Fourier acceleration momentum weights, and CLI help/autoin generation.
- Updated `README.md` with local build notes, interpolating-gauge input usage, and S8T32 smoke-test guidance.
- Built locally with `./configure --prefix=$PWD/local CFLAGS="-O2 -fopenmp" --with-fftw=`, `make -j2`, and `make install`; `./tests/unit` passed all 156 tests.
- Ran S8T32 smoke tests for `GF_EPSILON = 1.0`, `0.0`, and `0.5` using `CONF/S8T32_wilson_b6.0`; all reached the requested `1e-6` smoke-test accuracy and wrote local output configurations.
- Added `tests/input_S8T32_interpolating.txt` as an S8T32 interpolating-gauge input template based on the external benchmark input.
