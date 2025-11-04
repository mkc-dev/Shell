# Alacritty Development Guide for AI Agents

## Environment
- **Platform:** Windows - use PowerShell or cmd for all commands (no bash/Unix commands)

## Build/Test Commands
- **Build:** `cargo build` (debug) or `cargo build --release` (optimized)
- **Test:** `cargo test` (all tests) or `cargo test -p <package>` (specific workspace package)
- **Test single package without default features:** `cargo test -p alacritty_terminal --no-default-features`
- **Lint:** `cargo clippy --all-targets` (ensure clippy component is installed)
- **Format:** `rustfmt` (follows rustfmt.toml configuration)

## Project Structure
Rust workspace with packages: `alacritty`, `alacritty_terminal`, `alacritty_config`, `alacritty_config_derive`

## Code Style Guidelines
- **Edition:** Rust 2024, MSRV 1.85.0
- **Imports:** Module-level granularity, group std/external/internal with blank lines
- **Naming:** snake_case for functions/variables, PascalCase for types, SCREAMING_SNAKE_CASE for constants
- **Error handling:** Use `Result<T, Box<dyn Error>>` pattern, avoid unwrap() in production code
- **Comments:** Doc comments with `///`, wrap at 100 chars, normalize attributes
- **Formatting:** Follow rustfmt.toml: Unix newlines, field init shorthand, try shorthand, trailing commas
- **Lints:** Enable `#![deny(clippy::all, clippy::if_not_else, clippy::enum_glob_use)]`
- **Dependencies:** Prefer workspace.dependencies for version consistency across packages