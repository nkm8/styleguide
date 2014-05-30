## Tutorial: Add precommit hook to a project to run jshint (and more)

1. Copy the [.jshintrc](https://github.com/brandingbrand/styleguide/blob/master/javascript/.jshintrc) and [.jshintignore](https://github.com/brandingbrand/styleguide/blob/master/javascript/.jshintignore) files into the root directory of the project.
1. Install the precommit-hook module, saving it as a development dependency

    `npm i precommit-hook --save-dev`
1. **Optional:** If you would like the precommit hook to run jshint to ONLY apply to files that have been staged for commit, rather than the entire project, follow these steps.
    1. Create file `/scripts/lint_diff` containing the following code
        ```
        #!/bin/sh
        
        jshint $(git diff --cached --name-only --diff-filter=ACM | grep ".js$")
        ```
    1. chmod +x /scripts/lint_diff
1. Make the following changes to *package.json*
    1. If the `"scripts"` object exists, continue, otherwise add top level property `"scripts"`
    1. To the "scripts" object, add any number of executable commands you would like, such as `"mocha"` or `"./scripts/lint_diff"`
    1. Add top level key `"precommit"` with the value being an array of script names from the "scripts" object to be ran when `git commit` is executed.  For example, `"precommit": [ "test", "lint" ]
1. Add to *package.json* the following as a top level key
    `"precommit": [ "lint" ]`
1. Add to *package.json* the following as a property of `"scripts"`, `"lint": "jshint ."`, or if you want to only lint the diff per the optional step 2 above, then `"lint": "./scripts/lint_diff"`.

An example excerpt of a *package.json* with this information is shown below.  With this configuration, when `git commit` is executed, the test command and the lint command from scripts will be executed, and if both pass, the commit will be allowed to continue, otherwise the commit will fail.

``` json
{
    "scripts": {
        "test": "mocha",
        "lint": "./scripts/lint_diff"
    },
    "precommit": [ "test", "lint" ]
}
```

----
### Resources
- [precommit-hook](https://github.com/nlf/precommit-hook)
- [jshint](http://www.jshint.com/docs/)
    - [node module](https://github.com/jshint/jshint)
