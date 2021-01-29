<template>
  <v-app>
  <input-form 
    @correct-pw="startGame"
    :answer="msg[stage]"
    :question="questions[stage]"
  />
    <v-main>
    <div v-if="stage === 0">
      <home-page />
    </div>

    <div v-else-if="stage === 1">

    </div>
    </v-main>
    <div>
      {{ stage }}
      {{ msg }}
    </div>
  </v-app>
</template>

<script>
import HomePage from '@/components/HomePage.vue'
import InputForm from '@/components/InputForm.vue'
export default {
  name: 'app',
  data: () => ({
    stage: 0,
    msg: ["Chocolate", "Toast",],
    questions: ["q1", "q2"],
  }),
  components: {
    InputForm,
    HomePage,
  },
  methods: {
    startGame(){
      this.stage = this.stage + 1
      this.msg = "Toast"
    }
  },
}
</script>
<style>
