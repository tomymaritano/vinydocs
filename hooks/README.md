# Hooks Documentation

This section contains detailed documentation for Viny's custom React hooks.

## Available Hooks

### Performance
- [useDebounce](useDebounce.md) - Debounce values and callbacks
- [useSearchWorker](useSearchWorker.md) - Optimized search with Web Workers

### Form Handling
- [useFormValidation](useFormValidation.md) - Comprehensive form validation

### Error Management
- [useErrorHandler](useErrorHandler.md) - Centralized error handling integration

### Data Synchronization
- [useSync](useSync.md) - Data synchronization with conflict resolution

## Hook Patterns

All hooks in Viny follow these conventions:

1. **Prefix Convention** - All hooks start with `use`
2. **Single Responsibility** - Each hook has one clear purpose
3. **TypeScript Support** - Full type inference and safety
4. **Memoization** - Optimized to prevent unnecessary re-renders
5. **Error Handling** - Built-in error boundaries and recovery

## Usage Example

```tsx
import { useDebounce } from '@/hooks/useDebounce'
import { useFormValidation } from '@/hooks/useFormValidation'

function MyForm() {
  const [searchTerm, setSearchTerm] = useState('')
  const debouncedSearch = useDebounce(searchTerm, 300)
  
  const { errors, validate, isValid } = useFormValidation({
    rules: {
      email: ['required', 'email'],
      password: ['required', 'minLength:8']
    }
  })
  
  // Component logic...
}
```

## Best Practices

1. **Call hooks at the top level** - Never call hooks inside conditions or loops
2. **Use custom hooks for shared logic** - Extract common patterns
3. **Keep hooks focused** - One hook, one responsibility
4. **Document complex hooks** - Add JSDoc comments for complex logic
5. **Test hooks separately** - Use @testing-library/react-hooks