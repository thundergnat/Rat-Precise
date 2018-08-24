NAME
====

Rat::Precise

SYNOPSIS
========

Stringify Rats to a configurable precision.

Provides a Rational method .precise. Pass in a positive integer to set places of precision. Pass in a boolean flag :z to preserve trailing zeros.

    use Rat::Precise;

    my $rat = 2213445/437231;

    say $rat;                 # 5.0624155
    say $rat.precise;         # 5.0624155194851234
    say $rat.FatRat.precise;  # 5.06241551948512342445983930691099
    say $rat.precise(37);     # 5.06241551948512342445983930691099213
    say $rat.precise(37, :z); # 5.0624155194851234244598393069109921300
    say $rat.precise(0);      # 5

    # terminating Rats
    say (1.5**63).Str;     # 124093581919.64894769782737365038
    say (1.5**63).precise; # 124093581919.648947697827373650380188008224280338254175148904323577880859375

DESCRIPTION
===========

Augments Rat and FatRat classes with a .precise method. Stringifies configurably to a more precise representation than default .Str methods.

The .precise method can accept two parameters. A positive integer to specify the number of places of precision after the decimal, and/or a boolean flag to control whether non-significant zeros are trimmed.

In base 10, Rational fractions with denominators that are a power of 2 or 5 will terminate.

By default, the precise method stringifies terminating fractions completely. If the fraction is non-terminating, Rats return at least 16 places of precision, FatRats return at least 32 places. Any trailing zeros are trimmed.

If an integer parameter is passed, the fractional portion will be calculated to that many digits, but may have non-significant digits trimmed.

If a :z flag is passed, trailing (non-significant) zeros will be preserved.

Parameters can be in any order and combination.

Note that the .precise method only affects stringification. It doesn't change the internal representations of the Rationals, nor does it make calculations any more precise. It is merely a shortcut to express Rational strings to a configurable specified precision.

AUTHOR
======

2018 Steve Schulze aka thundergnat

This package is free software and is provided "as is" without express or implied warranty. You can redistribute it and/or modify it under the same terms as Perl itself.

LICENSE
=======

Licensed under The Artistic 2.0; see LICENSE.
