<template>
    <div>
        <div class="container text-center">
            <img src="../assets/head.jpg" class="rounded-circle " alt="">
            <h1 class="text-dark pt-3">{{name}}</h1>   

        </div>
    </div>
</template>

<script setup lang="ts">
    import {ref} from 'vue'

    let name = ref('賴彥光')
</script>

<style scoped>

</style>