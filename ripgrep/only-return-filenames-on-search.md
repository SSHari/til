# Return Filenames on Search

By default ripgrep returns the filename and the lines that match in a given search. To change this so that only the filenames are returned use the `-l` (shorthand for `--files-with-matches`) flag.

```zsh
rg -l "return me filenames with this content in them."
```

- To invert the search and return file names for files that don't match, use the flag `--files-without-match`.
