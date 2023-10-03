<script setup>
import item from '../component/item.vue'
</script>

<template>
    <div class="row">
        <div class="col-xl-2 col-md-3 col-sm-6">
            <item></item>
        </div>
        <div class="col-xl-2 col-md-3 col-sm-6">
            <item></item>
        </div>
        <div class="col-xl-2 col-md-3 col-sm-6">
            <item></item>
        </div>
        <div class="col-xl-2 col-md-3 col-sm-6">
            <item></item>
        </div>
        <div class="col-xl-2 col-md-3 col-sm-6">
            <item></item>
        </div>
        <div class="col-xl-2 col-md-3 col-sm-6">
            <item></item>
        </div>
    </div>
    <div class="row">
        <div class="col ">
            <nav aria-label="Page navigation ">
                <ul class="pagination justify-content-center">
                    <li class="page-item">
                        <a class="page-link" href="#" aria-label="Previous">
                            <span aria-hidden="true">&laquo;</span>
                        </a>
                    </li>
                    <li class="page-item"><a class="page-link" href="#">1</a></li>
                    <li class="page-item"><a class="page-link" href="#">2</a></li>
                    <li class="page-item"><a class="page-link" href="#">3</a></li>
                <li class="page-item">
                    <a class="page-link" href="#" aria-label="Next">
                        <span aria-hidden="true">&raquo;</span>
                    </a>
                </li>
            </ul>
        </nav>
    </div>
</div></template>
<style></style>