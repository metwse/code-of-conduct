# The Code of Conduct

Wikipedia defines a **code of conduct** as a set of rules outlining the norms,
principles, and responsibilities of an individual, party, or organization.

To standardize the style of my repositories, I created this repository to
specify the style I follow, which linters should be used, and other related
guidelines.

### Why?
***"many eyes"***
- I want to read your code.
- I want you to read my code.
- I want you to fix my bugs.
- I want you to change my code.
- I want to build on your code.

*You may encounter a closed pull request or `git reset --hard` if these
conventions are violated.*

## Key Points

1. The maximum line length is **80 columns**, which is a strongly preferred
limit. It is best not to exceed **79 columns** of code.
2. Indentation is **4 spaces** in all languages **except C**, including
**TS/JS/CSS**. Some heretical movements attempt to reduce it to **2 spaces**,
which is akin to defining **π as 3**. Use tabs in C which are 8 character wide.
3. Use **one space** around most **binary and ternary operators** (`=`, `+`,
`-`, `<`, `>`, `*`, `/`). However, **no space** should follow **unary
operators**: `&` (reference), `*` (dereference), `!` (bitwise/logical NOT),
etc.
4. `!important`: Get a decent file editor and do not leave trailing whitespace
at the end of lines.
5. Global items need to have descriptive names, but do not use global if you
do not really need them.

---

### C
Follow the [Linux kernel coding style](https://www.kernel.org/doc/html/v4.10/process/coding-style.html).

### Rust
Use `cargo fmt` and have `clippy` installed.

### Python
Run `pylint` over your code. Always apply `pyflakes` and `pylint`
recommendations.

Double quotes for text.\
Single quotes for anything that behaves like an identifier.\
Double quoted raw string literals for regexps.\
Tripled double quotes for docstrings.

### JS/TS
Even though it is not mandatory in JavaScript, placing a **semicolon** at the
end of lines is recommended for **future-proofing** code, as potential syntax
updates may break the code by changing statement and expression rules.

Using `var` is **not recommended**. Prefer `let` or `const` whenever possible
to ensure block scoping and prevent unexpected behavior due to hoisting.

Avoid redundant backticks. Use ' (single quotes) whenever possible. Reserve
backticks for format strings only.

`"` (double quotes) are not preferred in JavaScript. However, in HTML and JSX,
double quotes are preferred.

For example:
```jsx
function EnvironmentControl() {
    return (
        <div className={styles['control'] /* Use single quote in embeded JS */}>
            <DropdownMenu title="environment">
                <div>
                    <input placeholder="drone count" type="number"/>
                    <button>initialize environment</button>
                </div>
            </DropdownMenu>
        </div>
    );
}
```

### CSS/SCSS
Group similar CSS rules **on a single line** following this order:
`display/content > size > margin/padding > position/inset > font-related rules > flex/grid properties > interaction-related rules > animation > other`.

Avoid ID selectors. ID attributes are expected to be unique across an entire
page, which is difficult to guarantee when a page contains many components
worked on by many different engineers. Class selectors should be preferred in
all situations.

Avoid using !important declarations. These declarations break the natural
cascade of CSS and make it difficult to reason about and compose styles. Use
selector specificity to override properties instead.

*DO NOT* break responsiveness. Build the site from the ground up with a
responsive design. Use `rem` and `em` instead of `px` to maintain
responsiveness across devices with different font sizes.

Here is an example of my controversial choice of "grouping similar rules in a
single line":
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

### Casing
- Use `snake_case` in C.
- In object-oriented languages such as Python and JavaScript, **always** use
`PascalCase` for class names. No variables, functions, modules, etc., should
be named with `PascalCase`, except for React component functions.
- Preferred function/variable casing: JavaScript → `camelCase`,
Python → `snake_case`.
- Use `kebab-case` for HTML class names and IDs.

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
homepage: padding adjustments in footer / fix typos
feat(components/DropdownMenu): expand all method
optimize(collections/binary_heap): heap_push function
optimize(collections.1): bstree push/delete functions
optimize(collections.0): linked_list unshift
protocol: event payloads for command/drone command responses
tabs: tabbed view for App element
minor: update copyright year
```

### Branches
Code in the main branch must **always** work properly. ***NO*** MVP or
prototype code is allowed in either `main` or `dev`. Breaking/prototype commits
*should* be pushed to a separate branch related to the update and merged into
the `dev` branch once the feature or refactor is stabilized. Only a fully
functional and stable version in `dev` can be merged into `main`.

---

## References
- [Google styling guide](https://google.github.io/styleguide/)
- [Linux kernel coding style](https://www.kernel.org/doc/html/v4.10/process/coding-style.html).
- [Kernel process/coding-style.rst](http://www.kroah.com/linux/talks/ols_2002_kernel_codingstyle_talk/html/).
