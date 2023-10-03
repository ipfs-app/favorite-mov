<template>
  <nav class="navbar navbar-expand-lg bg-body-tertiary bg-dark" data-bs-theme="dark">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">F-MOV</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <a class="nav-link disabled" href="#">数据库：</a>
          </li>
          <li class="nav-item" v-for="db in nav_db">
            <a class="nav-link" href="#" @click="$emit('chang_db', db.address)">{{ db.title }}</a>
          </li>
        </ul>
        <form class="d-flex">
          <button type="button" class="btn btn-outline-secondary" data-bs-toggle="modal"
            data-bs-target="#configModal">Config</button>
        </form>
      </div>
    </div>
  </nav>
  <div class="modal fade" id="configModal" tabindex="-1" aria-labelledby="configModalLabel" aria-hidden="true">
    <div class="modal-dialog modal-lg">
      <div class="modal-content">
        <div class="modal-header">
          <h1 class="modal-title fs-5" id="configModalLabel">站点配置</h1>
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <div class="modal-body">
          <div class="input-group mb-3">
            <span class="input-group-text" id="username">username</span>
            <input type="text" class="form-control" aria-label="Username" aria-describedby="username" v-model="username">
          </div>
          <div class="mb-3">
            <label for="dbs" class="form-label">数据库:</label>
            <textarea class="form-control" id="dbs" rows="8" v-model="dbs"></textarea>
          </div>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-primary" @click="save_config" data-bs-dismiss="modal">保存</button>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
import { ref, onMounted } from 'vue'

const username = ref("anonymous")
const dbs = ref("[]")
const nav_db = ref([])
defineEmits(['chang_db'])
onMounted(() => {
  const configModal = document.getElementById('configModal')
  nav_db.value = JSON.parse(localStorage.getItem("fdbs"))
  configModal.addEventListener('shown.bs.modal', () => {
    username.value = localStorage.getItem("username")
    dbs.value = JSON.stringify(JSON.parse(localStorage.getItem("fdbs")), null, 2)
  })
})
function save_config() {
  localStorage.setItem("username", username.value)
  localStorage.setItem("fdbs", JSON.stringify(JSON.parse(dbs.value)))
}
</script>
<style></style>