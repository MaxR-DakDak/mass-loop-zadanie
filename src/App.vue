<template>
   <Menu/>
   <div class="page">
      <!-- header -->
      <div class="page__header title title_big">Inteligentna kruszarka, która zamienia szkło w piasek.</div>
      <img class="page__img" src="@/assets/maasloop.png" alt="maasloop">
      <img class="page__mob-btn" src="@/assets/mob_btn.png" alt="addtocart">

      <!-- rectangle -->
      <div class="page__rectangle">
         <div class="title">Płać 5 razy mniej za wywóz odpadów szklanych.</div>
         <div class="text">Kruszarka zmniejsza gabaryty szklanych śmieci, a Ty płacisz PIĘ-CIO-KROT-NIE niższe rachunki za ich wywóz.</div>
      </div>

      <!-- calculator -->
      <div class="page__calculator-title title">Ile zaoszczędzisz?</div>
      <div class="page__calculator-subtitle text">Rachunek jest prosty.</div>
      <div class="page__calculator">
         <div class="page__input-blocks">
            <div class="page__input-block">
               <div class="title title_line20 title_extra-small">Ile pojemników na szkło zapełniasz miesięcznie?</div>
               <input class="page__input text" type="number" v-model="container" placeholder="20">
            </div>
            <div class="page__input-block page__input-block_small">
               <div class="title title_line20 title_extra-small">Ile płacisz za wywóz jednego pojemnika na szkło?</div>
               <input class="page__input text" type="number" v-model="pay" placeholder="20">
            </div>
         </div>
         <div class="page__result">
            <div class="page__result-text title title_white title_extra-small">
               <div> Dzięki kruszarce zaoszczędzisz</div>
               <div class="title title_white title_opacity title_medium" id="calcSumDiv">{{ calcSum }} zł</div>
               <div>rocznie.</div>
            </div>
         </div>
      </div>

      <!-- bottom -->
      <div class="page__bottom_text text">To na co wydasz zaoszczędzoną gotówkę?</div>
      <div class="page__btn">KUP<span class="page__btn_price">8499 zł</span></div>
      <div class="page__bottom_title title title_small">
         <span class="page__bottom-margin"> Brzmi dobrze? </span>Uważaj. Dopiero się rozkręcamy!
      </div>
   </div>
</template>

<script>
import Menu from './components/Menu.vue'

