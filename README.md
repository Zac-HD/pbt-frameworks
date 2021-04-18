Overview of Property-Based Testing Functionality
================================================

Property-based testing (PBT) frameworks come with a number of
different features, but which library supports which features?
For a PBT newcomer, it can be hard to tell.
Strictly speaking you don't even need a PBT framework. Property-based tests can be written from scratch
on a case-by-case basis using a random number generator. One can even test stateful code without a state-machine framework,
e.g., [as outlined here](https://github.com/silentbicycle/theft/blob/master/doc/properties.md#testing-stateful-systems).
However a framework provides reusable parts and infrastructure, thus paving the way for bigger developments, such as
[property-based testing automotive software against the AUTOSAR specification](https://www.youtube.com/watch?v=zi0rHwfiX1Q).



- To test an imperative API a framework with state machine support would be nice.
- Integrated shrinking can be a nice feature for bigger developments
  where writing custom shrinkers may be out of the question.
- ...

This overview is to help myself keep track. It has been compiled over a number of years
[teaching PBT](https://janmidtgaard.dk/quickcheck/). As features are gradually added to
a framework the table's entries may unfortunately become outdated. YMMV.

I'll be happy to accept PRs for updating entries and adding new frameworks.




Framework functionality
-----------------------

| Framework                                                         | Language       | Gen. EDSL          | Shrinking          | Int. shr.          | State machine      | Par. st. mach.     | Cov. guidance      |
|:------------------------------------------------------------------|:---------------|:------------------:|:------------------:|:------------------:|:------------------:|:------------------:|:------------------:|
| [QuickCheck](http://www.quviq.com/products/erlang-quickcheck/)    | Erlang         | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    |
| [PropEr](https://github.com/proper-testing/proper)                | Erlang         | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    |
| [QuickCheck](https://github.com/nick8325/quickcheck)              | Haskell        | :heavy_check_mark: | :heavy_check_mark: |                    | [(:heavy_check_mark:)](https://github.com/advancedtelematic/quickcheck-state-machine) | [(:heavy_check_mark:)](https://github.com/advancedtelematic/quickcheck-state-machine) |                    |
| [Hedgehog](https://github.com/hedgehogqa/haskell-hedgehog)        | Haskell        | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    |
| [Scala-Hedgehog](https://github.com/hedgehogqa/scala-hedgehog)    | Scala / JVM    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    |
| [R-Hedgehog](https://github.com/hedgehogqa/r-hedgehog)            | R              | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    |                    |
| [FSharp-Hedgehog](https://github.com/hedgehogqa/fsharp-hedgehog)  | F# / .Net      | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    |                    |                    |
| [Hypothesis](https://github.com/HypothesisWorks/hypothesis)       | Python         | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | [(:heavy_check_mark:)](https://pypi.org/project/hypothesis-trio/)<sup>1</sup> |                    |
| [TSTL](https://github.com/agroce/tstl)                            | Python         | <sup>2</sup>       | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: |
| [ScalaCheck](https://github.com/typelevel/scalacheck)             | Scala / JVM    | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: | :heavy_check_mark: |                    |
| [gopter](https://github.com/leanovate/gopter)                     | Go             | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: |                    |                    |
| [propCheck](https://github.com/1Jajen1/propCheck)	                | Kotlin  	     | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    |
| [FsCheck](https://fscheck.github.io/FsCheck/index.html)           | F# / .Net      | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: |                    |                    |
| [fast-check](https://github.com/dubzzz/fast-check)                | JS / TS        | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | [(:heavy_check_mark:)](https://github.com/dubzzz/fast-check/blob/main/documentation/Tips.md#detect-race-conditions)<sup>1</sup> |                    |
| [QCheck](https://github.com/c-cube/qcheck)                        | OCaml          | :heavy_check_mark: | :heavy_check_mark: |                    | [(:heavy_check_mark:)](https://github.com/jmid/qcstm) |                |                    |
| [Crowbar](https://github.com/stedolan/crowbar)                    | OCaml          | :heavy_check_mark: | (:heavy_check_mark:)<sup>3</sup> |                    |                    |                    | :heavy_check_mark: |
| [QuickTheories](https://github.com/quicktheories/QuickTheories)   | Java           | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | [(:heavy_check_mark:)](https://github.com/quicktheories/QuickTheories/issues/42) | [(:heavy_check_mark:)](https://github.com/quicktheories/QuickTheories/issues/42) | [:heavy_check_mark:](https://github.com/quicktheories/QuickTheories#coverage-guidance) |
| [jqwik](https://jqwik.net/)                                       | Java           | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    |                    |
| [Fox](https://github.com/jeffh/Fox)                               | Obj.C / Swift  | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | [(:heavy_check_mark:)](https://github.com/jeffh/Fox/pull/28) |                     |
| [SwiftCheck](https://github.com/typelift/SwiftCheck)              | Swift          | :heavy_check_mark: | :heavy_check_mark: |                    |                    |                    |                    |
| [RapidCheck](https://github.com/emil-e/rapidcheck/)               | C++            | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: | [(:heavy_check_mark:)](https://github.com/emil-e/rapidcheck/issues/47) |                    |
| [test.check](https://github.com/clojure/test.check)               | Clojure        | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | ?                  | ?                  |                    |
| [Lua-QuickCheck](https://github.com/luc-tielen/lua-quickcheck)    | Lua            | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    |                    |
| [theft](https://github.com/silentbicycle/theft)                   | C              | (:heavy_check_mark:) | :heavy_check_mark: | [(:heavy_check_mark:)](https://github.com/silentbicycle/theft/blob/master/doc/shrinking.md#auto-shrinking) |                    |                    | [(:heavy_check_mark:)](https://github.com/silentbicycle/theft/issues/43) |
| [DeepState](https://github.com/trailofbits/deepstate)             | C / C++        | (:heavy_check_mark:) | :heavy_check_mark: | :heavy_check_mark: |                    |                    | :heavy_check_mark: |
| [Echidna](https://github.com/crytic/echidna)                      | Solidity / EVM |                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: |
| ... 

**Legend:**
 - **Language** denotes the frameworks's language or platform
 - **Generator EDSL** denotes whether the framework has an expressive, embedded domain-specific language for programming custom generators (`int`, `list`, `map`, ...)
 - **Shrinking** denotes whether the framework has built-in support for reducing counterexamples.
 - **Integrated shrinking** denotes whether a shrinker automatically preserves any invariants of an EDSL-based custom generator (sorted lists, non-empty array, valid JSON, ...)
 - **State machine** denotes whether the framework has a state-machine library for model-based testing.
 - **Parallel state machine** denotes whether the framework supports parallel state-machine testing for race conditons, etc.  
 - **Coverage guidance** denotes whether the framework's generators (and shrinkers) can be guided by code coverage information obtained via instrumentation.

 **Footnotes**
  - <sup>1</sup> [Hypothesis](https://github.com/HypothesisWorks/hypothesis) and [fast-check](https://github.com/dubzzz/fast-check) support asynchronous state machine testing, which can find race conditions (although it is strictly speaking not using parallel testing).
  - <sup>2</sup> [TSTL](https://github.com/agroce/tstl) instead uses an *external DSL*.
  - <sup>3</sup> Crowbar uses AFL which [trims each test input as part of its core genetic algorithm](https://lcamtuf.coredump.cx/afl/README.txt). In addition Crowbar supports test case reduction via `afl-tmin` [which is unaware of (and hence may break) OCaml typing](https://tarides.com/blog/2020-08-03-fuzzing-ocamlformat-with-afl-and-crowbar).


Background:
-----------

The term *property-based testing* seems to originate from [*'Property-Based Testing; A New Approach to Testing for Assurance'* by Fink and Bishop (SE Notes 1997)](http://nob.cs.ucdavis.edu/~bishop/papers/1997-sen/pbt.pdf).  
The approach was popularized as an embedded domain-specific language in [*'QuickCheck: A Lightweight Tool for Random Testing of Haskell Programs'* by Claessen and Hughes (ICFP 2000)](http://www.eecs.northwestern.edu/%7Erobby/courses/395-495-2009-fall/quick.pdf) which inspired ports to many other languages.

**Integrated shrinking** is explained in more detail in
 - [an early design thread on the Haskell mailing list](https://mail.haskell.org/pipermail/libraries/2013-November/021674.html)
 - [a Reddit thread announcing Hedgehog](https://www.reddit.com/r/haskell/comments/646k3d/ann_hedgehog_property_testing/)
 - [a talk by Jacob Stanley on Hedgehog's design](https://www.youtube.com/watch?v=AIv_9T0xKEo)
 - [a blog post by Edsko de Vries with pro/cons](https://www.well-typed.com/blog/2019/05/integrated-shrinking/)
 - [McIver's Hypothesis article advocating the approach](https://hypothesis.works/articles/integrated-shrinking/)
 - [*'Test-Case Reduction via Test-Case Generation: Insights From the Hypothesis Reducer'* by MacIver and Donaldson (ECOOP 2020)](https://www.doc.ic.ac.uk/~afd/homepages/papers/pdfs/2020/ECOOP_Hypothesis.pdf)
 - [Everything You Ever Wanted to Know About Test-Case Reduction, But Didn’t Know to Ask](https://blog.trailofbits.com/2019/11/11/test-case-reduction/) - describing DeepState's reducer/shrinker


**State machines** to test protocols and systems with state are described in
 - [*'Testing reactive systems with GAST'* by Koopman and Plasmeijer (TFP 2003, revised 2005)](https://repository.ubn.ru.nl/bitstream/handle/2066/60573/60573.pdf?sequence=1) - which describes a model-based framework for Clean's Gast library
 - [*'Testing Telecoms Software with Quviq QuickCheck'* Arts, Hughes, and Johansson (Erlang 2006)](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.148.6554&rep=rep1&type=pdf) - which describes Erlang's first `eqc_commands` module
 - [*'QuickCheck Testing for Fun and Profit'* by Hughes (PADL 2007)](https://people.inf.elte.hu/center/fulltext.pdf)  describes a later revision 
 - [the API documentation of Quviq's latest (commercial) version](http://quviq.com/documentation/eqc/)
 - [*'A Note on State-Machine Frameworks for Property-Based Testing'*](https://janmidtgaard.dk/quickcheck/stmnote.pdf) - a tutorial which reconstructs `qcstm` for OCaml


**Parallel state-machine tests** for race conditions were later introduced in
 - [*'Finding Race Conditions in Erlang with QuickCheck and PULSE'* by Claessen et al. (ICFP 2009)](https://smallbone.se/papers/finding-race-conditions.pdf) -- along with a scheduler and a process visualizer
 - *'Testing Telecoms Software with Quviq QuickCheck'* by Hughes and Bolinder (Erlang 2011)
   

Additional resources:
---------------------
 - [A shrinking challenge for comparing frameworks](https://github.com/jlink/shrinking-challenge)
 - [*'QuickCheck Advice'* by Jesper L. Andersen](https://medium.com/@jlouis666/quickcheck-advice-c357efb4e7e6)
 - [A recent course by John Hughes](http://www.cse.chalmers.se/~rjmh/MGS2019/)
 - [My own course material](https://janmidtgaard.dk/quickcheck/)
 - ...
