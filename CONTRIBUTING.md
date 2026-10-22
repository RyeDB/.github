# Contributing

Thanks for helping. Short version:

1. Open an issue first for anything larger than a small fix, so we can agree on the shape.
2. Fork or branch, make a focused change, and keep the diff small.
3. Run the repository's checks before pushing (`npm run typecheck && npm test` in the TypeScript repositories). A change that breaks them will not be merged.
4. Open a pull request using the template. Say what changed, why, and how you tested it.

## Ground rules

- **Tests with behaviour changes.** A fix comes with a test that fails without it.
- **No unconfirmed claims.** Do not describe something as shipped, secure or fast unless a test or measurement in the repository shows it.
- **Security issues are not public issues.** See [SECURITY.md](SECURITY.md).
- **Licence.** By contributing you agree your work is licensed under Apache-2.0.

## Commit messages

Imperative mood, a short subject line, and a body that explains why when it is not obvious.
