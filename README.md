prettier mirror
===============

Mirror of prettier package for pre-commit.

For pre-commit: see https://github.com/pre-commit/pre-commit

For prettier: see https://github.com/prettier/prettier


### Using prettier with pre-commit

Add this to your `.pre-commit-config.yaml`:

```yaml
-   repo: https://github.com/pre-commit/mirrors-prettier
    rev: ''  # Use the sha / tag you want to point at
    hooks:
    -   id: prettier
```

*note*: only prettier versions >= 2.1.0 are supported

When using plugins with `prettier` you'll need to declare them under
`additional_dependencies`. For example:

```yaml
-   repo: https://github.com/pre-commit/mirrors-prettier
    rev: ''  # Use the sha / tag you want to point at
    hooks:
    -   id: prettier
        additional_dependencies:
        -   prettier@2.1.2
        -   '@prettier/plugin-xml@0.12.0'
```

By default, all files are passed to `prettier`, if you want to limit the
file list, adjust `types` / `types_or` / `files`:

```yaml
    -   id: prettier
        types_or: [css, javascript]
```

### Pre-releases and autoupdate

Because pre-commit cannot make difference between alpha- and other
pre-releases, this hook is not compatible with `pre-commit autoupdate`, nor can
you install the latest stable version by using `rev`. Instead, to install the
latest version, you need to specify under `additional_dependencies` together
with the highest stable version of prettier which this hook can install, which
is `2.7.1`:

```yaml
-   repo: https://github.com/pre-commit/mirrors-prettier
    rev: '2.7.1'
    hooks:
    -   id: prettier
        additional_dependencies:
        -   prettier@2.8.4
```

In the above example, `pre-commit autoupdate` will overwrite `rev` with a
pre-release, you should manually reset that to `2.7.1`, and instead manually
look up the latest version of prettier and update the `additional_dependencies`
specification.

