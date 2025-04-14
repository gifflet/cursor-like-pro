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

## Configuration File

Required YAML structure:
```yaml
prompt: path/to/spec.md  # or direct text
execution_command: command to test code
max_iterations: 5  # maximum attempts allowed
```

## How to Use

1. **Create Configuration File**
   ```yaml
   # director.yaml
   prompt: specs/my-feature.md
   execution_command: pytest tests/
   max_iterations: 5
   ```

2. **Prepare Specification**
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

3. **Run Development Cycle**
   
   To activate Director mode, send the following message to the AI:
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