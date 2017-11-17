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
