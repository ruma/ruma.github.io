+++
title = "This Week in Ruma"
date = 2016-08-28
extra.author = "Jimmy Cuadra"
+++

Recently, types from the ruma-identifiers crate were integrated into ruma-events and ruma, so that values representing a Matrix ID can guarantee some important invariants.
Previously these values were just strings.
There was still a source of confusion and errors in that the ID types had to be converted to and from strings for the structs that represent database records using the Diesel ORM.
To fix this, I added the necessary implementations to ruma-identifiers (under the "diesel" feature) so that the ID types can serve directly as the database columns' data types.
Of course, these are still stored as text in the database, but the conversion happens only during data serialization and deserialization, and so cannot be broken by application logic.
This was a pretty hairy change and it took a while to get it all working and to get the test suite updated and passing.
Big thanks to Sean Griffin (author of Diesel) for helping me figure out how to achieve this.

## Notable changes to [ruma](https://github.com/ruma/ruma)

* Increase the portability of the Cargo wrapper script.
* Use ruma-identifiers ID types for relevant database columns.

## Notable changes to [ruma-identifiers](https://github.com/ruma/ruma-identifiers)

* Crate version 0.4.0 and then 0.4.1 were released, adding Diesel integration and a bug fix for case-sensitivity in user IDs.

## New contributors

* [Severen Redwood](https://github.com/SShrike)

## Rust at large

* Sean Griffin shared [some details](https://gist.github.com/sgrif/92809819185a4077e919aaf0a607c6ef) of generic implementations that don't work right now, but ideally could help make it easier for apps to create their own custom Diesel data types.
* An important step for the future prospects of moving Ruma to stable Rust, the [implementation for macros 1.1](https://github.com/rust-lang/rust/pull/35957) will land soon.
  This will allow Diesel and Serde to use custom derive without requiring nightly features, which is one of the main reasons Ruma targets nightly Rust.
