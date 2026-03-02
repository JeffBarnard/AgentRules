# Use custom instructions

Copilot instructions enable you to define common guidelines and rules that automatically influence how AI generates code and handles other development tasks. Instead of manually including context in every chat prompt, specify custom instructions in a Markdown file to ensure consistent AI responses that align with your coding practices and project requirements.

You can configure custom instructions to apply automatically to all chat requests or to specific files only. Alternatively, you can manually attach custom instructions to a specific chat prompt.

Copilot instructions enhance code quality and reduce Aikido issues. They are automatically ingested by the agent in Visual Studio or VS Code for every prompt, resulting in more consistent results regardless of which models are used.



> Instructions are repository specific and must be placed in a root .\_github\_ folder.

https://docs.github.com/en/copilot/how-tos/configure-custom-instructions/add-repository-instructions



The more complete the examples, the better, and the agents understand code snippets. If we find ourselves correcting agents, adding PR comments, or yelling at Aikido, just add a new rule for next time! We can expand these instructions for things like logging, telemetry, or other project conventions.



Community examples

https://github.com/github/awesome-copilot/blob/main/README.md



The option should be enabled by default in the latest VS product families, though developers should double check to be sure:\
https://learn.microsoft.com/en-us/visualstudio/ide/copilot-chat-context?view=visualstudio#use-custom-instructions \
https://code.visualstudio.com/docs/copilot/customization/custom-instructions
