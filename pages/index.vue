<template>
  <div class="container">
    <div v-if="data1">
      {{ data1 }}
    </div>
    <div v-if="data2">
      {{ data2 }}
    </div>
  </div>
</template>

<script>
import useSWRV from 'swrv';

export default {
  setup() {
    const { data: data1 } = useSWRV('post1', () => fetchPostById(1));
    const { data: data2 } = useSWRV('post2', () => fetchPostById(2));
    return { data1, data2 }
  }
}

async function fetchPostById(id) {
  await wait(1000);
  return `Post ${id}`;
}

function wait(ms) {
  return new Promise((resolve) => {
    setTimeout(resolve, ms)
  })
}
</script>
