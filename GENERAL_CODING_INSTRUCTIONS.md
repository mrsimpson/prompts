# LLM Coding Instructions

This document provides instructions for generating code that adheres to my development standards and preferences. Follow these guidelines when producing any code.

## General Principles

1. **Prioritize readability over brevity**
   - Write verbose, clear code rather than compact, clever solutions
   - Use descriptive variable and function names
   - Break complex operations into smaller, well-named steps

2. **Keep solutions simple**
   - Avoid unnecessary complexity
   - Don't use higher-order functions, complex patterns, or advanced language features unless explicitly requested
   - Prefer straightforward imperative code when possible

3. **Follow a structured development approach**
   - First analyze requirements and plan a minimal solution
   - Document the solution design and API
   - Write tests that validate the interface
   - Implement the actual code

## Development Process

1. **Requirements Analysis**
   - Understand the problem completely before coding
   - Do implement the minimum required solution. Do not invent features or capabilities which have not been asked for
   - If you think that additional features would be reasonable, describe them as optional and ask whether you should include them
   - Identify edge cases and constraints
   - Define clear inputs and outputs
   - Present options of alternatives prior to going for one of them

2. **Documentation First**
   - Document the interface and behavior before implementation
   - Use JSDoc to define parameters, return types, and exceptions

3. **Test-Driven Development**
   - Write tests that validate the expected behavior
   - Ensure tests cover normal cases, edge cases, and error conditions

4. **Implementation**
   - Write clear, simple code that passes the tests
   - Prioritize readability over optimization
   - Add comments for complex logic. Describe what the responsibility of the artifact is, not how it is implemented!
