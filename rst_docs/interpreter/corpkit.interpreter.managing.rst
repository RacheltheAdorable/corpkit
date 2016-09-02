Settings and management
========================

The interpreter can do a number of other useful things. They are outlined here.

Managing data
---------------

You should be able to store most of the objects you create in memory:

.. code-block:: bash

   > store result as 'good_result'
   > show store
   > fetch 'good_result' as result

A more permanent solution is to use `save` and `load`:

   > save result as 'good_result'
   > ls saved_interrogations
   > load 'good_result' as result

Toggles and settings
---------------------

* Using `toggle interactive`, You can switch between interactive mode, where results and concordances are shown in a way that you can manipulate directly, and non-interactive mode, where results and concordances are simply printed to the console.
* Using `toggle conc`, you can tell *corpkit* not to produce concordances. This can be much faster, especially when there are a lot of results.
* You can set the number of decimals displayed when viewing results with `set decimal to 3`

Switching to IPython
---------------------

When the interpreter constrains you, you can switch to IPython with `ipython`. Your objects are available there under the same name. When you're done there, do `quit` to return to the *corpkit* interpreter.

Running scripts
-----------------

You can also write and run scripts. If you make a file, `participants.cki`, containing:

```shell
#!/usr/bin/env corpkit

set mydata-parsed as corpus
search corpus for function matching roles.participant showing lemma
export result as csv to part.csv
```

You can run it from the terminal with:

```shell
corpkit participants.cki
# or, directly, if there's a shebang and chmod +x:
./participants.cki
```

which will leave you with a CSV file at `exported/part.csv`. This approach can be handy if you need to pipe `stdout` or `stderr`, or if you want to call *corpkit* within a shell script.

.. note::

   When running a script, interactivity will automatically be switched off, and concordancing disabled if the script does not appear to need it.
