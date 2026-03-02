---
applyTo: "**/*.razor"
---

# Blazor Coding Conventions
- Don't recommending adding third-party libraries without first checking if the functionality is available in .NET or Blazor itself.
- Don't include boostrap or other css frameworks without asking first
- Don't default to using JavaScript interop for tasks that can be accomplished with Blazor or .NET features.
- Don't overuse StateHasChanged(); understand the component lifecycle and use it judiciously to optimize performance.
