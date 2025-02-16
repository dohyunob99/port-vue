<script setup>
  import { skillTxt } from '../constants';
</script>

<template>
    <section id="skillCon" class="skillCon">
        <div class="inner">  
            <h2>{{ skillTxt.title }}</h2>
            <div class="profileBx">
                <div class="photo"><img src="@/assets/img/nho.jpg" alt="nho"></div>
                <div class="txtCon">
                  안녕하세요. 웹 표준과 접근성을 고려하여 똑똑한 웹 페이지를 구현하는 웹 퍼블리셔 나현오입니다.<br><br>

                  퍼블리셔는 디자인과 개발 중간에 있어 커뮤니케이션이 중요하다고 생각합니다.<br>
                  프로젝트를 진행하다 보면 서로의 생각이 다른 경우도 있어 결과가 만족스럽지 않은 경우도 생기는데 어떤 업무를 시작하게 되면 커뮤니케이션을 많이 하면서 각자의 파트에서 만족스러운 결과가 나오도록 노력하는 편입니다.<br><br>

                  항상 더 나은 결과물을 만들기 위해 끊임없이 고민하고 책임감을 가지고 최선을 다해 일하겠습니다.<br>
                  감사합니다.
                </div>
            </div>
            <ul class="cardList">
                <li>HTML</li>
                <li>CSS</li>
                <li>Javascript</li>
                <li>Jquery</li>
                <li>Git</li>
                <li>SVN</li>
                <li>PhotoShop</li>
                <li>Figma</li>
                <li>Zeplin</li>
                <li>
                    <a href="https://nho-vue.netlify.app" target="_blank">VUE 
                        <span><em class="none">VUE 프레임워크(컴포넌트, SCSS) 사용하여<br> 동일한 포트폴리오를 만들었습니다. </em><em class="link">포트폴리오 바로가기</em></span>
                    </a>             
                </li>           
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
              .fromTo(".cardList li:nth-child(9)", {
                  x: 0,       
              }, {
                  x: 80,       
                  autoAlpha:1,
                  duration: 1,   
              })
              .fromTo(".cardList li:nth-child(10)", {
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
      overflow: hidden;
      font-size: 2vw;
      font-weight: 900;
      line-height: 2vw;
      color: #000;
      text-transform: uppercase;
      letter-spacing: -0.05em;
      text-align: center;

      &:nth-child(2n) {
        margin-top: 50px;
      }

      a {
        display: block;
        width: 100%;
        height: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        color: #fff;
        background: #008773;

        span {
          display: block;
          margin-top: 10px;
          font-size: 1vw;
          line-height: 1.4vw;
          font-weight: 400;
          padding: 0 20px;

          em.link {
            display: block;
            background: #153f38;
            padding: 10px 15px;
            border-radius: 5px;
            font-size: 16px;
            margin-top: 10px;
          }
        }
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

    .cardList li {
      height: 15vw;

      a span em {
        display: none;

        &.link {
          margin-top: 0;
          font-size: 12px;
          line-height: 14px;
        }
      }
    }
  }
}


</style>