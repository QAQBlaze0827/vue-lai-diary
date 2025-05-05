<template>
    <div class="mb-3">
        <label for="diaryInput" class="form-label">寫下今天的日記：</label>
        <textarea 
          class="form-control" 
          id="diaryInput" 
          rows="3"
          v-model="diaryContent"
          @keydown.enter.ctrl.prevent="saveDiary"
        ></textarea>
    </div>
    <h4>我的日記紀錄</h4>
    <ul class="list-group" id="diaryList">
        <li class="list-group-item mb-2" v-for="(diary, index) in diaries" :key="index">
            {{ diary }}
            <button class="btn btn-danger btn-sm float-end" @click="deleteDiary(index)">刪除</button>
            <button class="btn btn-primary btn-sm float-end me-2" @click="editDiary(index)">編輯</button>
        </li>
    </ul>
</template>

<script setup lang="ts">
    import { ref, onMounted, watch } from 'vue'
    
    const diaryContent = ref('')
    const diaries = ref<string[]>([])
    
    const saveDiary = () => {
        if (diaryContent.value.trim() === '') {
            alert('請輸入日記內容')
            return
        }
        diaries.value.push(diaryContent.value)
        diaryContent.value = ''
    }
    
    const deleteDiary = (index: number) => {
        diaries.value.splice(index, 1)
    }
    const editDiary = (index: number) => {
        diaryContent.value = diaries.value[index]
        deleteDiary(index)
    }
    // 從 localStorage 載入資料
    onMounted(() => {
        const savedDiaries = localStorage.getItem('diaries')
        if (savedDiaries) {
            diaries.value = JSON.parse(savedDiaries)
        }
    })
    
    // 監聽日記變動，儲存到 localStorage
    watch(diaries, (newDiaries) => {
        localStorage.setItem('diaries', JSON.stringify(newDiaries))
    }, { deep: true })
</script>

<style scoped></style>
