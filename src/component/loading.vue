<template>
    <div class="row">
        <div class="alert alert-danger" role="alert">
            <h4 class="alert-heading">未添加数据源!</h4>
            <p>请参照<a href="#">链接</a>添加数据源。</p>
            <hr>
            <p class="mb-0">看到此信息说明没有添加数据裤。</p>
        </div>
    </div>
</template>
<script setup>
import { defineProps, onMounted } from 'vue'
const props = defineProps(["data"])
onMounted(() => {
})
</script>

<style></style>