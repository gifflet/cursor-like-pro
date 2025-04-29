# Director Agent Rules for Development 🤖

This rule provides guidelines for the Director Agent, an autonomous iterative development system that helps create, execute, and evaluate code changes.

## Overview

The Director Agent is designed to handle iterative development tasks by following a structured process of code creation, execution, and evaluation until reaching the desired goal or maximum attempts.

## Key Features

- **Configuration-based**: Requires YAML configuration file
- **Iterative Development**: Systematic approach to code changes
- **Automated Evaluation**: Tests and validates changes
- **Maximum Attempts Control**: Prevents infinite loops
- **Clear Reporting**: Detailed feedback on results

## Setting Up Director Mode in Cursor

To create a custom Director mode in Cursor:

1. **Open Cursor** and click on the **mode selector** in the chat panel
2. Select **"Add custom mode"**
3. In the configuration screen:
   - **Name**: Enter `⚒️ Director` (copy-paste the hammer and wrench emoji)
   - **Model**: Select `claude-3.7-sonnet` (or any other model that supports thinking)
   - **Icon**: Choose any available icon from Cursor's predefined options (optional)
   - **Shortcut**: Add a keyboard shortcut (optional)
   - **Tools**: Enable all tools
4. Click on **Advanced options**
5. Enable `Auto-run`
6. In the text box that appears at the bottom, paste the content from the [`rules/director/director.mdc`](director.mdc)

Once configured, you'll be able to select Director mode from the mode selection menu and start using the Director Agent for your development tasks.

## How to Use Director

### 1. Activate Director Mode

**IMPORTANT:** Before using Director, you **must activate Director mode**:

1. Click on the mode selector in Cursor's chat panel (typically located at the top of the panel)
2. Select `⚒️ Director` from the list of available modes
3. Director mode will become active and the AI will be ready to process your development commands

### 2. Configuration File Structure

Required YAML structure:
```yaml
prompt: path/to/spec.md  # or direct text
execution_command: command to test code
max_iterations: 5  # maximum attempts allowed
```

### 3. Create Configuration File

```yaml
# director.yaml
prompt: specs/my-feature.md
execution_command: pytest tests/
max_iterations: 5
```

### 4. Prepare Specification

- If using file path:
  ```markdown
  # Feature: User Authentication
  
  Implement user authentication with the following requirements:
  1. JWT-based authentication
  2. Password hashing with bcrypt
  3. Email validation
  ```
- Or use direct text in the configuration file:
  ```yaml
  prompt: |
    Implement user authentication with:
    1. JWT-based authentication
    2. Password hashing with bcrypt
    3. Email validation
  ```

### 5. Run Development Cycle

With Director mode activated, send the following message to the AI:
```
Director: @path/to/your/director.yaml
```

For example:
```
Director: @specs/auth-feature.yaml
```

What happens next:
1. The AI will read your configuration file
2. It will start the development cycle:
   - Generate initial code based on the prompt
   - Run tests using the specified command
   - Evaluate results
   - If needed, iterate until success or max_iterations is reached
3. You'll see real-time updates:
   - Code being generated
   - Test results
   - Feedback from each iteration
4. The process ends when:
   - ✅ Tests pass successfully
   - ❌ Maximum iterations reached
   - 🛑 You manually interrupt

**Tips:**
- Use descriptive names: `feature-name.yaml`
- Adjust the prompt if needed between attempts

## Best Practices

1. Always provide complete configuration file
2. Use clear and specific prompts
3. Include comprehensive test commands
4. Set reasonable max_iterations limit
5. Review feedback between iterations 