<template>
<div class="card">
    <h3>Giovanni & Rafael Patience Bar</h3>
    <div class="reput_bar">
        <div class="gio_bar_value"  :style="{width:patienceBar + '%', backgroundColor:dangerBar? 'red' : '#42B883' }"><h3 class="bar_text">{{patienceBar}}%</h3></div>
    </div>
    <section>
        <img
    v-if="patienceBar>=90"
      class="emoji"
      src="https://www.pngitem.com/pimgs/m/115-1151469_happy-reaction-emoji-icon-vector-graphic-emoticon-happy.png"
      alt="Happy emoji">
         <img
    v-if="patienceBar<=20"
      class="emoji"
      src="https://i.pinimg.com/originals/48/b2/0d/48b20d142bb790bc142f9b4337781db6.jpg"
      alt="Angry emoji">
    <img
      class="aestico_team"
      src="https://cdn.discordapp.com/attachments/821488234298081330/955874029653332068/Giovanni-picture.PNG"
      alt="Giovanni picture">
    <img
      class="aestico_team"
      src="https://cdn.discordapp.com/attachments/821488234298081330/955904230189838386/Rafael.PNG"
      alt="Rafael picture">
    <img
    v-if="patienceBar>=90"
      class="emoji"
      src="https://www.pngitem.com/pimgs/m/115-1151469_happy-reaction-emoji-icon-vector-graphic-emoticon-happy.png"
      alt="Happy emoji">
           <img
    v-if="patienceBar<=20"
      class="emoji"
      src="https://i.pinimg.com/originals/48/b2/0d/48b20d142bb790bc142f9b4337781db6.jpg"
      alt="Happy emoji">
    </section>
      <br>
      <button class="good_btn" @click="upReputation()">Answer</button>
      <button class="bad_btn" @click="downReputation()">Panic</button>
      </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent ({
    data(){
        return {
            patienceBar: 50,
            dangerBar : false,
        }
    },
    methods:{
        getRandomValue(min:number, max:number) {
        return Math.floor(Math.random() * (max - min)) + min;
        },

        upReputation(){
            const reputationValue = this.getRandomValue(5,12)
            if (this.patienceBar+reputationValue<100){
            this.patienceBar += reputationValue;
            }
            else
            this.patienceBar = 100
            
        },
        downReputation(){
            const reputationValue = this.getRandomValue(5,12)
            
            if (this.patienceBar-reputationValue>0){
            this.patienceBar -= reputationValue;
            }
            else
            this.patienceBar = 0
            
        }
    },
    watch: {
        patienceBar(value){
            if(value<=20){
                this.dangerBar = true
            }
            else if (value>60){
                this.dangerBar = false

            }
        }
    }

        
})
</script>

<style>


.card{
    height: 100%;
    border: 1px solid black;
    width: 450px;
    padding: 50px;
    margin: auto;
    margin-top: 10%;
    border-radius: 20px;
}

.reput_bar{
    background-color: rgba(245, 172, 164, 0.198);
    width: 55%;
    margin: auto;
}

.aestico_team{
    width: 90px;
    margin: 5px;
    border-radius: 50%;
}

.emoji{
    width: 20px;
    margin-bottom: 40px;
    border-radius: 50%;
}
.bar_text{
    color: #fff;
    display: flex;
    justify-content: center;
}
button{
    margin: 10px;
    border: 1px solid #fff;
    color: #fff;
    padding: 10px;
    padding-right: 20px;
    padding-left: 20px;
    border-radius: 20px;
    font-weight: 800;
}
.good_btn{
    background-color: rgb(85, 211, 85);
}
.bad_btn{
    background-color: rgb(255, 105, 67)
}

</style>