# swrv-ssr-bug

## Problem

Having multiple instances of `useSWRV` does not rehydrate correctly.

```bash
export default {
  setup() {
    const { data: data1 } = useSWRV('post1', () => fetchPostById(1));
    const { data: data2 } = useSWRV('post2', () => fetchPostById(2));
    return { data1, data2 }
  }
}
```

