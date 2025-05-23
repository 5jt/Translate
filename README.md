translate
=========

![translation dictionaries](dictionary-languages-translation.jpg)

An APL namespace for multilingual text support.

Function `translate.text` takes a string argument and returns it as its result a (no-op)

		  translate.text 'yesterday'
	yesterday

unless

-   `translate.dictionary` defines an equivalent string in another language
-   and the string appears in its dictionary

when the corresponding string is returned.

		  'fr' translate.text 'yesterday'
    hier
		  'de' translate.text 'yesterday'
    Gestern

Default target
--------------
You can set a default target language and omit the left argument.

		  translate.default←'fr'
		  translate.text 'yesterday'
    hier

Dictionary
----------
A dictionary is a table of equivalent strings in two or more languages, where a table is a matrix and a list of column names.

	      _testDictionary
	┌────────────────────┬──────────┐
	│┌─────┬──────┬─────┐│┌──┬──┬──┐│
	││cow  │vache │Kuh  │││en│fr│de││
	│├─────┼──────┼─────┤│└──┴──┴──┘│
	││sheep│mouton│Schaf││          │
	│├─────┼──────┼─────┤│          │
	││cat  │chat  │Katze││          │
	│├─────┼──────┼─────┤│          │
	││dog  │chien │Hund ││          │
	│└─────┴──────┴─────┘│          │
	└────────────────────┴──────────┘

The test dictionary shown above is the result of

	⎕CSV 'testDictionary.csv' 'UTF-8' ⍬ 1

Public interface
----------------
Consider objects whose names begin with an underscore `_` as internal to the namespace.
If `translate` were a class, they would be private to it.

Test suite
----------
The function `_testSuite` is niladic.
It reports in the session any tests failed and returns the number of problems found.

Help
----
The variable `translate.help` contains brief help.
