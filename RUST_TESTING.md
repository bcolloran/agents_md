# Rust Testing Guidelines
## Running tests
The agent should always run `cargo test` in the workspace root to run all tests in the workspace, not just the tests in the current crate. Do not pass additional flags to `cargo test` unless specifically requested by the user.

## Test file organization
Prefer to put tests in a `./tests/` subfolder next to the code being tested, rather than in the same file as the implementation code. This keeps the implementation code clean and focused, and makes it easier to find and run tests.

Try to ensure that the file organization for tests matches that of the implementation code, e.g., if functionality for `TypeY` is implemented in the file `type_y.rs`, put tests in `./tests/type_y.rs`. If there are many tests for a single file that that touch on multiple aspects, consider putting them in a subdirectories, e.g., `tests/type_y/mod.rs` with `tests/type_y/{topic_a}.rs`, `tests/type_y/{topic_b}.rs`, etc. The names should be descriptive of the functionality being tested -- describe the topic or aspect being tested.

## Do not use doctests
Tests should always be in dedicated test functions, doctests don't work well with rust-analyzer and other tools, and are harder to maintain.

## Multiple cases in one test
When it makes sense to repeatedly test a single function on multiple *input* cases, use a `#[test_case(data; "data case description")]` attribute on a test to specify the data cases. This allows the test to be run multiple times with different inputs, and will report each case separately in the test results.

This is "DRY"er than writing a separate test function for each case, and cleaner than putting multiple assertion statements in a single test function that loops over the data cases.

For example, we have this in the file `easy_hash/tests/test_utils.rs`:
```rust
#[test_case(0 ; "0u64")]
#[test_case(1 ; "1u64")]
#[test_case(u32::MAX as u64 ; "u32::MAX as u64")]
#[test_case(u64::MAX ; "u64::MAX")]
#[test_case(u64::MAX - 1 ; "u64::MAX - 1")]
#[test_case(0x1234_5678_9abc_def0 ; "0x1234_5678_9abc_def0")]
fn test_split_u64_roundtrip(val: u64) {
    let parts = split_u64(val);
    assert_eq!(join_u32s(parts[0], parts[1]), val);
}
```

## Property-based testing
When testing functions that have complex behavior over a wide range of inputs, consider using property-based testing with the `proptest` crate.