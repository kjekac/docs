# Minimal examples

1. a transferrable token with possibility to query for the balance of an address
1. a multisig
1. a contract that forwards calls from a particular sender
1. a publicly mutable key-value store
1. single-vote, first-past-the-post voting
1. european option


# Desiderata

* State changes are described in an analyzable way.

  Metric: Amount of code required to prove properties of a state change. Less is better.

* Hard to introduce errors.

  Metric: The amount of ways the minimal examples can be erroneously implementated that are syntactically "similar" to a correct version. Fewer is better.

* Composability.

  Metric 1: Number of minimal examples that can be composed with other ones, without changing their implementations. More is better.

  Metric 2: Amount of code required to piece together the minimal examples to (correctly functioning) larger examples. Less is better.

  Some examples of the minimal examples that should ideally be composable:
  * 3+4 = key-value store where each value is only mutable by a particular sender.
  * 1+6 = use an option as a token
  * ∀n. 2+n = obvious

* Emphasis on blockchain-as-a-knowledge-base.

  Metric:
    * let `c(A)` be the amount of code required to draw conclusions about the state of a set of contracts A.
    * The metric is the growth of `c(A)` as `|A|` grows. Lower is better.

* Formal verification possible within the program itself.

* High-level descriptions that are concise and "intuitive" for people familiar with the language.


## Disconsiderations

* Backwards compatibility with existing languages, ABI etc.
* Intuitive descriptions for people not familiar with the language.
* EVM gas consumption. I believe that language research should guide the VM design as far as practically possible, not the other way around. If the EVM proves insufficient and Ethereum refuses to adapt for whichever reason, let's use the language on another chain. (This *does not* mean that I would find it acceptable for the language to be too inefficient to run under consensus, just that I don't consider the (current) EVM in particular to be the goal.)

# Other info

* I think [Pony](https://www.ponylang.org/) is an interesting language to look up, though I'm not sure (yet) whether it serves as a good basis for this project or not. It is based on the actor model, and it has a type system that deals with capabilities (i.e. "Who can access which piece of data in which ways?").