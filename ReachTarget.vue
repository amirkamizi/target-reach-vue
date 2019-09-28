<template>
    <div class="card">
        <div class="card-header">
            Reach The Target
        </div>
        <div class="card-body">
            <button class="btn btn-info mb-1" @click="setTarget">Set the Target</button>
            <br>
            <small v-if="target">Your Target is {{ target }}</small>
            <br>
            <button class="btn btn-small btn-warning" @click="decreaseOne" :disabled=finished>-2</button>
            <input type="text" :value="value" readonly>
            <button class="btn btn-small btn-warning" @click="increaseThree" :disabled=finished>+3</button>
            <br>
            <small class="mx-5 my-3" v-if="target&&value!=0">{{ message }}</small>
        </div>
    </div>
</template>

<script>
    export default {
        data: function(){
            return {
                value : 0,
                target: 0,
                finished:true,
            }
        },
        computed:{
            message : function(){
                if(this.value < 0){
                    return "You are going in the wrong direction!";
                }else if(this.value > 130){
                    return "What are you doing?? go back!";
                }else if(this.value < this.target){
                    return "Not there yet";
                }else if(this.value > this.target){
                    return "You've passed the target!";
                }else{
                    this.finished = true;
                    return "WOW... you did it!";
                }
            }
        },
        methods:{
            setTarget : function(){
                this.target = Math.floor((Math.random() * 100) + 1);
                this.finished = false;
                this.value = 0;
            },
            increaseThree : function(){
                this.value = this.value + 3;
            },
            decreaseOne : function(){
                this.value = this.value - 2;
            }
        }
    }
</script>
