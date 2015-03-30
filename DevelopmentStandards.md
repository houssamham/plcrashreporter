# Introduction #

This page covers our development standards -- for related information on versioning and releases, see VersioningStandards.

Our development standards are short and sweet:

## Unit Testing ##

Short version: It's required.

Longer version: Write tests at the same time you write the code, as this is when you have the best understanding of the potential failure cases and bugs that may be in residence. Tests that are added later are invariably cursory; it's much, much harder to fully comprehend a complex system to the degree that you did when writing it.

Specific requirements:

  * All non-UI code should be unit tested.
  * If it can't be unit tested, figure out how it can be.
  * If it still can't be unit tested, write an integration test for it.
  * When reviewing code, make sure it's tested.

## API Documentation ##

Short version: It's required.

Longer version: Write documentation at the same time you write the code, for the exact same reason as we require test-driven development. Programming languages -- especially ones with lackluster type systems -- are simply incapable of expressing the full set of invariants of a piece of code. The best time to explain those invariants are when you have them in mind, as you're writing the code in question.

Additionally, documenting code will often reveal bugs and design flaws, as it forces you to think through the systemic invariants of the code you're writing, and how it fits into the larger whole.

We currently use doxygen syntax, which is largely compatible with clang's new -Wdocumentation flag and documentation parser. We may switch to another clang-based documentation generator at a future date.

Specific requirements:
  * **All** code must be documented. Classes methods, functions, parameters, constants.
  * Document code at the time you write it. That's when you'll write the most useful documentation.
  * If you need to express something that is more complex than can be expressed in basic API documentation, use doxygen's support for distinct documentation pages, and write up higher-level documentation.
  * When reviewing code, make sure it's documented in full.

## Code Review ##

All feature branches will be subject to peer code review before merging to master.