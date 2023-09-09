<template lang="">
    <div>
        <div class="block-result">
            <p>Reaction time: {{ score }}ms</p>
            <p class='rank'>{{rank}}</p>
        </div>
    </div>
</template>
<script>
export default {
    props:['score'],
    data() {
        return {
            rank:null
        }
    },
    mounted() {
        if(this.score < 300){
            this.rank = 'fasti faster'
        } else if (this.score < 400){
            this.rank = 'mid'
        } else {
            this.rank = 'slow az...'
        }
    },
}
</script>
<style>
    .block-result{
        width: 400px;
        height: 60px;
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
        font-size: 1.5rem;
        border-radius:20px ;
        background: white;
        color:  #0faf87;
        border: 2px solid #0faf87;
        padding: 100px 0;
        margin: 40px auto;
    }

    .block-result p{
        margin: 10px 0;
    }
</style>