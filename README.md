# direnv-gha

A quick test repo for running [direnv][1] on GitHub Actions (without a 
third-party action).

## Local usage

```
$ direnv allow .
direnv: loading ~/projects/nickcharlton/direnv-gha/.envrc
direnv: export +FOO
$ echo $FOO
foo
```

## Actions Workflow

```
- name: Setup direnv
  run: |
    sudo apt-get install direnv
    direnv allow .
    direnv exec . sh -c "echo $PATH" > "$GITHUB_PATH"
    direnv export gha >> "$GITHUB_ENV"
```

GitHub Actions specific commands come from [a comment on the direnv issues][2].

[1]: https://github.com/direnv/direnv
[2]: https://github.com/direnv/direnv/pull/910#issuecomment-1196621290
