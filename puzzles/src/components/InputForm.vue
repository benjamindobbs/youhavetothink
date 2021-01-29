<template>
  <!-- <v-app id=input-form>
    <v-main> -->
      
      <v-form
        ref="form"
        v-model="valid" 
      >
      <div>
        <v-layout justify-center>
        <h1 class="overline-xl">{{question}}  </h1>
        </v-layout>
        <br>
       
      <v-container>
        <v-text-field
          v-model="word"
          :hint= this.hint
          background-color= "#9575"
          persistent-hint
          reverse
          >
          </v-text-field>
        <v-layout justify-center>
        <v-btn
          elevation=5
          color="cyan lighten-1"
          large
          class="mr-4"
          @click="validate()"
          >
          Submit
          </v-btn>
          </v-layout>
          <br>
      <div>
            <v-snackbar
            v-model="right"
            app
            color="green accent-2"
            elevation= 5
            rounded
            
            :timemout="timeout"
            >
            <h1 class="overline-xl" align="center"> Correct! </h1>
            </v-snackbar>
          </div>
            <div>
              <v-snackbar
              v-model="wrong"
            app
            color="orange darken-4"
            elevation= 5
            rounded
            
            :timemout="timeout"
            >
            <h1 class="overline-xl" align="center"> Incorrect! </h1>
            </v-snackbar>
            </div>
          </v-container>
           </div>
          
<br>
        </v-form>
      <!-- </v-main>
    </v-app> -->
</template>
<script>
  export default {
    name: 'input-form',
    props: {
      answer: String,
      question: String,
      hint: String,
    },
    data: () => ({
      valid: false,
      name: '',
      word: '',
      wrong: '',
      right: '',
      timeout: 2000,
      
    }),
    methods: {
      validate(){
        if(this.word == this.answer){
          this.$emit('correct-pw', 1)
          this.right = true
          this.word = ''
        } else {
          this.wrong = true
          this.word= null
        }
      }
    },
    computed: {
      Rules: function() {
        return [v => v == this.answer]
      }
    }
  }

</script>
