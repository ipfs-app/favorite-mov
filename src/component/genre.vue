<template>
    <div class="row">
        <h2>分类:</h2>
    </div>
    <div class="row">
        <div class="col-xl-2 col-md-3 col-sm-6" v-for="genre in genres">
            <button type="button" class="btn btn-link">{{ genre.name }}</button>
        </div>
    </div>
</template>
<script setup>
import { defineProps, onMounted, ref } from 'vue'
import { create } from 'ipfs-core';
import { createOrbitDB, Documents } from '@orbitdb/core';

const props = defineProps(["data"])
const genres = ref([])
onMounted(async () => {
    const ipfs = await create();
    const orbitdb = await createOrbitDB({ ipfs });
    const db = await orbitdb.open(props.data.address, { Database: Documents({ indexBy: 'name' }) })

    for await (const record of db.iterator()) {
        genres.value.push({ "name": record.key }) // record.vaule.name 
    }

    await db.close();
    await ipfs.stop();
})
</script>
<style></style>