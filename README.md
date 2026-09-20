# GitVersion playground

A minimal workflow sandbox for exercising GitVersion calculation and release behavior without
imposing an application or .NET project structure.

## Workflow

The `ci` workflow runs for pull requests targeting `main`, pushes to `main` and manual dispatches.
It:

1. lints repository content;
2. calculates a version without creating a release;
3. validates the reusable workflow's version outputs; and
4. creates an immutable release only for the default branch after every validation succeeds.

This is not a GitHub Action repository, so releases use plain `MAJOR.MINOR.PATCH` tags. They do not
use a `v` prefix or maintain a floating major alias.

## Development

Edit [`GitVersion.yml`](GitVersion.yml) to try branch or versioning behavior, then open a pull
request or manually dispatch the workflow. Pull requests calculate and validate a version but
cannot create tags or releases.

Run the static repository checks locally with:

```console
pre-commit run --all-files
```

No Dev Container is tracked because this workflow-only sandbox has no repository-specific runtime
or local toolchain beyond standard Git and optional `pre-commit`.

## Support and license

Use GitHub issues for questions about the sandbox. Report security concerns through the
repository's Security tab rather than a public issue.

This project is available under the [MIT License](LICENSE).
