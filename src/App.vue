<script setup>
import { ref, onMounted } from 'vue';
// import { create } from 'ipfs-core';
// import { createOrbitDB } from '@orbitdb/core';

const pElementRef = ref(null)

onMounted(async () => {
  // const ipfs = await create();
  // const orbitdb = await createOrbitDB({ ipfs });
  // const db = await orbitdb.open('my-db')
  // pElementRef.value.textContent = db.address;
  // await db.close();
  // await ipfs.stop();
})
import cheader from './component/header.vue'
import loading from './component/loading.vue'
import genre from './component/genre.vue'
import lists from './component/lists.vue'
import player from './component/player.vue'
import comment from './component/comment.vue'
import donate from './component/donate.vue'
import cfooter from './component/footer.vue'
</script>

<template>
  <cheader></cheader>
  <div class="container">
    <loading></loading>
    <genre></genre>
    <lists></lists>
    <player></player>
    
    <div class="row justify-content-between">
      <div class="col-4"><donate></donate></div>
      <div class="col-6"><comment></comment></div>
    </div>
    <donate></donate>
  </div>
  <cfooter></cfooter>
</template>
