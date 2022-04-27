# Version control

## Commit messages should be written to a specified shape, to categorise and convey intent

A commit message should take the following form:

```
category: short description of what this commit does when applied

Closes #123

More meaningful description. This part is optional, but can be used to provide context to others on why you made this decision, or how to integrate.
```

The first line of a commit message is mandatory, and should describe what applying the commit does. Some examples of good commit messages:

+ `fix: apply margin to user dropdown to avoid logo overlap`
+ `feat: user account deletion`
+ `build: upgrade dependencies`
+ `perf: lazy load product list`
+ `test: user account deletion`

Further information inside a commit message is optional. Any tagged issues should come at the start of the description, used by some version control systems to automatically close/reference issues.

This type of commit message is referred to as [conventional commits][conventional-commits].

Try to avoid telling jokes or adding emoji into a commit message.

[conventional-commits]: https://www.conventionalcommits.org
