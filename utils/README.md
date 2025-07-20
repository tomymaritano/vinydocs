# Utils Documentation

This section contains detailed documentation for Viny's utility functions and modules.

## Available Utilities

### Error Management
- [Error Handler](errorHandler.md) - Centralized error handling with classification

### Data Management
- [Sync Manager](syncManager.md) - Data synchronization with conflict resolution
- [Search Utils](searchUtils.md) - Search optimization and highlighting

### Formatting
- [Date Utils](dateUtils.md) - Date formatting with localization support

### Development
- [Logger](logger.md) - Advanced logging system with performance tracking

## Utility Architecture

All utilities in Viny follow these principles:

1. **Pure Functions** - No side effects when possible
2. **Type Safety** - Full TypeScript support with generics
3. **Tree Shakeable** - Individual exports for optimal bundle size
4. **Well Tested** - Comprehensive unit test coverage
5. **Performance First** - Optimized for speed and memory

## Usage Examples

### Error Handler
```typescript
import { handleError, ErrorType } from '@/utils/errorHandler'

try {
  await riskyOperation()
} catch (error) {
  const { type, message, details } = handleError(error)
  
  if (type === ErrorType.NETWORK) {
    // Handle network errors
  }
}
```

### Date Utils
```typescript
import { formatDate, getRelativeTime } from '@/utils/dateUtils'

const formatted = formatDate(new Date(), 'long') // "January 20, 2025"
const relative = getRelativeTime(Date.now() - 3600000) // "1 hour ago"
```

### Logger
```typescript
import { logger, createLogger } from '@/utils/logger'

const moduleLogger = createLogger('MyModule')
moduleLogger.debug('Debug information')
moduleLogger.error('Error occurred', { details: errorData })
```

## Best Practices

1. **Import only what you need** - Use named imports
2. **Handle errors gracefully** - Always use try-catch with async utilities
3. **Respect immutability** - Don't mutate input parameters
4. **Use TypeScript** - Leverage type inference and safety
5. **Check performance** - Profile utilities in critical paths