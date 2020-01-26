# github-keys

This is a script meant to be used with the `AuthorizedKeysCommand` in your `sshd` configuration. It will read a list of usernames from a user's `~/.ssh/github_users` file, and attempt to fetch the appropriate keys from the GitHub ssh keys endpoint (`https://github.com/<username>.keys`).

When properly configured, that means that if you want to permit users Bob and Alice to log into your system, you simply need to add their github usernames to a `github_users` file:

```
cat > ~/.ssh/github_users <<EOF
bob
alice
EOF
```

`github-keys` caches both positive and negative results in order to avoid repeated requests to GitHub. You can adjust the cache expiration time on the command line.
