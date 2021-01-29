<template>
  <v-app id=input-form>
    <v-main>
      
      <v-form
        ref="form"
        v-model="valid"
      >
      <div v-if="this.wrong == true ">
        You're a moron
      </div>
      {{ question }}
        <v-text-field
          v-model="word"
          label="Today's Word"
          required
          ></v-text-field>
        <v-btn
          :disabled="!valid"
          color="cyan"
          class="mr-4"
          @click="validate()"
          >
          Submit
          </v-btn>
        </v-form>
      </v-main>
    </v-app>
  </template>
<script>
  export default {
    name: 'input-form',
    props: {
      answer: String,
      question: String,
    },
    data: () => ({
      valid: true,
      name: '',
      word: '',
      wrong: false,
      Rules:[
        v => v == "Chocolate",
      ]
    }),
    methods: {
      validate(){
        if(this.word == this.answer){
          this.$emit('correct-pw', 1)
        } else {
          this.wrong = true
        }
      }
    }
  }
</script>
