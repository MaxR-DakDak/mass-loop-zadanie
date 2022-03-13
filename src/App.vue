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
               <input class="page__input text" type="text" name="" id="">
            </div>
            <div class="page__input-block page__input-block_small">
               <div class="title title_line20 title_extra-small">Ile płacisz za wywóz jednego pojemnika na szkło?</div>
               <input class="page__input text" type="text" name="" id="">
            </div>
         </div>
         <div class="page__result">
            <div class="title title_white title_extra-small"> Dzięki kruszarce zaoszczędzisz 900 zł rocznie.</div>
         </div>
      </div>

      <!-- bottom -->
      <div class="page__bottom_text text">To na co wydasz zaoszczędzoną gotówkę?</div>
      <div class="page__btn">KUP<span class="page__btn_price">8499 zł</span></div>
      <div class="page__bottom_title title title_small"> <span class="page__bottom-margin"> Brzmi dobrze? </span> Uważaj. Dopiero się rozkręcamy!</div>
   </div>
</template>

<script>
import Menu from './components/Menu.vue'

export default {
   name: 'App',
   components: {
      Menu,
   }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;600;700;800;900&display=swap');

$text_color_21: #212121;

body {
   font-family: 'Montserrat', sans-serif;
   margin: 0;
}

.page {
   display: flex;
   flex-direction: column;
   align-items: center;
   padding-top: 90px;
   padding-bottom: 90px;
   overflow-x: hidden;
   text-align: center;

   @media screen and (max-width: 575.98px) {
      padding-left: 20px;
      padding-right: 20px;
   }

   &__header {
      max-width: 997px;
      margin-top: 74px;
      padding-left: 1px;

      @media screen and (max-width: 575.98px) {
         margin-top: 45px;
      }
   }

   &__img {
      margin-top: 59px;

      @media screen and (max-width: 575.98px) {
         margin-top: 57px;
         width: 142%;
         height: auto;
      }
   }

   &__mob-btn{
      display: none;

      @media screen and (max-width: 575.98px) {
         display: block;
         position: absolute;
         right: 0;
         bottom: -4px;
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

      @media screen and (max-width: 575.98px) {
         padding: 50px 20px 74px;
         border-width: 15px;
         margin-top: -182px;
         height: 343px;
         width: calc(100% + 70px);
      }
   }

   &__calculator-title {
      margin-top: 91px;

      @media screen and (max-width: 575.98px) {
         margin-top: 48px;
      }
   }

   &__calculator-subtitle {
      margin-top: 40px;

      @media screen and (max-width: 575.98px) {
         margin-top: 28px;
      }
   }

   &__calculator {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      flex-wrap: wrap;
      gap: 20px;
      width: 100%;
      max-width: 1012px;
      margin-top: 84px;

      @media screen and (max-width: 575.98px) {
         margin-top: 60px;
      }

      &_block {
         display: inline-flex;
         gap: 30px;
      }
   }

   &__input-blocks {
      display: inline-flex;
      gap: 30px;

      @media screen and (max-width: 575.98px) {
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

      @media screen and (max-width: 575.98px) {
         height: 240px;
         padding: 41px 34px 40px 34px
      }

      &_small {
         @media screen and (max-width: 575.98px) {
            height: 230px;
         }
      }
   }

   &__input {
      height: 66px;
      max-width: 219px;
      border-radius: 15px;
      border: 1px solid #{$text_color_21};
      text-align: center;
      outline: none;

      @media screen and (max-width: 575.98px) {
         width: 225px;
      }

      &:active, &:focus {
         border-color: #FFB001;
      }
   }

   &__result {
      display: flex;
      justify-content: center;
      align-items: center;
      width: 100%;
      height: 127px;
      box-sizing: border-box;
      background-color: #{$text_color_21};
      border-radius: 15px;

      @media screen and (max-width: 575.98px) {
         height: 213px;
      }
   }

   &__bottom_text {
      margin-top: 82px;

      @media screen and (max-width: 575.98px) {
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

      @media screen and (max-width: 575.98px) {
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
      margin-top: 78px;

      @media screen and (max-width: 575.98px) {
         margin-top: 60px;
         width: 243px;
         margin-left: 1px;
      }
   }

   &__bottom-margin{
      margin-left: -3px;
   }
}

.title {
   font-size: 40px;
   font-weight: 900;
   color: #{$text_color_21};

   @media screen and (max-width: 575.98px) {
      font-size: 24px;
   }

   &_big {
      font-size: 55px;
      @media screen and (max-width: 575.98px) {
         font-size: 35px;
      }
   }

   &_small {
      font-size: 28px;

      @media screen and (max-width: 575.98px) {
         font-size: 20px;
      }
   }

   &_extra-small {
      font-size: 20px;
      @media screen and (max-width: 575.98px) {
         font-size: 16px;
      }
   }

   &_line20 {
      line-height: 20px
   }

   &_white {
      color: white;
   }
}

.text {
   font-size: 20px;
   font-weight: 400;
   color: #{$text_color_21};
   line-height: 1.59;

   @media screen and (max-width: 575.98px) {
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
