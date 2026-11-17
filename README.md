# discretionary_engine
![Minimum Supported Rust Version](https://img.shields.io/badge/nightly-1.92+-ab6000.svg)
[<img alt="crates.io" src="https://img.shields.io/crates/v/discretionary_engine.svg?color=fc8d62&logo=rust" height="20" style=flat-square>](https://crates.io/crates/discretionary_engine)
[<img alt="docs.rs" src="https://img.shields.io/badge/docs.rs-66c2a5?style=for-the-badge&labelColor=555555&logo=docs.rs&style=flat-square" height="20">](https://docs.rs/discretionary_engine)
![Lines Of Code](https://img.shields.io/endpoint?url=https://gist.githubusercontent.com/valeratrades/b48e6f02c61942200e7d1e3eeabf9bcb/raw/discretionary_engine-loc.json)
![Build time](https://img.shields.io/endpoint?url=https://gist.githubusercontent.com/valeratrades/b48e6f02c61942200e7d1e3eeabf9bcb/raw/discretionary_engine-build.json)
![Test time](https://img.shields.io/endpoint?url=https://gist.githubusercontent.com/valeratrades/b48e6f02c61942200e7d1e3eeabf9bcb/raw/discretionary_engine-test.json)
<br>
[![errors](https://img.shields.io/endpoint?url=https://gist.githubusercontent.com/valeratrades/b48e6f02c61942200e7d1e3eeabf9bcb/raw/discretionary_engine-errors.json)](https://github.com/EV-Quant/discretionary_engine/actions/workflows/errors.yml?query=branch%3Amain)
[![warnings](https://img.shields.io/endpoint?url=https://gist.githubusercontent.com/valeratrades/b48e6f02c61942200e7d1e3eeabf9bcb/raw/discretionary_engine-warnings.json)](https://github.com/EV-Quant/discretionary_engine/actions/workflows/warnings.yml?query=branch%3Amain)

Places and follows a position from a definition of _what the target position is_
<!-- markdownlint-disable -->
<details>
<summary>
<h2>Installation</h2>
</summary>

TODO


</details>
<!-- markdownlint-restore -->

## Usage
Example query:
```sh
discretionary_engine new --size=-0.1 --symbol=ADAUSDT '-f=sar:t5m:s0.07:i0.02:m0.15' '-f=tpsl:t0.4884:s0.5190'
```
This would open a new position on ADA, where:
- Side: SELL, as the provided size is negative
- Size: 10% of the total balance
- rm_protocol_1: sar indicator, following the price action on 5m timeframe, with starting value 0.07, increase of 0.02, max 0.15
- rm_protocol_2: static tp and sl, which are set at 0.4884 and 0.5190, respectively

#### Configuration
Config is read from ${HOME}/.config/discretionary_engine.toml by default, but can also be specified via `--config` cli argument.

An example config can be found in ./docs/.readme_assets/examples/config.toml

## Assumptions
- strictly one asset per `Position`. No methods for acquiring several assets at once will ever be introduced.

### Current (may change in the future)
- no two `Position`s are opened on the same symbol

- no new `Position`s on account are opened outside of the engine

- orders are placed immediately (not that far off, as most of the time we will spam the thing until it accepts. And only other action, that will need to be taken, is to prevent any increases in exposure while we have any mismatches).

<!--## Roadmap-->
<!--- [ ] micro/macro data distinctions-->
<!--- [ ] scale to multiple positions-->
<!--    if we're correctly using websockets for trading, actually don't think we need to have a mother program for all to share exchange connections: micro data will be stored on a separate server; macro is generally cheap to pull (or needs to be pre-compiled anyways)-->


<br>

<sup>Links for devs:</sup>
- <sup><a href="./docs/ARCHITECTURE.md">architecture</a></sup>
- <sup><a href="https://github.com/EV-Main/.github/blob/main/code/STYLE.md">style</a></sup>
- <sup><a href="https://github.com/EV-Main/.github/tree/main/code/conventions">conventions</a></sup>
- <sup><a href="https://github.com/EV-Main/.github/blob/main/code/conventions/git">contributing</a></sup>

#### License

<sup>
	Licensed under <a href="LICENSE">Blue Oak 1.0.0</a>
</sup>

<br>

<sub>
	Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in this crate by you, as defined in the Apache-2.0 license, shall
be licensed as above, without any additional terms or conditions.
</sub>

