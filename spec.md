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

## dx builds on top of JavaScript syntax

dx exists to describe JavaScript code as it is written, not to invent new
features or overwrite existing syntax. For this reason you won't find
"namespaces" or "public/private". dx will also validate against your code.
For example, you can't have mismatching params in your code and comments.

```ts
/* Incrementing cat naps
 *
 * - param: `catName` `string` The name of the cat.
 * - param: `howManyMore` `number` How many naps should the cat take?
 * - returns: `number` The total number of naps the cat will take.
 */
function takeMoreNaps(howManyMore) {
  // ...
}
```

```
Error: `takeMoreNaps` only has 1 param(s), but you described 2.
```

## dx (optionally) builds on top of Flow/TypeScript syntax

dx can parse Flow and TypeScript code and will use your types as part of
the generated output.

```ts
/* Incrementing cat naps.
 *
 * - param: `howManyMore` `string` How many naps should the cat take?
 * - returns: The total number of naps the cat will take.
 */
function takeMoreNaps(howManyMore: number): number {
  // ...
}
```

```
Error: Cannot set type of `howManyMore` in comment when using Flow/TypeScript.
```

# Comments

dx is most commonly written as the content of code comments that spell out
documentation for code. Comments are interpreted as documentation based
on their placement within source code.

```js
// crashes the system
function crashTheSystem() {/* … */}
```

dx supports all [JavaScript comment styles]: multi-line comments, single-line comments,
and with or without leading `*` marks in each row. The following are equivalent:

```js
// Crashes the system

/*
 * Crashes the system
 */

/* Crashes the system */

/*
Crashes the system
*/
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
[JavaScript comment styles]: https://tc39.github.io/ecma262/#sec-comments
