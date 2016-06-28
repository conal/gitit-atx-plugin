This [Haskell](http://haskell.org)-based project is a simple [gitit](http://gitit.net/) plugin that restores ATX-like section headers in the presence of Markdown+LHS.

I upgraded gitit and found that my "##"-style headers don't work when the format is Markdown+LHS.
Apparently, the change is meant to allow Haskell programs with CPP directives to also work with Markdown+LHS.

This behavior is a change to Pandoc for [Better support for literate haskell](https://github.com/jgm/pandoc/issues/51).
The alternative Markdown header syntax using dashes or strings of equal signs allows level one and two indentation.

A workaround to precede headers with one or more equal signs.
See [Use '=' instead of '#' for atx-style headers in markdown+lhs](https://github.com/jgm/pandoc/pull/1689).

So that I don't have to fix *all* previous journal pages, I made another gitit plugin that recognizes the old style and converts it.

Compile the project with `cabal install`.
Then add it to your gitit plugins list.
For instance, my wiki's `config` file contains the following line:

    plugins: Network.Gitit.Plugin.ReviveATX

You can list additional plugins.  Separate by commas.

Finally, restart your gitit wiki, e.g.,

    gitit -f config

If everything works, the start-up messages will include the following:

    Loading plugin 'Network.Gitit.Plugin.ReviveATX...
    Finished loading plugins.
