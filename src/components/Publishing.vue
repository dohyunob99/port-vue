<script setup>
  import { pubTxt } from '../constants';
  import { pubList } from '../constants';
</script>

<template>
   <div id="horizontal">
        <section class="horIContent">
            <div class="inner">
                <div class="txtLeft">
                    <h2 class="tit">{{ pubTxt.title }} <span>{{ pubTxt.subTitle }}</span></h2>
                    <div class="exTxt">{{ pubTxt.desc1 }}</div>
                    <div class="exTxt2"><a href="#none">{{ pubTxt.desc2 }}</a>{{ pubTxt.desc3 }}</div>
                </div>
            </div>
        </section>
        <!-- //horIContent -->

        <section class="horIContent" v-for="(pubCon, key) in pubList" :key="key">
            <div class="inner">
                <h3><span>{{ pubCon.title }} </span><em>{{ pubCon.title2 }}</em></h3>
                <div class="imgBx"><img :src="pubCon.img" :alt="pubCon.imgAlt"></div>
                <div class="txtCon">
                    <p>{{ pubCon.exTxt }}</p>
                    <a :href="pubCon.link" target="_blank">Site View →</a>
                </div>
            </div>
        </section>
        <!-- //horIContent -->
    </div> 
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

          //섹션가로모드
          const horizontal = document.querySelector("#horizontal"); 
          const sections = gsap.utils.toArray("#horizontal > section");

          let scrollTween = gsap.to(sections, {
              xPercent: -100 * (sections.length -1),
              ease: "none",
              scrollTrigger: {
                  trigger: horizontal,
                  start: "top top",
                  end: () => "+=" + (horizontal.offsetWidth - innerWidth),
                  pin: true,
                  scrub: 1,
                  invalidateOnRefresh: true,
                  anticipatePin: 1,
                  onUpdate: (self) => {
                      // 현재 스크롤 진행도를 기반으로 활성 섹션 인덱스 계산
                      const progress = self.progress;
                      const totalSections = sections.length;
                      const activeIndex = Math.round(progress * (totalSections - 1));
                    
                      // 모든 섹션에서 active 클래스 제거
                      sections.forEach((section, index) => {
                          section.classList.remove('active');
                      });
                    
                      // 현재 활성 섹션에 active 클래스 추가
                      if (sections[activeIndex]) {
                          sections[activeIndex].classList.add('active');
                      }
                  }
                  
                  // snap: {
                  //     snapTo: 1/(sections.length -1),
                  //     inertia: false,
                  //     duration: {min: 0.1, max: 0.1},
                  //     invalidateOnRefresh: true,
                  //     anticipatePin: 1
                  // }
              }
            });

          },
      },
  };
</script>

<style lang="scss" scoped>
/* Publishing css */

#horizontal {
  display: flex;
  flex-wrap: nowrap;
  width: 800%; 
  background: #1a1a1a;

  > section {
    width: 100%;
    background: #1a1a1a;

    &:first-child {
      background: #0a0909;
    }
  }
}

/* #horizontal > section:nth-child(2n){background:blue;} */

.horIContent {
  position: relative;
  width: 100%;
  height: 100vh;

  .inner {
    position: relative;
    width: 100%;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .txtLeft {
    position: relative;
    width: 100%;
    height: 100vh;
    padding: 0 0 0 5vw;
    display: flex;
    flex-direction: column;
    justify-content: center;
    box-sizing: border-box;

    h2 {
      font-size: 6.4vw;
      font-weight: 900;
      text-transform: uppercase;
      letter-spacing: -0.05em;

      span {
        color: #abe500;
      }
    }

    .exTxt {
      font-size: 1.8vw;
      font-weight: 300;
      text-transform: uppercase;
      letter-spacing: -0.05em;
      word-break: keep-all;
    }

    .exTxt2 {
      margin-top: 20px;
      font-size: 1.2vw;
      font-weight: 300;
      text-transform: uppercase;
      letter-spacing: -0.05em;

      a {
        display: inline-block;
        padding: 5px 20px;
        background: #000;
        border-radius: 15px;
      }
    }
  }

  h3 {
    transition: transform 1s ease;
    position: absolute;
    z-index: 5;
    left: 70px;
    top: 140px;
    font-size: 5.4vw;
    font-weight: 900;
    line-height: 5.8vw;
    text-transform: uppercase;
    letter-spacing: -0.05em;

    span {
      transition: transform 1.5s 0.5s ease;
      margin-right: 20px;
      color: #42ab80;
    }

    em {
      display: block;
      color: #e0e3e7;
    }
  }

  .imgBx {
    transition: transform 1.5s 0.3s ease;
    width: 50vw;
    height: 35vw;
    border: 2vw solid #000;
    border-radius: 20px;
    background: #fff;

    img {
      width: 100%;
      height: 100%;
    }
  }

  .txtCon {
    transition: transform 1.5s 0.5s ease;
    position: absolute;
    z-index: 5;
    right: 110px;
    bottom: 70px;
    width: 500px;
    min-height: 150px;
    padding: 30px;
    border-radius: 10px;
    overflow: hidden;

    &::before {
      position: absolute;
      left: 0;
      top: 0;
      content: '';
      display: block;
      width: 100%;
      height: 100%;
      background: #000;
      opacity: 0.7;
    }

    p {
      position: relative;
      z-index: 1;
      margin-bottom: 10px;
      font-size: 16px;
      font-weight: 400;
      word-break: keep-all;
    }

    a {
      position: relative;
      z-index: 1;
      display: inline-block;
      padding: 8px 20px;
      background: #333;
      border-radius: 15px;
      font-size: 13px;
    }
  }

  &.active {
    h3 {
      transform: translateX(30px);

      span {
        color: #3efbae;
      }
    }

    .txtCon {
      transform: translateX(-50px);
    }
  }
}

@media (max-width: 1024px) {
  .horIContent .imgBx {
    width: 64%;
    height: auto;
  }
}

@media (max-width: 768px) {
  .horIContent {
    .inner {
      flex-direction: column;
    }

    h3 {
      position: relative;
      width: 90%;
      left: auto;
      top: auto;
      margin-bottom: 10px;

      em {
        display: inline-block;
      }
    }

    .imgBx {
      width: 90%;
      height: auto;
    }

    .txtCon {
      position: relative;
      width: 90%;
      right: auto;
      bottom: auto;
      margin-top: 10px;
    }

    &.active {
      h2, .txtCon {
        transform: none;
      }
    }
  }
}

@media (max-width: 576px) {
  .horIContent .txtLeft {
    padding: 0 10vw;

    .tit {
      font-size: 8.4vw;
      line-height: 11.4vw;

      span {
        display: block;
      }
    }

    .exTxt, .exTxt2 {
      font-size: 2.8vw;
    }
  }
}

</style>