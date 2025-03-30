# The Code of Conduct

Wikipedia defines a **code of conduct** as a set of rules outlining the norms,
principles, and responsibilities of an individual, party, or organization.

To standardize the style of my repositories, I created this repository to
specify the style I follow, which linters should be used, and other related
guidelines.

## Key Points

1. The maximum line length is **80 columns**, which is a strongly preferred
limit.
2. Indentation is **4 spaces** in all languages **except C**, including
**TS/JS/CSS**. Some heretical movements attempt to reduce it to **2 spaces**,
which is akin to defining **π as 3**. Use tabs in C which are 8 character wide.
3. Use **one space** around most **binary and ternary operators** (`=`, `+`,
`-`, `<`, `>`, `*`, `/`). However, **no space** should follow **unary
operators**: `&` (reference), `*` (dereference), `!` (bitwise/logical NOT),
etc.

---

### C
Follow the [Linux kernel coding style](https://www.kernel.org/doc/html/v4.10/process/coding-style.html).

### Rust
Use `cargo fmt` and have `clippy` installed.

### Python
Always apply `pyflakes` and `pylint` recommendations.

### JS/TS
Even though it is not mandatory in JavaScript, placing a **semicolon** at the
end of lines is recommended for **future-proofing** code, as potential syntax
updates may break the code by changing statement and expression rules.

Using `var` is **not recommended**. Prefer `let` or `const` whenever possible
to ensure block scoping and prevent unexpected behavior due to hoisting.

### CSS/SCSS
Group similar CSS rules **on a single line** following this order:
`display/content > size > margin/padding > position/inset > font-related rules > flex/grid properties > interaction-related rules > animation > other`.

For example:
```css
header {
    display: flex;
    margin: auto; padding: .5em 1em;
    border: .125em solid var(--bg-3);
    border-left: none; border-right: none;
    font-size: .75em; text-transform: uppercase;
    align-content: center; gap: .5em;
    user-select: none; cursor: pointer;
}
```

---

### Commit Messages
Commit messages should include a **keyword** or the name of the
**module/library/feature** that modified such as `refactor`, `feat`, `doc`,
`chore`, or `hotfix` to indicate the purpose of the commit. These keywords can
be **combined** when necessary.

You may also split commits using the **`keyword.<patch/commit version>`**
format to indicate incremental changes within a module.

#### Examples
```text
chore(refactor): dead code cleanup
minor: padding adjustments # fix typos
feat(components/DropdownMenu): expand all method
optimize(collections/binary_heap): heap_push function
optimize(collections.1): bstree push/delete functions
optimize(collections.0): linked_list unshift
protocol: event payloads for command/drone command responses
tabs: tabbed view for App element
```
