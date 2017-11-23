# Introduction

## What is dx?

dx is a format for inline code documentation of the ECMAScript family of languages.
It allows for people-oriented descriptions of what software is and what it does
to complement and interact with processing-oriented code.

dx annotations in code can be extracted to generate API documentation, documentation
integrated into text editors, and more.

## Why is a spec needed?

dx is a new format that intends to spur multiple compatible implementations. It also
will be authored by many people, and needs strict rules to unambiguously set
expectations for what formatted inputs will produce as output.

# Preliminaries

## dx is a CommonMark superset

Any valid CommonMark text is also valid dx. dx extends CommonMark syntax to add
documentation-related features as well as specific guidance for the positioning
of documentation comments amongst source code.

# Comments

dx is most commonly written as the content of code comments that spell out
documentation for code. Comments are interpreted as documentation based
on their placement within source code.

```js
// crashes the system
function crashTheSystem() {/* … */}
```

**Differences**: Unlike JSDoc, comments do not need to start with `/**` and
can be single-line C-style comments.

# Structure

## Tags

dx documentation includes structured, tagged content that describes
specific attributes of source code. The tags in a documentation comment are represented
in a backwards-compatible way to CommonMark lists and a format inspired by
[mdconf]. A tag is a list item in which the first word ends with a `:` character.
For example:

```md
- param: `teamName` `string`
- returns: `string` the team's name
```

**Diferences**: Unlike JSDoc, tags do not start with `@` and instead follow
Markdown's list syntax.

## Examples

CommonMark code blocks are treated as examples:

```js
/*
 * Starts the dance party.
 *
 * ```js
 * initDanceParty()
 * ```
 */
```

If you want to add a description to the example, you can use CommonMark
[info strings].

```js
/*
 * Starts the dance party.
 *
 * ```js Turning it up to 11.
 * initDanceParty({ turnItUpTo: 11 })
 * ```
 */
```

### References

[mdconf]: https://github.com/tj/mdconf
[info strings]: http://spec.commonmark.org/0.28/#info-string
