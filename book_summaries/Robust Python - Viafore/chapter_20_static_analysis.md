# Static Analysis

Can stack multiple tools together to throw a wide safety net

## Shift Left

Idea:

- fixing an error found in Prod by a customer is costly
- developer spends time away from feature development, involve tech support and testers
- high risk for emergency deployments
- the earlier in the development cycle errors are surfaces, the less expensive to fix them
- "shift left", leveraging static analysis tools
- can be added to CI pipeline or pre-commit hooks

## Type Checkers

see previous chapters

## Linting

Linters search for common programming mistakes and style violations, e.g.

- violating PEP 8
- unreachable code
- violating access constraints (private, protected)
- unused variables, functions, imports
- missing docstrings
- common errors, e.g. mutable default value, inconsistent returns

Most commonly used in Python: `pylint`

Can write your own plugins for Pylint, e.g. to confirm business logic constraints

## Complexity Checkers

Complexitiy is subjective, different heuristics exist

`mccabe` measures cyclomatic complexity by viewing code as a control flow graph (conditional loops and branches etc.)

similarly, we can count use whitespace as a heuristic by counting indentation levels; seems no library exists yet but the book contains an example snippet

## Security Analysis

`dodgy` can be used to look out for leaked secrets

`bandit` checks for common security problems, e.g.

- HTTPS request without certificate validation
- SQL injection
- unsafe YAML loading
- weak encryption

Bandit also comes with a plugin system to write your own checks

Tools should never be the only line of defense, i.e. supplement with more practices like penetration tests
