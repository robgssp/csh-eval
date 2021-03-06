csh-eval [![Circle CI](https://circleci.com/gh/ComputerScienceHouse/csh-eval.svg?style=svg)](https://circleci.com/gh/ComputerScienceHouse/csh-eval)
=========
An evaluations platform for the Computer Science House at RIT.

## Project Goals
- Maintainablility: Should be easy to refactor with confidence.
- Extensibility: Should be easy to extend or modify existing features and
                 integrate with other services.
- Usability: Site should have intelligent design decisions with real use cases
             in mind.

## Setup for development

- Add `~/.local/bin` to your `PATH`
- Install PostgreSQL (we have been using 9.4)
- Build and install `stack install`
- Add autocomplete for `csh-eval`: `source <(stack --bash-completion-script $(which stack))`
- Run tests: `stack test`
- Build documentation: `stack haddock`
- Initialize the database:
	- Create a user called "pvals": `createuser pvals`
	- Create a database called "pvals" owned by the pvals user: `createdb pvals -O pvals`
	- Initialize the schema: `csh-eval initdb <HOST> <PORT> <USER> <DB>`
- Try starting the site: `csh-eval members`. You should find it running on `localhost:8000` by default.

## Contributing

### Discussion
General coordination and discussion takes place in #pvals on cshrit.slack.com.
An `@*rit.edu` address is required to chat. Longer form discussion for specific
features will occur under issues on the ComputerScienceHouse Github.
Bugs and feature requests may also be made through Github issues.

### Issue Tracking
If you are working on a feature or patch for the project, make an issue on the 
ComputerScienceHouse github issue tracker, and assign yourself to it. Unassigned 
tasks are assumed to be fair game, and may in theory be picked up by anyone. If an
issue is unclear, ask for clarification!

### Review Process
Github pull requests are used as a code review mechanism. All commits must be
sent as pull requests, typically from topic branches in contributors' forks.
Pull requests may not be merged into this repository's master branch by the requestor,
this ensures that at least one other contributor with push access has
reviewed the code. Pull requests are built and tested by circleci. Pull requests may not
be merged until the circle build status is known.

### Testing and Documentation
All functions must have at least one doctest example in their docstring.
All pure Haskell functions must be accompanied by QuickCheck props. All impure
functions must be accompanied by HUnit tests. All pure SQL must be accompanied
by offerings to the deity of the contributor's choosing, proportional in
extravagance to the complexity of the SQL's behavior.

### Versioning
No guarantees are made with regards to the stability (or sanity) of this
repository's master branch. Please checkout the latest tagged commit for
deployment purposes.
