# Workers Documentation

This section contains documentation for Viny's Web Workers implementation.

## Available Workers

### Search Worker
- [Search Worker](search-worker.md) - Optimized search with Fuse.js in a separate thread

## Web Workers Architecture

Viny uses Web Workers to offload computationally intensive tasks from the main thread, ensuring a smooth UI experience.

### Benefits
1. **Non-blocking UI** - Heavy computations don't freeze the interface
2. **Better Performance** - Utilize multiple CPU cores
3. **Improved Responsiveness** - Main thread stays free for user interactions

### Implementation Pattern

```typescript
// Worker file (search.worker.ts)
self.addEventListener('message', (event) => {
  const { type, payload } = event.data
  
  switch (type) {
    case 'SEARCH':
      const results = performSearch(payload)
      self.postMessage({ type: 'SEARCH_RESULTS', payload: results })
      break
  }
})

// Using the worker (useSearchWorker.ts)
const worker = new Worker('/workers/search.worker.js')
worker.postMessage({ type: 'SEARCH', payload: { query: 'test' } })
worker.onmessage = (event) => {
  const { type, payload } = event.data
  // Handle results
}
```

## Best Practices

1. **Error Handling** - Always implement error boundaries for worker failures
2. **Fallback Strategy** - Provide main thread fallback when workers aren't supported
3. **Message Protocol** - Use consistent message structure with types
4. **Resource Cleanup** - Terminate workers when no longer needed
5. **Performance Monitoring** - Track worker performance and overhead

## Browser Support

Web Workers are supported in all modern browsers:
- Chrome 4+
- Firefox 3.5+
- Safari 4+
- Edge (all versions)
- Mobile browsers (iOS Safari 5+, Chrome Android)

For older browsers, Viny automatically falls back to main thread execution.