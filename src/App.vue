<template>
    <div class="container-fluid bg-secondary text-dark w-full h-100">
        <div class="container">
            <nav class="navbar navbar-expand-lg ">
                <div class="container-fluid">
                    <a class="navbar-brand text-white pt-3" href="#">
                        <h1 class="text-dark">彥光日記本</h1>
                    </a>
                </div>
            </nav>
            <div class="row">
                <div class="container col-lg-4">
                    <Person />
                </div>
                <div class="container col-lg-8">
                    <Diary />
                </div>
            </div>
        </div>
        <hr>
        <div class="container">
            <h1>彥光記帳本</h1>
            <div class="row">
                <!-- 這邊弄成輸入消費金額、總類-->
                <div class="col-lg-3">
                    <div class="pt-3">
                        <select class="form-select" aria-label="Default select example">
                            <option selected>總類</option>
                            <option value="breakfast">早餐</option>
                            <option value="lunch">午餐</option>
                            <option value="dinner">晚餐</option>
                        </select>
                    </div>
                    <div class="form-floating pt-3 mb-3">
                        <input class="form-control" v-model="money" type="text" placeholder="金額" id="floatingInput" required>
                        <label for="floatingInput">金額</label>
                    </div>
                </div>
                <div class="col-lg-3">
                    <input v-model="money" type="text">
                </div>
                <!-- 這邊可能作成展示 -->
                <div class="col-lg-3 bg-primary">
                    <span>總類</span>
                </div>
            </div>
        </div>
    </div>

</template>

<script setup lang="ts">
import Person from './components/person.vue'
import Diary from './components/Diary.vue'
</script>

<style scoped></style>