# Fast Diff for Generic JavaScript

This is a version of [jhchen's](https://github.com/jhchen) fast-diff that doesn't require Node.
Instead, the functions are provided in a global named window.FastDiff. The code is originally
based on [diff-match-patch](https://code.google.com/p/google-diff-match-patch/) library by
[Neil Fraser](https://neil.fraser.name/).

The diff function is an implementation of
["An O(ND) Difference Algorithm and its Variations" (Myers, 1986)]
(http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.4.6927&rep=rep1&type=pdf)
with the suggested divide and conquer strategy along with several
[optimizations](http://neil.fraser.name/news/2007/10/09/) Neil added.

```js
var good = 'Good dog';
var bad = 'Bad dog';

// Regular diff:
var result = window.FastDiff.diff(good, bad);
// [[-1, "Goo"], [1, "Ba"], [0, "d dog"]]

// Diff with suggested cursor position:
window.FastDiff.diff('aaa', 'aaaa', 1)
// Result = [[0, "a"], [1, "a"], [0, "aa"]]

// For convenience
window.FastDiff.INSERT === 1;
window.FastDiff.EQUAL === 0;
window.FastDiff.DELETE === -1;
```
