---
name: javascript-style
description: Write or refactor JavaScript in this EMC Analyzer project using its conventions, with emphasis on clear, compact code and practical memory and runtime efficiency.
disable-model-invocation: false
---

# JavaScript Style

Use this skill when changing JavaScript in this repository, especially `src` modules, utilities, hooks, stores, APIs, and workers.

## Decision priorities

- Prefer code that is easy to understand and maintain. Keep the implementation compact by removing unnecessary indirection, duplicate work, and redundant state; do not compress code into dense expressions that obscure intent.
- Consider memory use and runtime performance while preserving correctness. Avoid needless copies, temporary arrays/objects, repeated conversions, and retained references in hot or long-lived paths. Reuse suitable buffers or data structures when that makes a measurable difference without making the code harder to reason about.
- Choose data structures and algorithms that fit the workload. Avoid repeated scans or recomputation in frequently called paths when a clear cache, index, or single-pass approach is appropriate; account for the memory cost and invalidation of caches.
- In rendering, parsing, mapping, charting, and worker code, pay particular attention to large datasets, update frequency, and object lifetime. Keep expensive work out of frequently triggered callbacks where practical.
- Do not pursue speculative micro-optimizations. Optimize identifiable cost centers and keep a straightforward implementation when performance is not material.

## Responsibility and function design

- Separate responsibilities and split long functions into cohesive, clearly named steps. Aim for no more than 50 lines per function; treat this as a practical guideline, not a reason to fragment a cohesive operation or obscure its flow.
- Prefer procedural and functional design for algorithms and data transformation: use focused functions with explicit inputs and outputs, and keep state and side effects clear. Avoid unnecessary mutation and preserve performance where copying large data would be costly.
- Use object-oriented design for lifecycle and resource management when an object owns state, coordinates operations, and creates or releases resources. Keep independent algorithmic calculations outside lifecycle classes when practical.
- When extracting functions, retain or add documentation describing their purpose, inputs and outputs, key steps, and important constraints, as appropriate to their complexity. Keep the caller readable as an overview of the workflow.

## Project conventions

- Use ES modules, single quotes, no semicolons, and the existing Oxfmt formatting (`semi: false`, `singleQuote: true`).
- Prefer `camelCase` for values and functions. Name reusable Vue composition functions `useXxx`.
- Follow nearby code for module boundaries: API calls in `src/api`, shared state in `src/stores`, reusable logic in `src/utils` and `src/utils/hooks`, and worker logic in `src/utils/workers`.
- Use the project's existing Vue, Pinia, Axios, and browser APIs rather than adding dependencies for small tasks.
- Keep comments concise and useful; Chinese comments are common in this codebase. Explain business intent or non-obvious behavior, not syntax.

## Implementation guidance

- Use `const` by default and `let` when reassignment is needed. Use arrow functions for callbacks and small module functions where consistent with surrounding code.
- Prefer `async`/`await` for sequential asynchronous flows. Preserve rejection behavior and cancellation semantics; follow the existing Axios helpers when making requests.
- Use optional chaining and nullish coalescing where they clarify handling of missing data. Do not silently change established API response or error behavior.
- Keep functions focused on a clear task. Extract shared logic when it reduces duplication or clarifies responsibilities, not simply to create more layers.
- Match surrounding file patterns and naming. Avoid unrelated formatting or structural churn while making a focused change.

## Documentation for complex code

- For complex classes or modules, add an overview near the beginning explaining their purpose, responsibilities, main workflow, and public capabilities.
- For complex methods, explain what they do, relevant inputs and outputs, the main processing steps, and important assumptions or limitations. Give readers enough context to follow the implementation rather than relying on a terse summary.
- Add comments inside non-obvious logic to explain why each significant step is needed and how it relates to the overall workflow. Keep comments accurate and avoid restating syntax.

## Verification

- Do not proactively run `npm run build` after coding. Run it only when the user explicitly requests a build.
