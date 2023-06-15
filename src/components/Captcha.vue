<template>
  <div id="rc-anchor-container" class="rc-anchor rc-anchor-normal rc-anchor-light">
    <div class="rc-anchor-content">
      <div class="rc-inline-block">
        <div class="rc-anchor-center-container">
          <div class="rc-anchor-center-item rc-anchor-checkbox-holder">
            <span class="recaptcha-checkbox goog-inline-block recaptcha-checkbox-unchecked rc-anchor-checkbox"
              v-on:click="isChildVisible = true">
              <div class="recaptcha-checkbox-border"></div>
              <div class="recaptcha-checkbox-checkmark"></div>
            </span>
          </div>
        </div>
      </div>
      <div class="rc-inline-block">
        <div class="rc-anchor-center-container">
          <label class="rc-anchor-center-item rc-anchor-checkbox-label">
            进行人机身份验证</label>
        </div>
      </div>
    </div>
    <div class="rc-anchor-normal-footer">
      <div class="rc-anchor-logo-portrait">
        <div class="rc-anchor-logo-img rc-anchor-logo-img-portrait"></div>
        <div class="rc-anchor-logo-text">kiraCAPTCHA</div>
      </div>
    </div>
  </div>
  <CaptchaBoxVue v-if="isChildVisible" @update:ispass="handleIsPass" @close="handleChildClose" :jsonFileCountProps="2" :jsonBaseUrlProps="/assets/" />
</template>

<script>
import CaptchaBoxVue from "./CaptchaBox.vue";
export default {
  components: {
    CaptchaBoxVue
  },
  data () {
    return {
      isChildVisible: false,
    };
  },
  methods: {
    handleIsPass (ispass) {
      this.isChildVisible = !ispass;
    },
    handleChildClose () {
      this.isChildVisible = false;
    },
  },
}
</script>

<style>
.rc-anchor {
  -webkit-border-radius: 3px;
  -moz-border-radius: 3px;
  border-radius: 3px;
  -webkit-box-shadow: 0 0 4px 1px rgba(0, 0, 0, .08);
  -moz-box-shadow: 0 0 4px 1px rgba(0, 0, 0, .08);
  box-shadow: 0 0 4px 1px rgba(0, 0, 0, .08);
  -webkit-box-shadow: 0 0 4px 1px rgba(0, 0, 0, .08);
  -moz-box-shadow: 0 0 4px 1px rgba(0, 0, 0, .08);
}

.rc-anchor-light.rc-anchor-normal,
.rc-anchor-light.rc-anchor-compact {
  border: 1px solid #d3d3d3;
}

.rc-anchor-light {
  background: #f9f9f9;
  color: #000;
}

.rc-anchor-normal {
  height: 74px;
  width: 300px;
}

.rc-anchor-normal .rc-anchor-content {
  height: 74px;
  width: 206px;
}

.rc-anchor-content {
  display: inline-block;
  position: relative;
}

.rc-inline-block {
  display: inline-block;
  height: 100%;
}

.rc-anchor-center-container {
  display: table;
  height: 100%;
}

.rc-anchor-center-item {
  display: table-cell;
  vertical-align: middle;
}

.rc-anchor-checkbox {
  margin: 0 12px 2px 12px;
}

.recaptcha-checkbox {
  border: none;
  font-size: 1px;
  height: 28px;
  margin: 4px;
  width: 28px;
  overflow: visible;
  outline: 0;
  vertical-align: text-bottom;
}

.goog-inline-block {
  position: relative;
  display: -moz-inline-box;
  display: inline-block;
}

.recaptcha-checkbox-border {
  -webkit-border-radius: 2px;
  -moz-border-radius: 2px;
  border-radius: 2px;
  background-color: #fff;
  border: 2px solid #c1c1c1;
  font-size: 1px;
  height: 24px;
  position: absolute;
  width: 24px;
  z-index: 1;
}

.recaptcha-checkbox-spinner {
  background-color: #f9f9f9;
  border: 6px solid #4d90fe;
  -webkit-border-radius: 36px;
  -moz-border-radius: 36px;
  border-radius: 36px;
  border-bottom-color: transparent;
  border-left-color: transparent;
  height: 36px;
  left: -4px;
  outline: 0;
  position: absolute;
  top: -4px;
  width: 36px;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
  opacity: 0;
  -webkit-animation: spinner-spin linear 2.5s infinite;
  -o-animation: spinner-spin linear 2.5s infinite;
  animation: spinner-spin linear 2.5s infinite;
  animation-play-state: paused;
  -webkit-transition-duration: 1s;
  -o-transition-duration: 1s;
  transition-duration: 1s;
}

.recaptcha-checkbox-spinner-overlay {
  content: "";
  position: absolute;
  top: -7px;
  left: -7px;
  width: 38px;
  height: 19px;
  background-color: #f9f9f9;
  -webkit-animation: overlay-spin linear 1s;
  -o-animation: overlay-spin linear 1s;
  animation: overlay-spin linear 1s;
  animation-play-state: paused;
  -webkit-transform-origin: bottom center;
  -ms-transform-origin: bottom center;
  -o-transform-origin: bottom center;
  transform-origin: bottom center;
  -webkit-border-radius: 38px 38px 0 0;
  -moz-border-radius: 38px 38px 0 0;
  border-radius: 38px 38px 0 0;
  -webkit-transform: rotateZ(45deg);
  -ms-transform: rotateZ(45deg);
  -o-transform: rotateZ(45deg);
  transform: rotateZ(45deg);
  opacity: 0;
}

.recaptcha-checkbox-checkmark {
  background-image: url(data:image/png;base64,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);
  background-repeat: no-repeat;
  border: none;
  height: 30px;
  left: -5px;
  outline: 0;
  position: absolute;
  width: 38px;
}

.rc-inline-block {
  display: inline-block;
  height: 100%;
}

.rc-anchor-normal .rc-anchor-checkbox-label {
  width: 152px;
}

.rc-anchor-checkbox-label {
  font-family: Roboto, helvetica, arial, sans-serif;
  font-size: 14px;
  font-weight: 400;
  line-height: 17px;
}

.rc-anchor-center-item {
  display: table-cell;
  vertical-align: middle;
}

.rc-anchor-normal-footer {
  display: inline-block;
  height: 74px;
  vertical-align: top;
  width: 70px;
}

.rc-anchor-logo-portrait {
  margin: 10px 0 0 1px;
  width: 58px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
}

.rc-anchor-logo-img-portrait {
  -webkit-background-size: 32px;
  -o-background-size: 32px;
  background-size: 32px;
  height: 32px;
  margin: 0 23px 0 23px;
  width: 32px;
}

.rc-anchor-logo-img {
  background: url(/assets/icon/KiraCaptcha.svg);
  background-repeat: no-repeat;
}

.rc-anchor-light .rc-anchor-logo-text,
.rc-anchor-light div a:link,
.rc-anchor-light div a:visited {
  color: #555;
}

.rc-anchor-logo-text {
  cursor: default;
  font-family: Roboto, helvetica, arial, sans-serif;
  font-size: 10px;
  font-weight: 400;
  line-height: 10px;
  margin-top: 5px;
  text-align: center;
}
</style>