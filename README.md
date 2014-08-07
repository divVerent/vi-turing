vi-turing - vi is Turing complete!
==================================

vi-turing is a Turing Machine interpreter written in form of vi keyboard macros.
This proves that - given enough scratch space - vi macros are Turing complete!

Usage
=====

* Open vi-turing.vi in your favorite vi (ex-vi, nvi, elvis, vim are currently
  supported).
* Load vi-turing.vi's macros: `ESC :source % RETURN`
* Initialize: `\I`
* Run: `\\`

Lessons learned
===============

The following quirks of different vi versions were encountered during
development of this:

* In ex-vi, you cannot yank from within a nontrivial macro. Example:
  `:map \a yl`, `:map \\ \ap` -> beep, "p" will not paste anything.
* In ex-vi, you cannot paste from any register other than the default one
  from within a macro. Example: `:map \\ "ayl"ap` -> "Can't put partial line
  inside macro".
* In elvis, `@@` only executes unnamed registers. `"ayl@@` does not work there.
* In ex-vi, you cannot use marks from within a nontrivial macro.
* vi implementations do not agree on where the cursor is put after pasting
  from a register.
  * ex-vi: last character of the paste.
  * nvi: first character of the paste.
  * elvis: last character of the paste.
  * vim: last character of the paste.
* 
