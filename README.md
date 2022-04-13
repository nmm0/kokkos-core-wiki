# Kokkos Documentation

## Building the Documentation

To build the documentation, ensure that you have all build reequirements installed (it is a good idea to use a virtual environment):

```
pip install -r requirements.txt
```

Then build according to your desired target, e.g.:

```
make html
```

or, if you have latex installed,

```
make latexpdf
```

## View the HTML Documentation Locally

You can view the html documentation locally by navigating to `build/html` after runnning `make html`, and running the python http server: `python3 -m http.server`. Then, in your web browser, navigate to [http://localhost:8000](http://localhost:8000).

## Documentation Writing Reference

The documentation is written using the [Sphinx](https://www.sphinx-doc.org/en/master/) documentation generator. Sphinx primarily supports [reStructuredText](https://docutils.sourceforge.io/rst.html), but our build has support for Markdown via the [MyST](https://myst-parser.readthedocs.io/en/latest/sphinx/intro.html) plugin. For directives that Sphinx adds, see the documentation on [directives](https://www.sphinx-doc.org/en/master/usage/restructuredtext/directives.html). All of these resources can be used as a reference when writing documentation.

### Style Guide

### In-block Headings

When writing documentation for a `class` or other block directive, you cannot use standard rst headings to mark sections of functions or groups is a good alternative. See the rst documentation for View as an example.

#### New or Deprecated Features

New features should be marked in their relevant documentation section with the `versionadded` or `versionchanged` directive:

```rst
.. versionadded:: 3.7

  A swanky new Kokkos 3.7 feature.

.. versionchanged:: 4.0

  This function has an overload that takes ``std::string_view`` now that we have C++17 support!
```

Similarly, if a feature is deprecated we can use the `deprecated` directive.

```rst
.. deprecated:: 5.4

  ``DualView`` will be deprecated in the next release.
```
