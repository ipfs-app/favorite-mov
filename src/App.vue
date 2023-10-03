<template>
  <cheader @chang_db="chang_db"></cheader>
  <div class="container">
    <component :is="content" :data="content_data"></component>
    <!-- <genre></genre>
    <lists></lists>
    <player></player>
    
    <div class="row justify-content-between">
      <div class="col-4"><donate></donate></div>
      <div class="col-6"><comment></comment></div>
    </div>
    <donate></donate> -->
  </div>
  <cfooter></cfooter>
</template>
<script setup>
import { ref, shallowRef, onMounted, markRaw } from 'vue';
// import { create } from 'ipfs-core';
// import { createOrbitDB, Documents } from '@orbitdb/core';

const pElementRef = ref(null)

import cheader from './component/header.vue'
import loading from './component/loading.vue'
import genre from './component/genre.vue'
// import lists from './component/lists.vue'
// import player from './component/player.vue'
// import comment from './component/comment.vue'
// import donate from './component/donate.vue'
import cfooter from './component/footer.vue'
import axios from 'axios'
const content = shallowRef(loading)
const content_list = ref({
  "loading": markRaw(loading),
  "genre": markRaw(genre),
})
let content_data = ref({})
onMounted(async () => {
  // const ipfs = await create();
  // const orbitdb = await createOrbitDB({ ipfs });
  // const db = await orbitdb.open('vod', { Database: Documents({ indexBy: 'name'} ) })
  // const hash = await db.put({"name":"123","a":"b"})
  // console.log(hash)
  // console.log(db.address)
  // await db.close();
  // await ipfs.stop();
  axios.get("/config.json").then((res) => {
    if (!localStorage.getItem("username")) {
      localStorage.setItem("username", res.data.username)
    }
    if (localStorage.getItem("fdbs")) {
      let dbs = JSON.parse(localStorage.getItem("fdbs"))
      for (let i = 0; i < res.data.fdbs.length; i++) {
        let f = true
        for (let j = 0; j < dbs.length; j++) {
          if (dbs[j].title === res.data.fdbs[i].title) {
            f = false
            break
          }
        }
        if (f) {
          dbs.push(res.data.fdbs[i])
        }
      }
      localStorage.setItem("fdbs", JSON.stringify(dbs))
    } else {
      localStorage.setItem("fdbs", JSON.stringify(res.data.fdbs))
    }
  });
})
async function chang_db(address) {
  content_data.value = { address: address };
  content.value = content_list.value["genre"]
}
</script>
