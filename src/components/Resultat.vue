<template>
  <p>Reaktions tid - {{ score }} ms</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
props: ['score'],
data() {
    return {
        rank: null
    }
},
mounted(){
    if (this.score < 231) {
        this.rank = 'Du är en Geparden amazing ❤️'
    }   else if (this.score < 315) {
        this.rank = 'Du är en Antilop ✌'
    }   else {
        this.rank = 'Du är en snigel.. 😝'
    }
}
}
</script>

<style>
.rank{
    font-size: 1.4em;
    color: #0faf87;
    font-weight: bold;
}
</style>