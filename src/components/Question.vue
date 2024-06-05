<script setup>
import { ref } from 'vue'
import crypto from 'crypto'
import gsap from 'gsap'

defineProps({
    question: {
        type: String,
        required: true
    },
    correctAnswerHash: {
        type: String,
        required: true
    }
})

const inputAnswer = ref('入力回答')
const status = ref(null)

const CORRECT = 'CORRECT'
const INCORRECT = 'INCORRECT'

// 回答チェック
const checkAnswer = (correctHash, value) => {
    // inputAnswerをハッシュ化してanswerと比較
    const inputAnswerHash = crypto.createHash('sha256').update(value).digest('hex');

    if(correctHash === inputAnswerHash) {
        status.value = CORRECT
    }else{
        status.value = INCORRECT
    }
}
</script>

<template>
  <div >
    <p>{{ question }}</p>
    <p>debug情報:{{ correctAnswerHash }}</p>
    <input v-model="inputAnswer" />
    <button @click="checkAnswer(correctAnswerHash, inputAnswer)">回答する</button>
    <p v-if="status===CORRECT">正解です！</p>
    <p v-else-if="status===INCORRECT">不正解です！</p>
    <p v-else>回答してください！</p>
</div>
</template>