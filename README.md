# git-compare

Quickly compare a remote GIT repository with a local directory and identify differences


* Uses [dulwich](https://www.dulwich.io/) library

* Requires AaronO's [SSHGitClient patch](https://github.com/FriendCode/gittle/issues/18) :

> pip uninstall dulwich
> pip install 'https://github.com/AaronO/dulwich/tarball/eebb032b2b7b982d21d636ac50b6e45de58b208b#egg=dulwich-0.9.1-2'
> curl -o /usr/local/lib/python2.7/dist-packages/dulwich/refs.py https://raw.githubusercontent.com/jelmer/dulwich/dulwich-0.9.7/dulwich/refs.py

* Caches repos in ~/.cache/git-compare/*

* Example usage:

    git-compare  ssh://myuser@example.com/path/to/repo.git  /local/path/to/repo/deployment/

* Quickly identifies any extra / missing files or symlinks, and any files that don't 100% match (sha1 checksum) what's in the remote GIT repostory.

* Similar to `git checkout && git fetch && git fsck && git status` but will IGNORE all GIT-ignore-rules (~/.gitignore, .gitignore in any directory, $HOME/.config/git/ignore, $GIT_DIR/info/exclude, $XDG_CONFIG_HOME/git/ignore), so that someone can't add a rule to one of those files to hide files.

