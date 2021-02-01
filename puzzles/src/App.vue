<template>
  <v-app>
    <v-container>
      <v-banner
      elevation="10"
      dark
      outlined
      rounded
      color= "cyan lighten-1"
      min-height=50
      >
      <h1 class= "text-button"  align="center">YOU HAVE TO THINK</h1>
      </v-banner>
      
  </v-container>
    <br>
    <v-main>
      <v-container v-if="!finish">
        <input-form 
          @correct-pw="startGame"
          :answer="ans[stage]"
          :question="questions[stage]"
          :hint="hints[stage]"
        />
        <v-container v-if="stage > 0">
          <timer
            @time-up="timeUp"
            />
         </v-container>
        
        </v-container>

        <v-container v-else>
        <h1 class="overline-xl" align="center">
          You Got Through {{stage}} Questions!
          </h1>
          </v-container>
      
    </v-main>
    
  </v-app>
</template>

<script>
import InputForm from '@/components/InputForm.vue'
import Timer from '@/components/Timer.vue'
export default {
  name: 'app',
  data: () => ({
    stage: 0,
    ans: ["Chocolate", "13","Djibouti","Appa","43.4, 110.7", "2009", "Comoros", "Papagei", "1911196", "Valiant Lady"],
    questions: ["Password", "What is the Square Root of 169","Capital of Djibouti", "Avatar Aangs Sky Bison",  "What are the Coordinates of Jackson, Wyoming ", "What Year Did Rihanna Release 'Rude Boy'?", "Small Island Nation inbetween Madagascar and Mozambique beggining with the Letter 'C'", "ببغاء في اللغة الألمانية", "Distance from Earth to the Moon in Furlongs", "American Soap Opera premiering October 12th, 1953",  ],
    hints:["Today's Password","Whole Number", "Name of City", "One Word", "Format: 00.0, 00.0", "2XXX", "One Word", "Hint: Translate", "Round to Whole Number", "Two Words"],
    finish: false,
  }),
  components: {
    InputForm,
    Timer,
  },
  methods: {
    startGame(){
      this.stage = this.stage + 1
    },
    timeUp(){
      this.finish=!this.finish
    }
  },
}
</script>
<style>
