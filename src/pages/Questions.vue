<template>
    <Layout>
        <h1>Sample Questions</h1>
        <p>Here are some sample questions.</p>
        <Question 
            question="ぴかちゅうのいろは？" 
            correctAnswerHash="09d5775dfdea64e5c946788b1833e0091f85a84fbd8f67fc3c3557b6c2969437"
        />
    </Layout>
</template>

<script>
import Question from '../../src/components/Question.vue'

export default {
  components: {
    Question
  }
}
</script>
