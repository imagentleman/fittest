# fittest

A lightweight in-browser unit testing library.

## Example

    <!doctype html>

    <title>Fittest Example</title>

    <script src=fittest.js></script>

    <script>
    fittest(function(test) {
      test.assert(1, 1);
      test.assert(1, '1');
    }, 'Test 1');

    fittest(function(test) {
      test.assert(2, 2);
      test.assert(true, '1');
    }, 'Test 2');

    fittest(function(test) {
      test.assert(1, { a: 2 });
      test.assert(true, [1, 2, 3]);
    }, 'Test 3');

    console.log('All tests ok?', fittest.ok());
    console.log('Tests stats', fittest.stats());
    console.log('Fittest object', fittest);
    </script>

Would print on the console:

    All tests ok? false
    Tests stats { fail: 4, ok: 2, total: 6 }
    [{
      description: 'Test 1',
      results: [
        {
          expr: "1 === 1",
          ok: true
        },
        { 
          expr: "1 === '1'",
          ok: false
        }
      ]
    }, { ... }, { ... }]

* Inspired by [tape](https://github.com/substack/tape)
* Doesn't have global harness variables (e.g. describe, it or expect functions) that may populate the scope, just a single global ```window.fittest```.
* Has a single assertion function (assert, which just does strict equals).
* Weights 475 bytes when minified and gzipped.

