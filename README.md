# Lambda Soup

Lambda Soup is a functional HTML scraping and manipulation library for OCaml
aimed at being easy to use.

![Lambda Soup usage example][sample]

[sample]: https://raw.githubusercontent.com/aantron/lambda-soup/master/docs/sample.gif

[![version 0.5][version]][releases] [![BSD license][license-img]][license]

[version]:     https://img.shields.io/badge/version-0.5-blue.svg
[license-img]: https://img.shields.io/badge/license-BSD-blue.svg

For some more examples, see the Lambda Soup [postprocessor][postprocess] that
runs on Lambda Soup's own [documentation][docs] after it is generated by
`ocamldoc`.

Lambda Soup is *simple*. It provides a set of
[elementary traversals][traversals] for getting from node to node, familiar
functional [combinators][combinators] such as `filter`, `map`, and `fold`, and
support for all CSS selectors that still make sense when not running in a
browser (and a few obvious [extensions][extracss] on top of that).

The library is [tested][tests] thoroughly.

## Installing

Until the library is added to OPAM, the easiest way to install Lambda Soup is to
clone this repository locally, then, in your local Lambda Soup repository root,
run

    make install

This requires OPAM and uses it to pin the `lambdasoup` package. Later, to remove
the installation from local clone, you can do

    make uninstall

Lambda Soup relies on Ocamlnet's HTML parser. OPAM will grab that for you.
Lambda Soup has no other dependencies.

## Documentation

Lambda Soup consists of one module, whose signature is documented [here][docs].

## Performance

I ran a simplistic performance test, comparing some
[Lambda Soup code][ocaml-perf] to the equivalent
[Beautiful Soup code][python-perf] operating on the Google search page. The
Lambda Soup code was compiled to both native code and bytecode. Here are the
results on my system:

    test            native      bytecode    python

    parse            272 µs     1167 µs     4173 µs
    traverse           4 µs       44 µs       53 µs
    select            13 µs      167 µs      105 µs
    select_all        26 µs      338 µs      164 µs

It seems that the initial, naive implementation of `select` could use some work.
However, absent feedback, this does not have a very high priority. It is
certainly fast enough for interactive use, for example.

## Developing

See [CONTRIBUTING][contributing]. All feedback is welcome – open an issue on
GitHub, or send me an email at [antonbachin@yahoo.com][email]. If you find
yourself repeatedly writing the same helper on top of Lambda Soup's functions,
perhaps we should add it to Lambda Soup.

[![Travis status][travis-img]][travis]

[travis]:       https://travis-ci.org/aantron/lambda-soup/branches
[travis-img]:   https://img.shields.io/travis/aantron/lambda-soup/master.svg

## License

Lambda Soup is distributed under the BSD license. See [LICENSE][license].

[docs]:         http://aantron.github.io/lambda-soup
[postprocess]:  https://github.com/aantron/lambda-soup/blob/master/docs/postprocess.ml
[tests]:        https://github.com/aantron/lambda-soup/blob/master/test/test.ml
[ocaml-perf]:   https://github.com/aantron/lambda-soup/blob/master/test/performance.ml
[python-perf]:  https://github.com/aantron/lambda-soup/blob/master/test/performance.py
[contributing]: https://github.com/aantron/lambda-soup/blob/master/docs/CONTRIBUTING.md
[email]:        mailto:antonbachin@yahoo.com
[license]:      https://github.com/aantron/lambda-soup/blob/master/docs/LICENSE
[releases]:     https://github.com/aantron/lambda-soup/releases
[extracss]:     http://aantron.github.io/lambda-soup#VALselect
[traversals]:   http://aantron.github.io/lambda-soup#2_Elementarytraversals
[combinators]:  http://aantron.github.io/lambda-soup#2_Combinators
