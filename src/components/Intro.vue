<script setup>
  import { introText } from '../constants';
</script>

<template>
    <section id="intro" class="intro">
        <div class="inner">
            <h2 class="hidTxt">{{ introText.title }}</h2>
            <canvas ref="canvas" id="canvas"></canvas>
            <div class="vsTxt">
                <div class="tit">{{ introText.desc[0] }}</div>
                <div class="exTxt">{{ introText.desc[1] }}</div>
            </div>
        </div>
    </section>
</template>
  


<style lang="scss" scoped>


/* intro css */

.intro {
    .inner {
      position: relative;
      width: 100%;
      height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      background: #000;
      &::before{
        position:absolute;left:0;top:0;content: '';display:block;width:100%;height:100%;background: #000 url(@/assets/img/bg_main.jpg) no-repeat center center;background-size: cover;
        opacity: 0.5;
      }
    }
  
    canvas {
      width: 100%;
      opacity: 0.8;
    }
  
    .vsTxt {
      position: absolute;
      left: 50%;
      top: 50%;
      transform: translate(-50%, -50%);
      width: 90%;
      text-align: center;
    }
  
    .tit {
      opacity: 0;
      animation: vsTxt1 1.5s 0.2s ease forwards 1;
      -webkit-animation: vsTxt1 1.5s 0.2s ease forwards 1;
      padding-right: 30vw;
      font-size: 6.8vw;
      line-height: 6.8vw;
      font-weight: 900;
      text-transform: uppercase;
      letter-spacing: -0.05em;
      color:#fff;
    }
  
    .exTxt {
      opacity: 0;
      animation: vsTxt2 1.5s 0.4s ease forwards 1;
      -webkit-animation: vsTxt2 1.5s 0.4s ease forwards 1;
      padding-left: 20vw;
      font-size: 6.8vw;
      line-height: 6.8vw;
      font-weight: 900;
      text-transform: uppercase;
      letter-spacing: -0.05em;
      color: #abe500;
    }
  }
  
  @media (max-width: 768px) {
    .intro {
      .tit {
        padding-right: 0;
        font-size: 10vw;
        line-height: 10vw;
      }
  
      .exTxt {
        padding-left: 0;
        font-size: 10vw;
        line-height: 10vw;
      }
    }
  }
  
  @keyframes vsTxt1 {
    0% {
      transform: translateX(50px);
      opacity: 0;
    }
  
    100% {
      transform: translateX(0);
      opacity: 1;
    }
  }
  
  @keyframes vsTxt2 {
    0% {
      transform: translateX(-50px);
      opacity: 0;
    }
  
    100% {
      transform: translateX(0);
      opacity: 1;
    }
  }
  
  @-webkit-keyframes vsTxt1 {
    0% {
      -webkit-transform: translateX(50px);
      opacity: 0;
    }
  
    100% {
      -webkit-transform: translateX(0);
      opacity: 1;
    }
  }
  
  @-webkit-keyframes vsTxt2 {
    0% {
      -webkit-transform: translateX(-50px);
      opacity: 0;
    }
  
    100% {
      -webkit-transform: translateX(0);
      opacity: 1;
    }
  }
  

</style>