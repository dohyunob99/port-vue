<script setup>
  import { skillTxt } from '../constants';
  import { skillList } from '../constants';
</script>

<template>
    <section id="skillCon" class="skillCon">
        <div class="inner">  
            <h2>{{ skillTxt.title }}</h2>
            <div class="profileBx">
                <div class="photo"><img src="@/assets/img/nho.jpg" alt="nho"></div>
                <div class="txtCon">
                    {{ skillTxt.desc }}
                </div>
            </div>
            <ul class="cardList">
                <li v-for="(listTxt, key) in skillList" :key="key">{{ listTxt.listTxt }}</li>        
            </ul>
        </div>
    </section>
</template>


<script>
  import gsap from "gsap";
  import ScrollTrigger from "gsap/ScrollTrigger";
  gsap.registerPlugin(ScrollTrigger);

  export default {
      mounted: function () {
          this.scrollAnimation();
      },
      methods: {
          scrollAnimation() {            

          const skillCon = gsap.timeline();
          skillCon
              .fromTo(
                ".skillCon h2",
                { y: 50 },
                { y: 0, autoAlpha: 1, duration: 0.3 }
              )
              .fromTo(
                ".skillCon .photo",
                { x: -50 },
                { x: 0, autoAlpha: 1, duration: 0.2 }
              )
              .fromTo(
                ".skillCon .txtCon",
                { x: -50 },
                { x: 0, autoAlpha: 1, duration: 0.2 }
              );

            ScrollTrigger.create({
              animation: skillCon,
              trigger: "#skillCon",
              start: "top 40%",
              end: "bottom bottom",
              pin: false,
              anticipatePin: 1,
            });

          const skillCon2 = gsap.timeline();
          skillCon2.fromTo(".cardList li:nth-child(1)", {
                  x: 0,       
              }, {
                  x: 80,       
                  autoAlpha:1,
                  duration: 3,  
            
              })
              .fromTo(".cardList li:nth-child(2)", {
                  x: 0,       
              }, {
                  x: -80,       
                  autoAlpha:1,
                  duration: 3,  
            
              })
              .fromTo(".cardList li:nth-child(3)", {
                  x: 0,       
              }, {
                  x: 80,       
                  autoAlpha:1,
                  duration: 1,  
          
              })
              .fromTo(".cardList li:nth-child(4)", {
                  x: 0,       
              }, {
                  x: -80,       
                  autoAlpha:1,
                  duration: 1,   
            
              })
              .fromTo(".cardList li:nth-child(5)", {
                  x: 0,       
              }, {
                  x: 80,       
                  autoAlpha:1,
                  duration: 1, 
            
              })
              .fromTo(".cardList li:nth-child(6)", {
                  x: 0,       
              }, {
                  x: -80,       
                  autoAlpha:1,
                  duration: 1,  

              })
              .fromTo(".cardList li:nth-child(7)", {
                  x: 0,       
              }, {
                  x: 80,       
                  autoAlpha:1,
                  duration: 1,   
              })
              .fromTo(".cardList li:nth-child(8)", {
                  x: 0,       
              }, {
                  x: -80,       
                  autoAlpha:1,
                  duration: 1,   
              })
              
            
          ScrollTrigger.create({
              animation: skillCon2,
              trigger: "#skillCon",
              start: "top 40$",
              end: "bottom bottom",
              scrub: true,
              pin: false, 
              anticipatePin: 1,
              //markers: true
          });


          },
      },
  };
</script>

<style lang="scss" scoped>
/* skill css */

.skillCon {
  border: 26px solid #111;

  .inner {
    position: relative;
    width: 100%;
    padding: 110px 5% 5vw;
    background: #000;
    box-sizing: border-box;
  }

  h2 {
    opacity: 0;
    font-size: 4.375rem;
    font-weight: 900;
    text-transform: uppercase;
    letter-spacing: -0.05em;
  }

  .profileBx {
    position: relative;
    margin-top: 20px;
    padding: 0 0 0 250px;

    .photo {
      opacity: 0;
      position: absolute;
      left: 0;
      top: 0;
      width: 200px;
      border-radius: 10px;
      overflow: hidden;

      img {
        width: 100%;
      }
    }

    .txtCon {
      opacity: 0;
      position: relative;
      padding: 0 20px 20px 20px;
      font-size: 20px;
      line-height: 32px;
      font-weight: 400;
      width: 90%;
      color: #fff;
      background: #000;
      border-radius: 10px;
      word-break: keep-all;
      white-space: pre-wrap;
    }
  }

  .cardList {
    margin-top: 5vw;
    position: relative;
    overflow: hidden;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    gap: 5vw 10px;

    &::before {
      content: '';
      display: block;
      position: absolute;
      left: 50%;
      top: 50%;
      width: 30px;
      height: 100%;
      background: #d1d1d1;
      transform: translate(-50%, -50%);
      border-radius: 20px;
    }

    li {
      flex: 0 0 35.5%;
      height: 12vw;
      border-radius: 20px;
      background: #d1d1d1;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 2vw;
      font-weight: 900;
      line-height: 2vw;
      color: #000;
      text-transform: uppercase;
      letter-spacing: -0.05em;

      &:nth-child(2n) {
        margin-top: 50px;
      }
    }
  }
}

@media (max-width: 768px) {
  .skillCon {
    h2 {
      font-size: 3.125rem;
    }

    .profileBx {
      padding: 0 0 0 0;

      .photo {
        position: relative;
        left: auto;
        top: auto;
        width: 100%;
        text-align: center;
        background: #fff;

        img {
          width: 80%;
        }
      }

      .txtCon {
        padding: 20px 0 0 0;
        width: 100%;
      }
    }
  }
}

</style>