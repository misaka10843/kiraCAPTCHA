<template>
  <div id="rc-anchor-container" class="rc-anchor rc-anchor-normal rc-anchor-light">
    <div class="rc-anchor-content">
      <div class="rc-inline-block">
        <div class="rc-anchor-center-container">
          <div class="rc-anchor-center-item rc-anchor-checkbox-holder"><span
              class="recaptcha-checkbox goog-inline-block recaptcha-checkbox-unchecked rc-anchor-checkbox" role="checkbox"
              aria-checked="false" id="recaptcha-anchor" dir="ltr" aria-labelledby="recaptcha-anchor-label"
              aria-disabled="false" tabindex="0">
              <div class="recaptcha-checkbox-border" role="presentation" style=""></div>
              <div class="recaptcha-checkbox-borderAnimation" role="presentation" style=""></div>
              <div class="recaptcha-checkbox-spinner" role="presentation"
                style="display: none; animation-play-state: running; opacity: 0; transform: scale(0);">
                <div class="recaptcha-checkbox-spinner-overlay" style="animation-play-state: running;"></div>
              </div>
              <div class="recaptcha-checkbox-checkmark" role="presentation"></div>
            </span></div>
        </div>
      </div>
      <div class="rc-inline-block">
        <div class="rc-anchor-center-container"><label class="rc-anchor-center-item rc-anchor-checkbox-label"
            aria-hidden="true" role="presentation" id="recaptcha-anchor-label"><span aria-live="polite"
              aria-labelledby="recaptcha-accessible-status"></span>进行人机身份验证</label></div>
      </div>
    </div>
    <div class="rc-anchor-normal-footer">
      <div class="rc-anchor-logo-portrait" aria-hidden="true" role="presentation">
        <div class="rc-anchor-logo-img rc-anchor-logo-img-portrait"></div>
        <div class="rc-anchor-logo-text">kiraCAPTCHA</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {

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

.recaptcha-checkbox-borderAnimation {
  background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAFQAAANICAYAAABZl8i8AAAABmJLR0QA/wD/AP+gvaeTAAAACXBIWXMAAABIAAAASABGyWs+AAAACXZwQWcAAABUAAADSAC4K4y8AAA4oElEQVR42u2dCZRV1ZX3q5iE4IQIiKQQCKBt0JLEIUZwCCk7pBNFiRMajZrIl9aOLZ8sY4CWdkDbT2McooaAEmNixFhpaYE2dCiLScWiQHCgoGQoGQuhGArKKl7V+c5/n33fO/V4w733nVuheXuv9V/rrnvP2Xud3zvTPee+ewsKxMTExMTExMTExMTExMTExMTExMTExMTExMTExMTExMTExMTExMTExMTExMTExMTExMTExP4OdtlT6ztAbRWvvLy8A3QkwxzH6tBGMMexIo+nCgraaf2E1U6A5g60o9a9rI7S5N1APQaSzl1MTExMTExMTExMTExMTExMTExMTExMTExMTExMTOwIsMueWl8EtVW88vLyIqit4qmCguOgtoT5AKuojWA+wCpqA5i9tP6d1UuA5g70K1oPsL4iTd4N1DMh6dzFxMTExMTExMTExMTExMTExMTExMTExMTExMTExMT+l9tlT63/stbtrC9HHa+8vPzLWrezIo+nCgq6a41hdW8LoAD5COv2NgAKkI+wbm8DoHhf0yOsnwjQ3IHeaQG9U5p87kAHa01kDZZOXkxMTExMTExMTExMTExMTExMTExMTExMTExMTEysLe2yp9afoTWWdUbU8crLy8/QGsuKPJ4qKOirdRWrb1vAfDJJZ0QM88kknREhTLwR5wmtJ1lPRPpmHK6VT/5q3g4SAx0bIVDUyidXr15NYqBjIwT6YwI5cqSRgfpjARoe6E8J4vjxRgboT6XJhwf6Dau5e/qGDEq5Qb3I+mriRTINERMTExMTExMTExMTExMTExMTExMTExMTEzss7LKn1neB2ipeeXl5F+hIBHma1mStF1g4Pi1CkKdpTdZ6gYXjyOKpgoLeWndoPcPCce8oYU63YHqaHgVUhjndgulpehRQNbgiree0XkgSzhVFAZRq5pQ3t7+w+0CMhGOvpkYAlGrmhx9++EJTUxMJx15NjQDozwngN7/5gnr/fSMcG6g/j6LPJHgAqZQi4diqqV0c95kEDyC9eDi2amoXhzCP0ppO8DZsiMejYwMU144SoP6BHk3gCgtf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);
  background-repeat: no-repeat;
  border: none;
  height: 28px;
  outline: 0;
  position: absolute;
  width: 28px;
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
  background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACYAAATsCAYAAADsAfBvAAAABmJLR0QA/wD/AP+gvaeTAAAACXBIWXMAAABIAAAASABGyWs+AAAACXZwQWcAAAAmAAAE7AAx5U8eAAAGSElEQVR42u3dMWicZQDG8dRo0FIrgqFFVCxWQaFD6VDnqiBCJ3NK1UVQsaOQQsAiKIoF7eLSwfLh0lXaKmZTEBQLgkNXRxHUqUvX+l6+7/guSQOXL5fLk9zvB++iwz0kl1zeP+llZgYAAAAAAGBHVb3T5TycNuqFcp5KG3VPOc94ygAAAADRqt7Zcs6ljXqrnH/LeTppVL/2XCvnmKcNAAAAEKuuPZ+ljerXnjvNOZ8yql97fm1G3cqqPlXvoXJ+KOek5zQAAABMt11Qe74oZ1/CqOHaMziXUsb1a88va8a9kfLp3F/Oj82oyxkfsdXjPihn1ncDAAAA9ga1Z/RRu672fJPRMFbXnsG5Us59KeO+WzPuejlzCePmyrk6NOz3cg6mfJXONp/Gm+XMp30Lmc17PzIAAIAJ3orUnlFHqT1dx6k9XcetrT39s1zOws4/79racyfvi6Ied/ku4xYTPq37mo/SYNTPK1/BQd+ALzRfsfsTX7LmZgAAgBF+dFZ7Rh21h2pP1ft85VM/oXGj1Z76jjn4/xMdt3HtWT2qf36bXEPbuPZ8uea/3Zh8Lti49uzgqNXjLmeNasepPVv7ogAAAEb40blb7al6H5dzartGdas97c389vjHda0963PBT9vxEdts7bkwuUtwt9ozoZv55mvPBHOB2rO1cWpP14FqDwAAW/qZ7YHEUUt5b0NR9T4auheMeVz32rP2EvzH+IZtvfZsw9VufLVnG+6bao/ao/aoPWoPAMAUhpWllZ/fAkcNftq9kDhqEFcOJNWeMRcftUftUXvUHrVH7VF7AICsF/3jqWFlgm870a1hnEkNK/NGqT1qj9qj9qg9ao/ao/YAwIReXxfyXmPbm/n1nHHrc8FFYcUotUftUXvUHrVH7VF71B4Apj2sPJ84anAJXkocNTjvCCtGqT1qj9qj9qg9ao/ao/YAMO1h5f7UsBL3PrFLWRdgucAotUftUXvUHrVH7VF71B4AuOurxvvlPJZYe/o/APyZM279Jfiq2mOUUWqP2qP2qD1qj9qj9qg9ANMeVmYTRy3lvaStvm+GjLv7JfgRN3OjjFJ71B61R+1Re9QetUftAZjm2nMstfbE//2k11Jrj5u5UUapPWqP2qP2qD1qj9qj9gBMde15Ne+Vo73aBb2srb9vXlJ7jDJK7VF71B61R+1Re9QetQeAwG/Qb3uLnI73zatqj1FGqT1qj9qj9qg9ao/ao/YAEPgN+r28f83VXu3+Kedoau1ZVnuMMkrtUXvUHrVH7VF71B61BwC1R+1xMzfKKLVH7VF71B61R+1Re9QeANQetcfN3Cijpqr2HCvnw7Ta82w5/2XVnvoBvlV71B61R+1Re9QeANQetccoo4yKrj31AxzOqj31Axxtik9U7TlSzl9qj9qj9qg9ao/aA4Dao/YYZZRR0bWn+31gG2tP+0CHcmpP+0CPN9UnpPbUD/Ro8xcH1B61R+1Re9QeANQetcfN3Cij1J7c2rO1URFXux0aVfVez6g9qx/4k6zaUz/wgtqj9qg9ag8Aao/a42ZulFFqj9pjlFGTH/NKOdcyak876lQ5t/PCStX7Su1RewBQe9QeN3OjjFJ71B6jjNolo17OG7X+I3Yjq2HU487mjQKAPUDt6X7fVHuMMmqqR6k9csG4R802/14pMhfMNeMic0F/3EE/0wEADP+IpPZ0vW+qPUYZNdWjImvPgWZIUO1px8034yJzwbzfLgAAYA9Re7rfN9Ueo/bkqMW8UfWw4behuJnTMNpxN7JGteP2zQAAANNF7el+M1d7jBrHsEt5owaJoB53M69h1OP8sw0AAICNbk1qT9dcoPZsNGohNazMDb0nRtwvh/THXcz85RAAAAB2FbVn86Oias/xzLBSjzubGVbqcWeEFQAAAPYmtWf0Uafzak89rP9XXK6k/sZKf9ynwgoAAABM8DYeWXsW82pPPWz4fWKX0z5q3icWAAAASK09h8u5lVd76nEnm3HLiZ/OE36NBgAAAKZb1Xs3r/bUw94s5++82tOO+z71U3qv5zUAAABMr6r3Umrt6f+Joq9Ta09/3DlPHwAAACBO1XuinOdSx71YzpHUcSc8fQAAAIA4Ve/BleITOu7J3HehqXqHPH0AAAAAAAAAALr5H72AWmG4R73sAAAAAElFTkSuQmCC);
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