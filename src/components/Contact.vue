<template>
    <section id="contact" class="contact">
        <div class="inner">
            <h2 class="hidTxt">이메일 연락처 영역</h2>
            <div class="txtLeft">
                <div class="txt1">
                    Thank you for  
                </div>
                <div class="txt2">
                viewing the portfolio 
                </div>
                <div class="txt3">
                to the end
                </div>
                <div class="txtEmail">
                    <span>E-mail: <a href="mailto:skgusdh@naver.com">skgusdh@naver.com</a></span>      
                </div>
            </div>
        </div>
    </section>
</template>
<script>

</script>
<style lang="scss" scoped>

/* contact css */

.contact {
  .inner {
    width: 100%;
    height: 100vh;
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    background: #1a1a1a;
    box-sizing: border-box;
    padding: 10%;
  }

  .txtLeft {
    font-size: 6.4vw;
    font-weight: 900;
    text-transform: uppercase;
    letter-spacing: -0.05em;

    .txt2 {
      color: #abe500;
    }
  }

  .txtEmail {
    margin-top: 1.8vw;
    display: block;
    font-size: 20px;
    text-transform: initial;
    font-weight: 400;
    letter-spacing: 0.3em;
    text-align: center;
    padding: 10px 50px;
    border-radius: 30px;
    background: #000;

    span {
      display: inline-block;
      margin: 0 10px;
    }
  }
}

@media (max-width: 768px) {
  .contact {
    .inner {
      height: auto;
      text-align: center;
    }

    .txtLeft {
      display: block;
      font-size: 3.25rem;
    }
  }
}

</style>