# Style guide

If you are using a linter, here is a snippet you can add into the linter configs.

```yaml
pep8:
  options:
    max-line-length: 120
  disable:
    - E127

pep257:
  disable:
    - D213
    - D105
    - D406
    - D407

pylint:
  run: false
  options:
    max-line-length: 120
    disable:
      - too-many-ancestors
      - too-few-public-methods
      - invalid-unary-operand-type
```

This is a style **guide**, not rules. There will be exceptions and use your
best judgement when you need to.

As a quick reference, the above rules are explained below. 

* max-line-length is for readability reasons. If the code needs to be scrolled
  horizontally, it's nested too deep, variable names are too long etc.; usually
  a sign of bad code.
* E127 - explains indentation in long arguments to functions.
* D213 - Style check for multi-line docstrings
* D105 - Don't throw linter errors for missing docstrings in dundermethods. 
* D406 - Section name should end with a newline
* D407 - Missing dashed underline after section. 

More information regarding the error codes can be found here: [For
pep8](https://www.python.org/dev/peps/pep-0008/), [For
pep257](http://www.pydocstyle.org/en/2.1.1/error_codes.html), [For
pylint](http://pylint-messages.wikidot.com/all-messages). 

# Git workflow

* All pull requests must be submitted to the devel branch. 
* Preferred way is to fork the repo (only devel branch, if you are primarily a
  contributor)
* Create a branch, to focus on the aspects you wish to work on.
* Submit a pull request to devel. 
* It will be reviewed and merged into devel. 
* After tests and bug fixes, it will be merged into master for release.

The reason for this is that `master` will always be ready for end users and be
stable, without any unexpected bugs and issues (hopefully). `devel` is for
continuous testing and development and to catch bugs before they reach the end
user. Everything else is to keep the code history nice and traceable. 

## Some gotchas

* Before you start working on an issue or feature, check if your local repo is up
  to date with the remote. Run `git pull` on `devel`. Or run `git pull origin
  devel`. Then create a branch and continue working. 
* Before pushing the changes (but after committing them), do a `git pull origin
  devel` again to account for changes from others since you began. Then run
  `git rebase devel <your_branch>`. For more detailed explanation, read `man
  git-rebase`.

