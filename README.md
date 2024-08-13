# fsed
A wrapper around sed for safe automated find&sed-ing

fsed returns with exit code 42, if PATTERN wasn't matched and thus ACTION didn't happen.
Also supports a mode where exit code is 42 unless PATTERN was matched exactly N times.

Example usage: fsed '/foo/' 's//bar/' baz.txt

## Sources
Detailed explanation of the mechanism: https://stackoverflow.com/a/15966279

Script based on stripped down template: https://gist.github.com/Ithanil/b72d61091b73cd8cb0c33de3de593834

## Examples

1) Substitute pattern and verify:

`fsed '/foo/' 's//bar' baz.txt && echo "Found" || "Not found"`

2) Delete pattern and verify number of matches

`fsed -c 1 '/foo/' 'd' baz.txt && echo "Exactly 1 match" || echo "Not exactly 1 match"`

3) Substitution with different pattern / action delimiters:

`fsed '\|foo|' 's!!bar!' baz.txt`

4) (Caveat!) Append a line (requiring explicit line breaks):
```
fsed '/foo/' 'a\
appended bar line
' baz.txt
```

5) In-place edit without following symlinks (i.e. default sed behavior):

`fsed -i --no-follow-symlinks '/foo/' 's//bar' baz.link`
