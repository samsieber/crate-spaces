# Crate Space Pre-RFC

What's the best solution for namespaces in the rust ecosystem? After a quick survey of proposals, 
the one with the most support from team members (though not necessarily the team itself) is a way to group crates into a top level item.

## Motivation

Structured Trust. Crate spaces provide a counter balance to the ease of adding dependencies. While easily creating/adding dependencies is nice, it invites a proliferation of crates and deep dependency trees.

There are a couple of factors at play:
 * The rust std is small
 * There is a convention of prefixing extension crates to with the name of the base crate they are for. E.g. json support for serde is serde-json
 * Large disjointed dependency trees are unwieldy from a maintainer point of view
 
## References

There have been several attempts at this:

* https://internals.rust-lang.org/t/namespacing-on-crates-io/8571
* https://internals.rust-lang.org/t/pre-rfc-domains-as-namespaces/8688
* https://internals.rust-lang.org/t/pre-rfc-packages-as-namespaces/8628
* https://internals.rust-lang.org/t/scoped-packages-like-in-npm/10223/3
* https://internals.rust-lang.org/t/pre-rfc-idea-cratespaces-crates-as-namespace-take-2-or-3/11320
* https://internals.rust-lang.org/t/pre-rfc-user-namespaces-on-crates-io/12851
 
And the subject has been broached in major threads about crates.io policies

* https://internals.rust-lang.org/t/crates-io-package-policies/1041
* https://internals.rust-lang.org/t/crates-io-squatting/8031/62
* https://internals.rust-lang.org/t/proposal-for-crates-io-crate-name-reservation/11341/34
* https://internals.rust-lang.org/t/crates-io-incident-2018-10-15/8568
* https://internals.rust-lang.org/t/pre-rfc-formal-squatting-policy-on-crates-io/11302/20

## Major Questions

* Referring to namespaced crates in code
* Referring to namespaced crates in Cargo.toml
* Referring to namespaced crates in urls (docs, crates.io and lib.rs)
* Can they be nested? Can a crate space use another crate space? 
* Who controls crate membership in a cratespace / how it's created
  * When a space is created and owned, and a child made, should it inherit the space owners? Then what if the owner changes?
* Does the entire crate space get a version, or do you select the individual versions of the crates
  
## Alternatives

* Just use defacto namespace prefixes (e.g. serde-*)
* An externally maintained list of packages that work together well
* Allow for defacto metadata in extra Cargo.toml fields that crev can work with
