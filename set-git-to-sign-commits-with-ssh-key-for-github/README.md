# Set git to sign commits with SSH key for GitHub

## Configure Git to use SSH to sign commits and tags

```sh
git config --local gpg.format ssh
```

## Set signing key

```sh
git config --local user.signingkey /PATH/TO/.SSH/KEY.PUB
```

## Configure Git to sign all commits by default

```sh
git config --local commit.gpgsign true
```

## Configure globally

```sh
git config --global ${OPTIONS}
```

## References

- [GitHub - Telling Git about your signing key](https://docs.github.com/en/authentication/managing-commit-signature-verification/telling-git-about-your-signing-key)
