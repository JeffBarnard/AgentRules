---
applyTo: "**/*.cs"
---

# C# Coding Conventions
- Favor Microsoft documentation over third-party sources when explaining c# features or best practices
- Be aware of .net version differences, and ensure compatibility with the project's target framework, prefer newer .net core features when possible
- Prefer native Microsoft libraries and packages over third-party alternatives unless a specific need is identified
- Use file-scoped namespaces in C# 10 and later for less indented files
- Use string.Empty instead of empty literal ""
- Use platform specific constants such as Environment.NewLine
- Keep using directives organized, at the top of the source file, and remove any unused directives. This will help keep the code clean

- Place comments on a separate line above, not at the end of a line of code
- Begin comment text with an uppercase letter.
- Insert one space between the comment delimiter (//) and the comment text
- Do not create formatted blocks of asterisks around comments

# Memory
- Every time you += an event handler, ensure -= is applied when it's no longer in scope to prevent memory leaks, this is often done in a Dispose() method

# Unit tests
- Use MSTest as the testing framework
- Use Moq for mocking dependencies in unit tests
- Add comments for Arrange, Act, Assert sections in tests
- Use unit test names that follow the pattern Entity_WhenCondition_ThenExpect