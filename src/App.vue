<template>
  <div id="app">

    <!-- <button @click="musicOn()">sound</button> -->

    <img src="./assets/img/1.png">
    <img src="./assets/img/2.png">
    <img src="./assets/img/3.png">
    <img src="./assets/img/4.png">
    <img src="./assets/img/5.png">

    <div id="gop-wrapper">
        <div id="gop">

        </div>
        <div id="gop-speech">

        </div>

    </div>

    <div id="wrapper">

      <div id="el1-1" style="left:20px;" :style="`top:${bottom}px; transition: top ease ${trans1}s, background-image 0s; background-image: url(./img/${number1}.${arr[number1]}.png)`"> </div>
      
      <div id="el1-2" style="left:20px" :style="`top:${bottom2}px; opacity: ${opacity}; background-image: url(./img/${number1}.${arr[number1]}.png)`"> </div>
      
      <div id="el1-3" style="left:20px" :style="`top:${bottom3}px; opacity: ${opacity}; background-image: url(./img/${number1}.${arr[number1]}.png)`"> </div>
      
      
      <div id="el2-1" style="left:240px" :style="`top:${bottom}px; transition: top ease ${trans2}s, background-image 0s; background-image: url(./img/${number2}.${arr[number2]}.png)`"> </div>
      
      <div id="el2-2" style="left:240px" :style="`top:${bottom2}px; opacity: ${opacity}; background-image: url(./img/${number2}.${arr[number2]}.png)`"> </div>
      
      <div id="el2-3" style="left:240px" :style="`top:${bottom3}px; opacity: ${opacity}; background-image: url(./img/${number2}.${arr[number2]}.png)`"> </div>


      <div id="el3-1" style="left:460px" :style="`top:${bottom}px; transition: top ease ${trans3}s, background-image 0s; background-image: url(./img/${number3}.${arr[number3]}.png)`"> </div>

      <div id="el3-2" style="left:460px" :style="`top:${bottom2}px; opacity: ${opacity}; background-image: url(./img/${number3}.${arr[number3]}.png)`"> </div>

      <div id="el3-3" style="left:460px" :style="`top:${bottom3}px; opacity: ${opacity}; background-image: url(./img/${number3}.${arr[number3]}.png)`"> </div>

      <div id="upWrapper">

      </div>
      <div id="downWrapper">

      </div>
    </div>
  </div>
</template>

<script>
// import {useSound} from '@vueuse/sound'
// import soundSprite from './assets/audio/sound-sprite.mp3'

export default {
  //   setup() {
  //   const {play, stop} = useSound(soundSprite, {
  //     sprite: {
  //       start: [2750, 1250],
  //       spin: [5050, 1150],
  //       end: [6300, 400],
  //       guitar: [7300, 131900],
  //     },
  //   })

  //   return {
  //     play,
  //     stop,
  //   }
  // },
  data() {
    return {
      bottom: 20,
      bottom2: -200,
      bottom3: -420,
      opacity: 0,
      inter1: 0,
      inter2: 0,
      number1:2,
      number2:3,
      number3:4,
      trans1:0,
      trans2:0,
      trans3:0,
      spin: false,
      // music: false,
      arr: ['zero', 'adcb3c81', 'c8ccef56', '1c9b6cf1', '9b45790e', '03cd1c9c']
    }
  },
  mounted() {
    document.addEventListener('keydown', this.startSpin);
    document.addEventListener('keyup', this.stopSpin);
  },

  methods: {

    // musicOn() {

    //   if (!this.music) {
    //     this.music = true;
    //     this.play({id:'guitar'});
    //     setInterval(()=>{
    //       this.play({id:'guitar'});
    //     }, 131900)
    //   } else {
    //     this.stop();
    //     this.music = false;
    //   }
    // },

    startSpin(event) {

      if (event.keyCode == 13 && !this.spin) {
        this.spin = true;
        this.trans1 = 0;
        this.trans2 = 0;
        this.trans3 = 0;
        this.opacity = 1;
        // this.play({id:'start'});
        this.moveUp();
      }

    },

    stopSpin(event) {
      if (event.keyCode == 13 && this.spin) {
        // this.play({id:'end'});
        this.spin = false;
        this.bottom = -400;
        this.trans1 = 0.5;
        this.trans2 = 1;
        this.trans3 = 1.5;
        this.stopMove();
        // setTimeout(()=>{this.stop},400)

      }
    },

    stopMove() {
      this.bottom = 20;
      this.bottom2 = -200;
      this.bottom3 = -420;
      this.opacity = 0;
      this.number2 = 3;
    },

    moveUp() {
      let _this = this;

      // setInterval(()=>{
      //   if (!_this.spin) {
      //     _this.stop();
      //   } else {
      //     _this.play({id:'spin'});
      //   }
      // },1150)

      setInterval(() => {
        if (!_this.spin) {
          return;
        }

        if (this.bottom <= 240) {
          this.bottom+=10;
          this.number1++;
          this.number2++;
          this.number3-=1;

            if (this.number3 < 1) {
              this.number3=5
            } 
            if (this.number2 > 5) {
              this.number2=1;
            } 
            if (this.number1 > 5) {
              this.number1=1;
            }
            if (this.bottom >240) {
              this.bottom=(-420)
            }
        }
        if (this.bottom2 <= 240) {
          this.bottom2+=10;
          
            if (this.bottom2 >240) {
              this.bottom2=(-420)
            }
        }
        if (this.bottom3 <= 240) {
          this.bottom3+=10;
          
            if (this.bottom3 >240) {
              this.bottom3=(-420)
            }
        }
      }, 10);
    },
  },
}
</script>

<style>
  body {
    margin: 0;
    padding: 0;
    background-color: rgb(97, 4, 4);
    background-image: url(./assets/img/logo.png);
    background-size: 10%;
    background-repeat: space;
    overflow: hidden;
  }
  #app {
    width: 100vw;
    height: 100vh;
    margin: 0;
    background-image: url(./assets/img/main-bg.png);
    background-position: center;
    background-repeat: no-repeat;
  }
  #gop-wrapper {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: aqua;
    /* background-image: url(./assets/img/gop.png); */
    /* background-position: center; */
    /* background-repeat: no-repeat; */
    /* background-size: 80%; */
    z-index: 8768;
  }
  #gop {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-800px, 37px);
    width: 500px;
    height: 550px;
    background-image: url(./assets/img/gop.png);
    background-position: center;
    background-repeat: no-repeat;
    background-size: 100%;


  }
  #wrapper {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 680px;  
    height: 240px;
    /* background-color: burlywood; */
  }
  #upWrapper {
    position: absolute;
    top: -412px;
    width: 680px;  
    height: 412px;
    z-index: 500;
    /* background-color: burlywood; */
    background-image: url(./assets/img/up-wrapper.png);
    /* border-bottom: 3px solid black; */
    /* display: none; */

  }
  #downWrapper{
    position: absolute;
    bottom: -408px;
    right: 1px;
    width: 680px;  
    height: 412px;
    /* background-color: burlywood; */
    background-image: url(./assets/img/down-wrapper.png);
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
    /* border-top: 3px solid black; */
    /* display: none; */

  }
  #el1-1, #el1-2, #el1-3, #el2-1, #el2-2, #el2-3, #el3-1, #el3-2, #el3-3 {
    position: absolute;
    width: 200px;
    height: 200px;
    /* background-color: burlywood; */
    /* background-image: url(./assets/img/1.png); */
    /* border: 2px solid black; */
    box-sizing: border-box;
    background-position: center;
    background-repeat: no-repeat;
    background-size: 100%;
  }
  img {
    display: none;
  }
</style>