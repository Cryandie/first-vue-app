<template>
<div class="card">
    <section class="screen">
    <h3 class="color-animation">Giovanni & Rafael Patience Bar</h3>
    <div class="reput_bar">
        <div class="gio_bar_value"  :style="{width:patienceBar + '%', backgroundColor:dangerBar? 'red' : '#42B883' }"><h3 class="bar_text">{{patienceBar}}%</h3>
         <h2 v-if="patienceBar==0" class="gameover">Interview Over</h2>
         <h2 v-else-if="patienceBar==100" class="welcome">Welcome To Aestico!🎈🎈🎈</h2>
        </div>
    </div>
    <section class="images_container">
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
    </section>
      <br>
      <hr>
      <section class="buttons_container">
      <button class="good_btn" @click="upReputation()">Answer</button>
      <button class="bad_btn" @click="downReputation()">Panic</button>
      </section>
      <section class="buttons_image_container">
          <img class="buttons_image" src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRLRO31jt_EqUj5GSM8EXkyGGcOa8Tx14c2bg&usqp=CAU" alt="gaming buttons logo">
      </section>
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
            else if (value>20){
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
    background-color: rgb(59, 59, 59);
}

.reput_bar{
    background-color: rgba(241, 203, 97, 0.692);
    height: 120px;
    width: 55%;
    margin: auto;
    display:flex;
    justify-content: center;
    align-content: center;
    border-radius: 10px;
}

.gio_bar_value{
  background-color: #42B883;
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
    width: 100%;
    display: flex;
    justify-content: center;
}
.gameover{
    width: 100%;
    color: red;
    display: flex;
    justify-content: center;
}
.welcome{
    color: rgb(195, 34, 235);
}

.screen{
    border: 5px solid black;
    background-color: rgb(255, 176, 5);
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
    cursor: pointer
}
.buttons_container{
    padding-top: 20px;
}
.good_btn{
    background-color: rgb(85, 211, 85);
}
.bad_btn{
    background-color: rgb(255, 105, 67)
}

.buttons_image_container{
    display: flex;
    justify-content: flex-end;
    width: 100%;
}
.buttons_image{
    width: 90px;
    border-radius: 50%;
}




/* Color Animation */
.color-animation {
  -webkit-animation: color-change-4x 6s linear infinite alternate both;
  animation: color-change-4x 6s linear infinite alternate both;
}

@-webkit-keyframes color-change-4x {
  0% {
    color: #19dcea;
  }
  33.3333% {
    color: #b22cff;
  }
  66.666% {
    color: #ea2222;
  }
  100% {
    color: #f5be10;
  }
}
@keyframes color-change-4x {
  0% {
    color: #19dcea;
  }
  33.3333% {
    color: #b22cff;
  }
  66.666% {
    color: #ea2222;
  }
  100% {
    color: #f5be10;
  }
}

</style>