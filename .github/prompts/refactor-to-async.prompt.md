---
name: Refactor-To-Async
description: Converts synchronous C# methods to asynchronous
tools: [chat]
---

You are an expert C# developer. Review the selected code and refactor all synchronous database calls to asynchronous (`async/await`) patterns.
1. Change method signatures to return `Task<T>` or `Task`.
2. Use `await` for methods like `ToListAsync()`, `FirstOrDefaultAsync()`, etc.
3. Keep the original logic and error handling intact.

Code:
{{clipboard}}
