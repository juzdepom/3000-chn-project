<template>
    <div style="text-align: center; justify-content: center">
        <h1>3000 Chinese Characters</h1>
        <h3>三千字</h3>
        <div class="form-group">
          <textarea
            style="font-size: 15pt"
            class="form-control"
            v-model="text"
            rows="8"
            cols="80"
            placeholder="Paste Chinese characters here..."></textarea>
        </div>

        <br>
        <p>I have a ranked deck of <strong>{{ length }}</strong> of the most common Chinese characters.</p>
        <p v-if="!isChineseCharacter">Error: Your input isn't Chinese.</p>
        <p v-else>You have input <strong>{{ charAmount }}</strong> Asian characters.</p>
        <div v-if="isChineseCharacter && charAmount > 0" style="width: 50%; text-align: center; margin: 0 auto">
          If I knew the <strong>first {{ mastered }}</strong> of my {{ length }} cards
          I would already know <strong>{{ matchingChar.length }}</strong> of these {{ charAmount }} characters
          which means I would be able to read <strong>{{ percentage }}</strong> of this text.
          <br><br>
          Number of Mastered Cards:
          <input style="width:50%; margin: 0 auto" class="form-control"type="number" v-model="mastered">
        </div>


        <!-- <button style="margin: 20px"class="btn btn-primary" @click="run">Run</button> -->

    </div>
</template>

<style>
  strong {
    font-size: 15pt;
  }
</style>



<script>


    export default {
        data(){
          return {
            text: "",
            length: onlyCharacters.length,
            mastered: 100,
          }
        },
        computed: {
          percentage(){
            var fraction = this.matchingChar.length
            var decimal = this.onlyChar.length
            var percentage = (fraction/decimal) * 100
            percentage = Math.round(percentage * 100) / 100
            return percentage+'%'
          },
          matchingChar(){
            var arr = []
            var x = this.onlyChar
            var m = this.masteredChar
            x.forEach(char => {
              if(m.includes(char)){
                arr.push(char)
              }
            });
            return arr
          },
          masteredChar(){
            var arr = onlyCharacters.slice(0,(this.mastered))
            return arr
          },
          isChineseCharacter(){
            return (this.text=="")?true:this.text.match(/[\u3400-\u9FBF]/)
          },
          charAmount(){
            return this.onlyChar.length
          },
          onlyChar(){
            var x = this.text
            x = x.replace(/[0-9]/g, '');
            x = x.replace(/[a-z]/gi, '')
            x = x.replace(/[.,\/#!$%\^&\*;:{}=\-_`~()。，（\n）、·]/g,"")
            x = x.split('')
            return x;
          },
        },
        methods: {
          run(){
          }
        }
    }
</script>
