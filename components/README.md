# Components Documentation

This section contains detailed documentation for Viny's UI components.

## Available Components

### Error Handling
- [Error Boundaries](ErrorBoundaries.md) - Robust error handling components with recovery strategies

### Performance
- [Lazy Components](LazyComponents.md) - Lazy loading system for heavy components
- [Virtualized List](VirtualizedList.md) - High-performance list rendering for thousands of items

### UI Feedback
- [Toast System](Toast.md) - Comprehensive notification system with actions and styles
- [Validation Message](ValidationMessage.md) - Form validation feedback component

## Component Architecture

All components in Viny follow these principles:

1. **TypeScript First** - Full type safety with proper interfaces
2. **Performance Optimized** - Using React.memo, useMemo, and useCallback where appropriate
3. **Accessibility** - WCAG 2.1 AA compliant with proper ARIA attributes
4. **Dark Theme Support** - All components work seamlessly with Viny's dark theme
5. **Error Boundaries** - Protected by error boundaries for graceful failure

## Usage Example

```tsx
import { ToastContainer, useToast } from '@/components/ui/Toast'
import { VirtualizedList } from '@/components/ui/VirtualizedList'

function MyComponent() {
  const { showToast } = useToast()
  
  return (
    <>
      <VirtualizedList
        items={data}
        renderItem={(item) => <ItemComponent {...item} />}
        itemHeight={60}
      />
      <ToastContainer />
    </>
  )
}
```