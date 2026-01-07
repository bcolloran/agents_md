# Tests
- When writing tests for numerical functions and physical dynamics, avoid hardcoding expected numerical values for arbitrary configurations. These are extremely hard for a human to understand and interpret, as they often require doing mental computations; moreover, there are often floating point precision issues that make exact comparisons brittle. Instead:
  - Specify equilibrium or edge cases where expected values can be derived analytically for simple cases and special constants (0, 1, -1, `pi`, `e`, etc). Tests like "at equilibrium, some quantity should be zero" or "given this special input configuration, we expect this special value" are easy to understand and verify.
  - Encode system invariants and properties that should hold true regardless of specific numbers with inequality checks or relative comparisons. For example, "after applying a force, the velocity should increase" is easy to understand and verify.
    - Inequalities relative to zero (sign checks) are particularly easy to understand.
    - Relative checks on monotone functions are pretty good.
    - Checks relative to special and edge case values (0, 1, -1, pi, etc) are also good.
- Using the `proptest` framework to generate random configurations is a good way to cover a wide range of scenarios without hardcoding specific numerical values.