# snpsMan2VimSyntax

_Author:_ Eric Roller<br>
_Created:_ 14th August, 2015

This Perl script parses Synopsys man pages to generate a Tcl-compatible syntax
file for vim.

## Details

Based on the [Synopsys](www.synopsys.com) man pages for one or more of these
tools installed on your system:

* Design Compiler,
* IC Compiler,
* Formality, or
* PrimeTime,

this Perl script will generate a single synopsys.vim syntax file for
[Vim](http://www.vim.org), which can be used in combination with the standard
Tcl syntax file, e.g. [tcl.vim](http://www.vim.org/scripts/script_search_results.php?keywords=tcl&script_type=syntax&order_by=rating&direction=descending&search=search).

Only the script commands in the `cat2` category are parsed.

Given that man pages follow familiar rules, this script may also be used for
other Synopsys tools, but it has been tested only for the tools listed above.

Other, pre-compiled .vim syntax files exist, but most are out-of-date. With
`snpsMan2VimSyntax`, you can generate a syntax file that matches the tool(s)
that are installed on your system.


## Using the Script

You need the Synopsys tools installed on your system. Begin by adding their
`$SYNOPSYS/bin` paths to your `$PATH`. This is necessary to be able to locate
the executables, e.g. `dc_shell`, from which the man paths can be determined.
Then run:

	snpsMan2VimSyntax -verbose

This will search for DC, FM, and PT to generate a `synopsys.vim` file.
If you like, you can use only selected tools:

	snpsMan2VimSyntax -verbose -tool dc -tool pt

For help and additional options, use:

	snpsMan2VimSyntax -help


## Installing the Syntax File

The aim is not to replace the standard `tcl.vim` file that already exists
on your system. Instead, the `synopsys.vim` file is used to extend the Tcl
syntax definitions. To do this, place the file here:

	~/.vim/syntax/synopsys.vim

Next, create this file:

	~/.vim/syntax/after/tcl.vim

and edit it to contain:

```tcl
" Vim syntax file
" NB. This file is loaded after the standard tcl.vim file.

" Include the Synopsys commands.
source ~/.vim/syntax/synopsys.vim

" Additional syntax definitions:

```

Now open one of your Tcl scripts in `vim` and make sure you use `:syntax on`
and `:set syntax=tcl`.


## License and Warranty

This script is distributed under the MIT License (MIT).
See the enclosed LICENSE file for details.
