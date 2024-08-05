# fsed
A wrapper around sed for safe automated find&sed-ing

fsed returns with exit code 42, if PATTERN wasn't matched and thus ACTION didn't happen.
Also supports a mode where exit code is 42 unless PATTERN was matched exactly N times.

Example usage: fsed foo 's//bar/' baz.txt

## Sources
Detailed explanation of the mechanism: https://stackoverflow.com/a/15966279

Script based on stripped down template: https://gist.github.com/Ithanil/b72d61091b73cd8cb0c33de3de593834
