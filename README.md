### fuse-box
---
https://github.com/fuse-box/fuse-box

```ts
// src/core/__tests__/WeakModuleReferences.test.ts
import { createContext } from '../Context';
import { createWeakModuleReferences, WakModuleReferences } from '../WeakModuleReferences';

describe('WeakModuleReferences', () => {
  function create(): WeakModuleReferences {
    const ctx = createContext({});
    return createWeakModuleReferences(ctx);
  }
  it('should be 0 at start', () => {
    const ref = create();
    expect(Object.keys(ref.collection)).toHaveLength(0);
  });
  
  it('should add one ref', () => {
    const ref = create();
    ref.add('/foo', '/bar');
    expect(Object.keys(ref.collection)).toHaveLength(1);
  });
  
  it('should not add same ref', () => {
    const ref = create();
    ref.add('/foo', '/bar');
    ref.add('/foo', '/bar');
    expect(Object.keys(ref.collection)).toHaveLength(1);
  });
  
  it('should flush', () => {
    const ref = create();
    ref.add('/foo', '/bar');
    ref.add('/foo', '/bar');
    ref.flush();
    expect(Object.keys(ref.collection)).toHaveLength(0);
  });
  
  it('should find', () => {
    const ref = create();
    ref.add('/foo', '/bar');
    const res = ref.find('/foo');
    expect(res).toEqual(['/bar']);
  });
})



```

```
```

```
```


