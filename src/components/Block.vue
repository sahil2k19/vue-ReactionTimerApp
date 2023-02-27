<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    click me
  </div>
</template>

<script>
export default {
    props:['delay', ],
    data(){
        return{
            showBlock:false, // initially not shown
            timer:null, // timer interval
            reactionTimer:0, // we keep increasing the reaction timer
        }

    },
    mounted(){
        console.log('components mounted');
        setTimeout(()=>{
            this.showBlock=true;
            this.startTimer();
            console.log(this.delay);    
        }, this.delay);
    },
   
    methods:{
        startTimer(){
            this.timer = setInterval(()=>{
                this.reactionTimer += 10;
            },10);
        },
        stopTimer(){
             clearInterval(this.timer);
             this.$emit('end',this.reactionTimer);
             console.log(this.reactionTimer)
        },
    }
}
</script>

<style>
    .block{
        width: 400px ;
        border-radius: 20px;
        background: #0faf87;
        color: white;
        text-align: center;
        padding : 100px 0;
        margin : 40px auto;
    }
</style>