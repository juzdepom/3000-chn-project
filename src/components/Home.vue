<template>
    <div style="text-align: center;">
        <h1>3000 Chinese Characters</h1>
        <h3>三千字</h3>
        <div class="form-group">
          <textarea class="form-control" v-model="text" rows="8" cols="80" placeholder="Paste Chinese characters here..."></textarea>
        </div>


        <p>I have a library of x cards</p>
        <button class="btn btn-primary" @click="run">Run</button>

    </div>
</template>



<script>


    export default {
        data(){
          return {
            text: ""
          }
        },
        computed: {

        },
        methods: {
          run(){
            var x = 0
            var array = []
            for(var i=0;i<ONE_THOUSAND.length;i++){
              x++
              console.log(x)
              console.log(ONE_THOUSAND[i].character)
              array.push(ONE_THOUSAND[i].character)
            }
            for(var i=0;i<TWO_THOUSAND.length;i++){
              x++
              console.log(x)
              console.log(TWO_THOUSAND[i].character)
              array.push(TWO_THOUSAND[i].character)
            }
            for(var i=0;i<THREE_THOUSAND.length;i++){
              x++
              console.log(x)
              console.log(THREE_THOUSAND[i].character)
              array.push(THREE_THOUSAND[i].character)
            }

            var str = JSON.stringify(array);
            console.log(str)
            console.log(array.length)

          }
        }
    }
</script>
