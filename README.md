# BeatMaxing — model mirror

This repository holds **spare copies of open-source model files**, nothing else.

BeatMaxing is a Premiere Pro plugin that finds the real drum hits in a song. To
separate the drums it uses an open-source engine, and that engine needs a model
file of about 610 MB the first time it runs. Until now every new customer
downloaded that file from a single upstream repository. If that repository ever
went away, new installs would break and there would be nothing we could do about
it from our side.

So the files are mirrored here. The BeatMaxing helper tries this copy first and
falls back to the original publishers if it is missing, so neither copy is a
single point of failure any more.

## What is in the release

Everything lives under the **`models-v1`** release. Each file is checked by the
helper against its size **and** its sha256 before it is used — a copy that does
not match byte for byte is discarded and the original is fetched instead.

| File | Bytes | sha256 |
| --- | --- | --- |
| `model_bs_roformer_ep_368_sdr_12.9628.ckpt` | 639317465 | `f6c94864adfb73bbb0ca58ec14d58dd0b364549e9fb61433ae51916f3e2f8d0b` |
| `model_bs_roformer_ep_368_sdr_12.9628.yaml` | 2274 | `aea599b3f9bd4892a9c6bf5ac7c44787d3c99f717903d16054702665d477c86b` |
| `download_checks.json` | 28267 | `d3622e1fa19c161d3cf704927711b453d593a3f1eb0f2e0838c3136907935151` |
| `mdx_model_data.json` | 15358 | `1aca8f9bcc57233bc714029663a9ec2345d9c7721f91e5e08f46392a879c6a9a` |
| `vr_model_data.json` | 4380 | `6a2021b9aa355c10f845b68c73944d47bd9e1fdf37b8a584b14ce8f88b09bb2f` |

The last two are the engine's own model index files. Upstream they are both named
`model_data_new.json`; they are published here under the names the engine expects
to find on disk, because a copy under the source name would not be recognised.

**The release tag never changes.** A shipped copy of the helper points at
`releases/download/models-v1/`, so renaming the tag or this repository would
break every customer who has not downloaded the model yet.

## Credit

None of this is BeatMaxing's own work. It is republished unchanged so that it
stays reachable.

- The model was trained as part of the [Ultimate Vocal Remover
  (UVR)](https://github.com/Anjok07/ultimatevocalremovergui) project and is
  distributed under the MIT licence. **Credit to UVR and its developers.**
- The code that loads it is
  [python-audio-separator](https://github.com/nomadkaraoke/python-audio-separator),
  MIT licensed, © 2023 karaokenerds.

The same credit is published at <https://beatmaxing.com/terms>.

## Issues

This repository is a file store and is not the place for support. Anything about
the plugin itself belongs at <https://beatmaxing.com>.
