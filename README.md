# rustdoc-math-example
 Example for using latex equations in rustdoc

## Quickstart

In your project's root directory, create a `doc_assets/docs-header.html` file, paste the following lines:
```html
<script async src="https://cdn.jsdelivr.net/npm/tex-math@latest/dist/tex-math.js"></script>
<script src="https://cdn.jsdelivr.net/gh/LucaCiucci/rustdoc-math-example@main/doc_assets/header-script.js"></script>
```
This code will be injected into the header of every page of your documentation. The `tex-math.js` script will provide the `<tex-math>` and `<i-math>` tags to display latex equations while the `header-script.js` script will search all the `$$...$$` and `$...$` strings in the documentation and replace them with the appropriate tags.

Now, we add the following lines to the `.cargo/Config.toml` file:
```toml
[build]
rustdocflags = [ "--html-in-header", "./doc_assets/docs-header.html" ]
```

This will tell `cargo rustdoc` command to inject the header into the documentation.

Finally, in your project's `Cargo.toml`, we add the following:
```toml
[package.metadata.docs.rs]
rustdoc-args = ["--html-in-header", "doc_assets/docs-header.html"]
```
This will tell [`docs.rs`](https://docs.rs) to inject the header into the documentation.

## Generating documentation

```bash
cargo rustdoc --open
```

## Useful links

 * https://github.com/victe/rust-latex-doc-minimal-example
 * https://github.com/arkworks-rs/algebra/pull/427