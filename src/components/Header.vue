<script setup>
  import { headerNavMo } from '../constants';
</script>

<template>
  <header id="header" role="banner">
    <h1><a href="/"> <img src="@/assets/img/logo.png" alt="Logo"></a></h1>
    <div class="pcNav">
        <nav class="nav" role="navigation" aria-label="메인 메뉴">
            <ul>     
              <li v-for="(nav, key) in headerNavMo" :key="key">
                <a :href="nav.url">{{ nav.title }}</a>
              </li>            
            </ul>
        </nav>
    </div>
    <div 
      class="moNav" :class="{ active: isNavVisible }"
    >
        <button 
          class="moIcon"
          aria-controls="primary-menu"
          :aria-expanded="isNavVisible.toString()"
          @click="toggleMobileMenu"
        >
            <span></span>
            <span></span>
            <span></span>
        </button>
        <div class="moMenu">
            <nav>
                <ul>
                  <li v-for="(nav, key) in headerNavMo" :key="key">
                    <a :href="nav.url" @click="scrollLink($event)">{{ nav.title }}</a>
                  </li>        
                </ul>
            </nav>            
        </div>
    </div>
  </header>
</template>

<script>



export default {
    data() {
        return {
            isNavVisible: false,
        };
    },
    methods: {
        toggleMobileMenu() {
            this.isNavVisible = !this.isNavVisible;
        },
        scrollLink(event) {
            event.preventDefault();

            const targetId = event.target.getAttribute("href");
            const targetElement = document.querySelector(targetId);

            if (targetElement) {
                targetElement.scrollIntoView({ behavior: "smooth" });
            }
             // 모바일 메뉴 닫기
            this.isNavVisible = false;
        },
    },
};
</script>

<style lang="scss" scoped>
  /* @import "@/assets/scss/mixin.scss"; */

#header {
  h1 {
    position: absolute;
    left: 30px;
    top: 14px;
    opacity: 0.8;
  }

  width: 96%;
  height: 70px;
  z-index: 5000;
  display: flex;
  justify-content: center;
  align-items: center;
  position: fixed;
  left: 2%;
  top: 25px;
  border: 1px solid #2e2e2e;
  border-left: 0;
  border-right: 0;
  backdrop-filter: blur(5px);
}

.pcNav {
  display: none;

  li {
    display: inline-block;
    overflow: hidden;
    position: relative;

    + li {
      margin-left: 3vw;
    }

    a {
      font-size: 16px;
      font-weight: 400;
      text-transform: uppercase;

      &.active {
        color: #46bcda;
      }

      &::after {
        content: "";
        width: 0;
        height: 2px;
        display: block;
        background-color: #46bcda;
        transition: width .5s;
      }
    }

    &:hover a {
      color: #46bcda;

      &.acteve {
        color: #46bcda;
      }

      &::after {
        width: 100%;
      }
    }
  }
}

.moNav {
  display: block;
  position: fixed;
  left: 0px;
  top: 0px;
  z-index: 3000;
  width: 100%;
  height: 0;
  transition: height 1s;
}

.moIcon {
  position: absolute;
  right: 30px;
  top: 23px;
  z-index: 10000;
  width: 25px;
  height: 20px;
  cursor: pointer;

  span {
    position: absolute;
    left: 0;
    width: 100%;
    height: 2px;
    background: #fff;
    transition: .7s;

    &:nth-child(1) {
      top: 0;
    }

    &:nth-child(2) {
      top: 9px;
    }

    &:nth-child(3) {
      top: 18px;
    }
  }
}

.moMenu {
  width: 100%;
  height: calc(100% - 50px);
  overflow: hidden;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  text-align: center;
  position: absolute;
  left: 0;
  top: -100%;
  background-color: #000;
  transition: 1s;
}

.moNav.active {
  height: 100vh;

  .moMenu {
    top: 0;
  }

  .moIcon span {
    background: #fff;

    &:nth-child(1) {
      top: 9px;
      transform: rotate(45deg);
    }

    &:nth-child(2) {
      display: none;
    }

    &:nth-child(3) {
      top: 9px;
      transform: rotate(-45deg);
    }
  }
}

.moMenu {
  nav {
    margin-bottom: 30px;
  }

  li a {
    font-size: 5vw;
    font-weight: 800;
    line-height: 1.8;
    text-transform: uppercase;
    transition: all .3s;
  }
}

.mList li {
  width: 40px;
  height: 40px;
  padding: 0 10px;
  display: inline-block;
  border-radius: 50%;

  a {
    font-size: 4vw;
    line-height: 40px;
  }

  &:nth-child(3) a {
    font-size: 3.5vw;
  }
}

.moMenu li a {
  &:hover, &.active {
    color: #46bcda;
  }
}

.mList li:hover {
  background-color: #46bcda;

  a {
    color: #000;
  }
}

@media (max-width: 1200px) {
  #header {
    justify-content: right;
    padding-right: 30px;
  }

  #nav {
    margin-right: 30px;
  }
}

@media (max-width: 768px) {
  #header {
    height: 70px;
  }

  .pcNav {
    display: none;
  }

  .moNav {
    display: block;
  }
}

</style>