# RecapIt patch for silero 0.1.0

Base: `26a646003cd8532ae2dde424ccdab1b6cdf5d7b0` from `emotechlab/silero-rs` (MIT).

The `VadSession` and `VadTransition` 0.1.0 API and its VAD implementation are retained. The package manifest moves `ort` from exact `2.0.0-rc.10` to `ort` 2.0.0-rc.12 and `ndarray` from 0.16 to 0.17 so it shares the app's resolved runtime and array graph; it also keeps the current fixture test dependencies. `src/lib.rs` funnels the newer ORT builder errors through `ort::Error` before converting to `anyhow`; this changes error typing only, not VAD processing.

The upstream ONNX model remains byte-identical (SHA-256 `a35ebf52fd3ce5f1469b2a36158dba761bc47b973ea3382b3186ca15b1f5af28`). The six upstream LFS WAV fixtures used by the library tests are materialized as ordinary Git blobs, with their source revision, URLs, sizes and SHA-256 values recorded in `tests/audio-fixtures.json` and `tests/README-audio-fixtures.md`. `.gitattributes` disables the LFS filter for these paths so Cargo Git checkouts receive the fixture bytes directly.
