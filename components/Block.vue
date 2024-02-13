<template>
  <div class="block" v-if="showblock" @click="stopTimer">click me</div>
</template>

<script>
export default {
    props: ['delay'],
    data(){
        return{
            showblock: false,
            timer: null,
            reactionTime : 0, //يحسب كم اخذك وقت لين ضغطت
        }
    },
    mounted(){ //اي شي جوا دي المنطقه مارح يشتغل الا لما يصير ماونتيد 
        setTimeout(() => {
            this.showblock = true
            this.startTimer()
        }, this.delay);
        console.log('mounted')
    },
    //     unmounted(){ //اي شي جوا دي المنطقه مارح يشتغل الا لما يصير ماونتيد 
    //     console.log('unmounted')
    // },
    // updated(){ //اي شي جوا دي المنطقه مارح يشتغل الا لما يصير ابديت للداتا

    // },

    methods:{
        startTimer(){
            this.timer = setInterval(() => { //Schedules repeated execution of callback every delay milliseconds.
                this.reactionTime += 10
            }, 10)
        },
        stopTimer(){
            clearInterval(this.timer) //Cancels a Timeout object created by setInterval().
            console.log(this.reactionTime)
                        this.$emit('end' , this.reactionTime) //is used within a Vue.js component to emit a custom event named 'end'
        //this.$emit() in Vue.js is like ringing a bell to let others know that something has happened. When you ring this bell, you can also pass along some information, like a message.

// * this.$emit() : In Vue.js, this refers to the current component you're working with. The $emit() part is like calling a function provided by Vue.js itself.
// * Ringing a Bell : Imagine there's a special bell in your component. When you call this.$emit('eventName'), you're ringing this bell and letting other parts of your application know that something has happened.
// * Passing a Message : Besides just ringing the bell, you can also attach a message to it. For example, this.$emit('eventName', someData) means you're ringing the bell and saying, "Hey, this event happened, and here's some extra information about it."
        },
    },
}
</script>

<style>
.block{
    width: 400px;
    border-radius: 20px;
    background: #0faf87;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
</style>