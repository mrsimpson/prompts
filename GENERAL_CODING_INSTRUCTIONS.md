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


## Language and Technology Stack

- **Primary**: TypeScript with Vite and Express
- **Secondary**: JavaScript (for small scripts only)
- **Testing**: Vitest
- **Linting**: ESLint

## Coding Standards

### Naming Conventions

- **Variables and Functions**: Use camelCase
  ```typescript
  const userData = getUserInformation()
  function calculateTotalPrice(items) { /* ... */ }
  ```

- **Classes**: Use PascalCase
  ```typescript
  class UserAccount {
    // ...
  }
  ```

- **Interfaces**: Use PascalCase with descriptive names
  ```typescript
  interface UserProfile {
    id: string
    name: string
    email: string
  }
  ```

- **Constants**: Use UPPER_SNAKE_CASE for true constants
  ```typescript
  const MAX_RETRY_ATTEMPTS = 3
  ```

- **File names**: Use kebab-case for files
  ```
  user-service.ts
  auth-middleware.ts
  ```

### Code Structure

- **File Organization**: One primary concern per file
- **Function Length**: Keep functions focused and under 30 lines when possible
- **Parameter Count**: Limit to 3-4 parameters; use objects for more
- **Nesting**: Avoid deep nesting (more than 3 levels)

### Documentation

- **Use JSDoc for all public functions and classes**
  ```typescript
  /**
   * Retrieves user information from the database
   * 
   * @param {string} userId - The unique identifier for the user
   * @returns {Promise<UserProfile>} The user's profile information
   * @throws {NotFoundError} If the user doesn't exist
   */
  async function getUserProfile(userId) {
    // Implementation
  }
  ```

- **Include comments for complex logic**
  ```typescript
  // Calculate the discount based on user tier and purchase history
  const baseDiscount = userTier * 0.05
  const loyaltyBonus = purchaseHistory.length > 10 ? 0.1 : 0
  const totalDiscount = Math.min(baseDiscount + loyaltyBonus, 0.3)
  ```

### Error Handling

- **Be explicit about error cases**
- **Use custom error classes for domain-specific errors**
  ```typescript
  class ValidationError extends Error {
    constructor(message) {
      super(message)
      this.name = 'ValidationError'
    }
  }
  ```

- **Handle promises with try/catch**
  ```typescript
  try {
    const data = await fetchUserData(userId)
    return processUserData(data)
  } catch (error) {
    logger.error('Failed to process user data', { userId, error })
    throw new ProcessingError('Could not process user data')
  }
  ```

- **Use proper log levels**

  - Error: Something the user expected didn't work and the user needs to resolve it. Provide instructions of possible resolutions along with the description of the failure.
  - Warning: Something wasn't working as expected, but the system could recover. Usually, this means that the user was made aware about this via the UI.
  - Info: Use this to trace important results of a user interactions
  - Debug: Use this for traces and intermediate results which shall only be relevant during development

### Testing

- **Write tests before implementation**
- **Test the public interface, not implementation details**
- **Use descriptive test names that explain the expected behavior**

```typescript
// Example Vitest test
import { describe, it, expect } from 'vitest'
import { calculateDiscount } from './pricing'

describe('calculateDiscount', () => {
  it('should apply 10% discount for premium users', () => {
    const user = { tier: 'premium' }
    const cart = { total: 100 }
    
    const result = calculateDiscount(user, cart)
    
    expect(result).toBe(10)
  })
  
  it('should cap discount at maximum allowed value', () => {
    const user = { tier: 'vip' }
    const cart = { total: 1000 }
    
    const result = calculateDiscount(user, cart)
    
    expect(result).toBe(200) // Assuming max discount is 20%
  })
})
```