export default {
   name: 'App',
   components: {
      Menu,
   },
   data() {
      return {
         container: null,
         pay: null,
         calcSum: 900,
      }
   },
   methods: {
      calcCost() {
         if (this.container && this.pay) {
            this.calcSum = Math.round(12 * (
                this.container * this.pay - this.container * this.pay / 5))
            document.getElementById('calcSumDiv').classList.remove("title_opacity");
            document.getElementById('calcSumDiv').classList.add("title_orange");
         }
      }
   },
   watch: {
      container() {
         this.calcCost();
      },
      pay() {
         this.calcCost();
      },
   }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;600;700;800;900&display=swap');

$mediaSmall: 767.98px;
$mediaMedium: 991.98px;
$mediaLarge: 1439.98px;
$textColor: #212121;

body {
   font-family: 'Montserrat', sans-serif;
   margin: 0;
}

::placeholder {
   color: #C2C2C2;
   font-weight: 300;
}

.page {
   display: flex;
   flex-direction: column;
   align-items: center;
   padding-top: 90px;
   padding-bottom: 90px;
   overflow-x: hidden;
   text-align: center;

   @media screen and (max-width: $mediaMedium) {
      padding-left: 20px;
      padding-right: 20px;
   }

   &__header {
      max-width: 997px;
      margin-top: 74px;
      padding-left: 1px;

      @media screen and (max-width: $mediaMedium) {
         margin-top: 45px;
      }
   }

   &__img {
      margin-top: 59px;

      @media screen and (max-width: $mediaMedium) {
         margin-top: 57px;
         width: 100%;
         height: auto;
      }

      @media screen and (max-width: $mediaSmall) {
         width: 142%;
      }
   }

   &__mob-btn {
      display: none;

      @media screen and (max-width: $mediaSmall) {
         display: block;
         position: absolute;
         right: 0;
         top: 566px;
      }
   }

   &__rectangle {
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      width: 100%;
      height: 365px;
      box-sizing: border-box;
      background-color: #FFB001;
      border: 20px solid white;
      border-radius: 30px;
      margin-top: -400px;
      padding: 59px 339px 64px 358px;


      @media screen and (max-width: $mediaLarge) {
         padding: 50px 100px 74px;
      }

      @media screen and (max-width: $mediaMedium) {
         border-width: 15px;
         margin-top: -182px;
         height: 343px;
         width: calc(100% + 70px);
      }

      @media screen and (max-width: $mediaSmall) {
         padding: 50px 20px 74px;
      }

      & div:nth-child(1) {
         margin-left: -16px;
         @media screen and (max-width: $mediaMedium) {
            margin-left: unset;
         }
      }
   }

   &__calculator-title {
      margin-top: 91px;

      @media screen and (max-width: $mediaMedium) {
         margin-top: 48px;
      }
   }

   &__calculator-subtitle {
      margin-top: 40px;

      @media screen and (max-width: $mediaMedium) {
         margin-top: 28px;
      }
   }

   &__calculator {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      flex-wrap: wrap;
      gap: 28px;
      width: 100%;
      max-width: 1012px;
      margin-top: 84px;

      @media screen and (max-width: $mediaMedium) {
         margin-top: 60px;
         gap: 20px;
      }

      &_block {
         display: inline-flex;
         gap: 30px;
      }
   }

   &__input-blocks {
      display: inline-flex;
      gap: 30px;

      @media screen and (max-width: $mediaMedium) {
         flex-wrap: wrap;
         gap: 20px
      }
   }

   &__input-block {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: space-between;
      flex-grow: 1;
      box-sizing: border-box;
      border-radius: 15px;
      background-color: #fafafd;
      height: 260px;
      padding: 38px 72px 52px 76px;

      @media screen and (max-width: $mediaMedium) {
         height: 240px;
         padding: 41px 34px 40px 34px
      }

      &_small {
         @media screen and (max-width: $mediaMedium) {
            height: 230px;
         }
      }
   }

   &__input {
      height: 66px;
      max-width: 219px;
      border-radius: 15px;
      border: 1px solid #{$textColor};
      text-align: center;
      outline: none;

      @media screen and (max-width: $mediaMedium) {
         width: 225px;
      }

      &:active, &:focus {
         border-color: #FFB001;
      }
   }

   &__result {
      display: flex;
      align-items: center;
      width: 100%;
      height: 127px;
      box-sizing: border-box;
      background-color: #{$textColor};
      border-radius: 15px;

      @media screen and (max-width: $mediaMedium) {
         height: 213px;
      }
   }

   &__result-text {
      display: inline-flex;
      align-items: center;
      justify-content: space-between;
      width: 100%;
      padding-left: 225px;
      padding-top: 1px;
      padding-right: 223px;
      box-sizing: border-box;
      height: 100%;

      & div:nth-child(2) {
         margin-left: 24px;
         margin-right: 22px;
         line-height: 20px;
      }

      @media screen and (max-width: $mediaSmall) {
         display: flex;
         flex-direction: column;
         justify-content: space-between;
         padding: 57px 0 42px;

         & div:nth-child(2) {
            margin-top: 15px;
            margin-right: 17px;
         }

         & div:nth-child(3) {
            margin-left: 3px;
         }
      }
   }

   &__bottom_text {
      margin-top: 82px;

      @media screen and (max-width: $mediaMedium) {
         margin-top: 60px;
      }
   }

   &__btn {
      display: flex;
      justify-content: center;
      align-items: center;
      gap: 7px;
      box-sizing: border-box;
      border-radius: 47.5px;
      background-color: #FFB001;
      height: 95px;
      width: 386px;
      margin-top: 59px;
      font-weight: 900;
      font-size: 24px;
      cursor: pointer;

      @media screen and (max-width: $mediaMedium) {
         margin-top: 62px;
         width: 100%;
         height: 80px;
         line-height: 24px;
         font-size: 20px;
      }

      &_price {
         font-weight: 400;
      }
   }

   &__bottom_title {
      width: 450px;
      margin-top: 77px;
      margin-left: 1px;

      @media screen and (max-width: $mediaMedium) {
         margin-top: 60px;
         width: 243px;
      }
   }

   &__bottom-margin {
      margin-left: -3px;
   }
}

.title {
   font-size: 40px;
   font-weight: 900;
   color: #{$textColor};

   @media screen and (max-width: $mediaMedium) {
      font-size: 30px;
   }

   @media screen and (max-width: $mediaSmall) {
      font-size: 24px;
   }

   &_big {
      font-size: 55px;
      @media screen and (max-width: $mediaMedium) {
         font-size: 35px;
      }
   }

   &_medium {
      font-size: 24px;
      @media screen and (max-width: $mediaSmall) {
         font-size: 28px;
      }
   }

   &_small {
      font-size: 28px;

      @media screen and (max-width: $mediaMedium) {
         font-size: 20px;
      }
   }

   &_extra-small {
      font-size: 20px;
      @media screen and (max-width: $mediaMedium) {
         font-size: 16px;
      }
   }

   &_line20 {
      line-height: 30px;
      @media screen and (max-width: $mediaMedium) {
         line-height: 20px
      }
   }

   &_white {
      color: white;
   }

   &_orange {
      color: #FFB001;
   }

   &_opacity {
      opacity: 0.5;
   }
}

.text {
   font-size: 20px;
   font-weight: 400;
   color: #{$textColor};
   line-height: 1.59;

   @media screen and (max-width: $mediaMedium) {
      font-size: 16px;
   }

   &_900 {
      font-weight: 900;
   }

   &_white {
      color: white;
   }
}
</style>
