# git-good-commit

Git hook to help you write good commit messages.

Validates commit messages conform to six of [the seven rules of a great git commit message](http://chris.beams.io/posts/git-commit/), plus a couple of extras:

1. [Separate subject from body with a blank line](http://chris.beams.io/posts/git-commit/#separate)
2. [Limit the subject line to 50 characters](http://chris.beams.io/posts/git-commit/#limit-50)
3. [Capitalize the subject line](http://chris.beams.io/posts/git-commit/#capitalize)
4. [Do not end the subject line with a period](http://chris.beams.io/posts/git-commit/#end)
5. [Use the imperative mood in the subject line](http://chris.beams.io/posts/git-commit/#imperative)
6. [Wrap the body at 72 characters](http://chris.beams.io/posts/git-commit/#wrap-72)
7. ~~[Use the body to explain what and why vs. how](http://chris.beams.io/posts/git-commit/#why-not-how)~~ _- you're on your own with this one_
8. Do no write single worded commits
9. Do not start the subject line with whitespace

## Installation

### Single repository

At the root of the repository, run:

```sh
curl https://raw.githubusercontent.com/noelmansour/git-good-commit/master/hook.sh > .git/hooks/commit-msg && chmod +x .git/hooks/commit-msg
```

### Globally

To use the hook globally, you can use `git-init`'s template directory:

```sh
mkdir -p ~/.git-template/hooks
git config --global init.templatedir '~/.git-template'
curl https://raw.githubusercontent.com/noelmansour/git-good-commit/master/hook.sh > ~/.git-template/hooks/commit-msg && chmod +x ~/.git-template/hooks/commit-msg
```

The hook will now be present after any `git init` or `git clone`. You can [safely re-run `git init`](http://stackoverflow.com/a/5149861/885540) on any existing repositories to add the hook there.

---

_If you're security conscious, you may be reasonably suspicious of [curling executable files](https://www.seancassidy.me/dont-pipe-to-your-shell.html). In this case you're on HTTPS throughout, and not piping directly to execution, so you can check contents and the hash against MD5 `32dd8bb7163fa44bde41e2a4b6329aa1` for latest from master._

### CI

`ci-hook.sh` can be used for CI builds. It behaves the same as `hook.sh` but simply exits on failure with a non-zero status code.

## Credits

* http://chris.beams.io/posts/git-commit
* http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html
* https://www.git-scm.com/book/en/v2/Distributed-Git-Contributing-to-a-Project#Commit-Guidelines
* Tim Perry's excellent [git-confim](https://github.com/pimterry/git-confirm) hook, which provided the inspiration and much of the scaffolding for this hook.
