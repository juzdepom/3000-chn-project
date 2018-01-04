<template>
    <div style="text-align: center;">
        <h1>3000 Chinese Characters</h1>
        <h3>三千字</h3>

        <textarea v-model="text" rows="8" cols="80"></textarea>

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

        }
    }
</script>
