# The Code of Conduct
Wikipedia defines a code of conduct as a set of rules outlining the norms, 
principles, and responsibilities of an individual, party, or organization.

To standardize the style of my repositories, I created this repository to 
specify the style I follow, which linter should be used, and other related 
guidelines.

## Key Points
1. The limit on the length of lines is 80 columns and this is a strongly 
preferred limit.
2. Indentations are 4 characters no matter what the language, including 
TS/JS/CSS. Some heretical movements attempt to reduce it to 2 characters deep,
and that is akin to trying to define the value of PI to be 3.
3. Use one space around most binary and ternary operators, suck as `=`, `+`, 
`-`, `<`, `>`, `*`, `/`. But no space after unary operators: `&` (reference), 
`*` (dereference), `!` (bitwise/logical not)...

### C
I explicitly follow the (Linux kernel coding style)
[https://www.kernel.org/doc/html/v4.10/process/coding-style.html].

### Rust
I always format my code with `cargo fmt`. Also get clippy installed.

### Python
I always apply `pyflakes` and `pylint` recommations.

### JS/TS
Even though it is not mandatory in JavaScript, placing a semicolon at the end 
of lines is recommended for future-proof code, as potential syntax updates may
break the code by changing statement and expression rules.\
Using `var` is not recommended. Prefer `let` or `const` whenever possible to 
ensure block scoping and prevent unexpected behavior due to hoisting.

### CSS/SCSS
I group similar CSS rules in a single line. I usually follow this order:
`display/content > size > margin/padding > position/inset > font-releated 
rules > flex/grid properties > interaction-related rules > animation > other`.

for example
```
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

### Commit Messages
Commit messages should include keywords such as `refactor`, `feat`, `chore`, or
`hotfix` to indicate the purpose of the commit. These keywords can be combined 
when necessary.\
You may also split commits by using the `keyword.<patch/commit version>` format
to indicate incremental changes within a module.

Examples\
`chore(refactor): dead code cleanup`\
`minor: padding adjustments # fix typos`\
`feat(components/DropdownMenu): expand all method`\
`optimize(collections/binary_heap): heap_push function`\
`optimize(collections.1): bstree push/delete functions`\
`optimize(collections.0): linked_list unshift`
