<template>
   <div class="menu">
      <div class="menu__content">
         <img class="menu__logo" src="@/assets/logo.svg" alt="logo">

         <div class="menu__links">
            <a class="menu__link" href="/calc">Policz zyski</a>
            <a class="menu__link" href="/products">O produkcie</a>
            <a class="menu__link" href="/contact">Kontakt</a>
            <a class="menu__link menu__link_faq" href="/faq">FAQ</a>
         </div>

         <div class="menu__btns">
            <div class="menu__lang">
               <span> PL </span>
               <img class="menu_arrow" src="@/assets/arrow.svg" alt="lang">
            </div>

            <div class="menu__buynow menu__buynow_desktop">
               KUP
            </div>

            <div @click="hamburgerAnim($event)" class="menu__hamburger">
               <div class="menu__hamburger-line"></div>
               <div class="menu__hamburger-line"></div>
               <div class="menu__hamburger-line"></div>
            </div>

            <div v-bind:class="{ active: showMobList }" class="menu__links_mobile">
               <a class="menu__link menu__link_mobile1" href="/calc">Policz zyski</a>
               <a class="menu__link menu__link_mobile2" href="/products">O produkcie</a>
               <a class="menu__link menu__link_mobile3" href="/contact">Kontakt</a>
               <a class="menu__link menu__link_mobile4" href="/faq">FAQ</a>

               <div class="menu__buynow menu__buynow_mobile">
                  KUP
               </div>
            </div>
         </div>
      </div>
   </div>
</template>

<script>
export default {
   name: 'PageMenu',
   data() {
      return {
         showMobList: false,
      }
   },
   methods: {
      hamburgerAnim(event) {
         event.currentTarget.classList.toggle('active');
         this.showMobList = !this.showMobList;
      }
   }
}
</script>

<!--scoped-->
<style scoped lang="scss">

$text_color: #212121;

@mixin keyframes($animation-name) {
   @-webkit-keyframes #{$animation-name} {
      @content;
   }
   @-moz-keyframes #{$animation-name} {
      @content;
   }
   @-ms-keyframes #{$animation-name} {
      @content;
   }
   @-o-keyframes #{$animation-name} {
      @content;
   }
   @keyframes #{$animation-name} {
      @content;
   }
}

@mixin animation($str) {
   -webkit-animation: #{$str};
   -moz-animation: #{$str};
   -ms-animation: #{$str};
   -o-animation: #{$str};
   animation: #{$str};
}

@include keyframes(slideDown) {
   0% {
      height: 0;
   }
   100% {
      height: 100vh;
   }
}


.menu {
   display: flex;
   justify-content: center;
   align-items: center;
   position: fixed;
   height: 90px;
   left: 0;
   top: 0;
   right: 0;
   z-index: 10;
   background: #FFFFFF;
   box-shadow: 0 4px 24px -5px rgba(0, 0, 0, 0.15);
   padding-left: 110px;
   padding-right: 110px;
   color: #{$text_color};

   @media screen and (max-width: 575.98px) {
      padding-left: 20px;
      padding-right: 20px;
   }

   &__logo {
      height: 51px;
      width: auto;

      @media screen and (max-width: 575.98px) {
         height: 41.38px;
         width: auto;
      }
   }

   &__content {
      display: flex;
      justify-content: space-between;
      align-items: center;
      height: 57px;
      width: 100%;
   }

   &__links {
      display: flex;
      justify-content: center;
      align-items: center;
      gap: 64px;
      margin-left: 83px;

      @media screen and (max-width: 575.98px) {
         display: none;
      }

      &_mobile {
         display: none;
         position: fixed;
         top: 0;
         left: 0;
         right: 0;
         z-index: -1;
         background-color: white;

         @media screen and (max-width: 575.98px) {
            &.active {
               display: flex;
               flex-direction: column;
               align-items: center;
               gap: 77px;
               height: 100vh;
               padding-top: 137px;
               @include animation('slideDown 0.5s');
            }
         }
      }
   }

   &__link {
      text-decoration: none;
      font-size: 16px;
      font-weight: 400;
      color: #{$text_color};

      @media screen and (max-width: 575.98px) {
         font-size: 15px;
         font-weight: 500;
         line-height: 18px;
      }

      &_faq {
         margin-left: -6px;
      }

      @media screen and (max-width: 575.98px) {
         &_mobile1 {
            margin-left: -22px;
         }
         &_mobile2 {
            margin-left: -23px;
         }
         &_mobile3 {
            margin-left: -15px;
         }
         &_mobile4 {
            margin-left: -5px;
         }
      }
   }

   &__btns {
      display: inline-flex;
      justify-content: center;
      align-items: center;
      gap: 26px;

      @media screen and (max-width: 575.98px) {
         gap: 29px;
      }
   }

   &__lang {
      display: flex;
      gap: 10px;
   }

   &_arrow {
      padding-top: 2px;
   }

   &__buynow {
      display: flex;
      align-items: center;
      justify-content: center;
      background: #FFB001;
      width: 152px;
      height: 57px;
      border: 2px solid #FFB001;
      box-sizing: border-box;
      box-shadow: 0 20px 59px -10px rgba(0, 0, 0, 0.15);
      border-radius: 28.5px;
      font-weight: 900;
      font-size: 16px;
      line-height: 20px;
      padding-top: 2px;
      cursor: pointer;

      &_desktop{
         @media screen and (max-width: 575.98px) {
            display: none;
         }
      }

      &_mobile{
         height: 50px;
      }
   }

   &__hamburger {
      cursor: pointer;

      &.active {
         -webkit-transition: all 0.2s ease-in-out;
         -o-transition: all 0.2s ease-in-out;
         transition: all 0.2s ease-in-out;
         -webkit-transition-delay: 0.4s;
         -o-transition-delay: 0.4s;
         transition-delay: 0.4s;
         -webkit-transform: rotate(45deg);
         -ms-transform: rotate(45deg);
         -o-transform: rotate(45deg);
         transform: rotate(45deg);
      }

      &.active div:nth-child(1) {
         -webkit-transform: translateY(13px);
         -ms-transform: translateY(13px);
         -o-transform: translateY(13px);
         transform: translateY(13px);
         -webkit-transition-delay: 0.2s;
         -o-transition-delay: 0.2s;
         transition-delay: 0.2s;
      }

      &.active div:nth-child(2) {
         width: 0;
      }

      &.active div:nth-child(3) {
         -webkit-transform: translateY(-11px) rotate(90deg);
         -ms-transform: translateY(-11px) rotate(90deg);
         -o-transform: translateY(-11px) rotate(90deg);
         transform: translateY(-11px) rotate(90deg);
         -webkit-transition-delay: 0.2s;
         -o-transition-delay: 0.2s;
         transition-delay: 0.2s;
      }
   }

   &__hamburger-line {
      width: 36px;
      height: 2px;
      background: #{$text_color};
      margin: 10px auto;
      -webkit-transition: all 0.2s ease-in-out;
      -o-transition: all 0.2s ease-in-out;
      transition: all 0.2s ease-in-out;
   }
}

</style>
