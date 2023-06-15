<template>
  <div class="captcha-box">
    <div class="head-box">
      <p style="font-size: 12px;">选择包含</p>
      <p><strong style="font-size: 28px;">{{ character }}</strong></p>
      <p style="font-size: 12px;">的所有图片。</p><img src="/assets/icon/KiraCaptcha.svg" class="cover">
    </div>
    <div class="images-box">
      <div class="image-item" v-for="image in images" :key="image.id" @click="toggleSelected(image)"
        :data-selected="isSelected(image)">
        <i :style="{ backgroundImage: `url(${image.url})` }"></i>
      </div>
      <div class="ct-warning">{{ warningText }}</div>
    </div>
    <div class="ctrl-box">

      <div class="left-box">
        <button @click="loadRandomData()" class="reset icon">
          <svg viewBox="0 0 24 24">
            <path
              d="M21,3v7h-7l2.9-2.9C15.7,5.8,13.9,5,12,5c-3.9,0-7,3.1-7,7s3.1,7,7,7c3.2,0,5.9-2.2,6.8-5.2l2,0.4 c-1,3.9-4.5,6.7-8.7,6.7c-5,0-9-4-9-9s4-9,9-9c2.5,0,4.7,1,6.4,2.6L21,3z">
            </path>
          </svg>
        </button>
        <button @click="$emit('close')" class="reset icon">
          <svg viewBox="0 0 24 24">
            <path
              d="M19 6.41 17.59 5 12 10.59 6.41 5 5 6.41 10.59 12 5 17.59 6.41 19 12 13.41 17.59 19 19 17.59 13.41 12z">
            </path>
          </svg>
        </button>
      </div>
      <button class="blue" @click="checkAnswer">验证</button>
    </div><!---->
  </div>
</template>

<script>
export default {
  props:['jsonFileCountProps','jsonBaseUrlProps'],
  data () {
    return {
      character: null,
      images: [],
      correctImageIds: [],
      warningText: "",
      jsonBaseUrl: this.jsonBaseUrlProps,
      jsonFileCount: this.jsonFileCountProps,
      lastRandomIndex: 0,
    }
  },
  mounted () {
    this.loadRandomData();
  },
  methods: {
    loadRandomData () {
      let randomIndex = this.lastRandomIndex; // Start with the last random index
      while (randomIndex === this.lastRandomIndex) {
        randomIndex = Math.floor(Math.random() * this.jsonFileCount) + 1;
      }
      this.lastRandomIndex = randomIndex; // Store the current random index
      const jsonUrl = `${this.jsonBaseUrl}${randomIndex}.json`;
      fetch(jsonUrl)
        .then(response => response.json())
        .then(data => {
          this.character = data.character;
          this.images = data.images;
          this.correctImageIds = data.correctImageIds;
          this.resetSelections();
        })
        .catch(error => {
          console.error('Error fetching data:', error);
        });
    },
    resetSelections () {
      this.images.forEach(image => image.selected = false);
    },
    toggleSelected (image) {
      const index = this.getImageIndex(image);
      this.images[index].selected = !this.images[index].selected;
    },
    isSelected (image) {
      return this.images[this.getImageIndex(image)].selected;
    },
    getImageIndex (image) {
      return this.images.findIndex(item => item.id === image.id);
    },
    checkAnswer () {
      const selectedCount = this.images.filter(image => image.selected).length;
      const warning = document.querySelector('.ct-warning');
      //判断错误图片选择情况
      const incorrectSelectedCount = this.images.filter(image => image.selected && !this.correctImageIds.includes(image.id)).length;
      //判断正确图片选择情况
      const correctSelectedCount = this.images.filter(image => image.selected && this.correctImageIds.includes(image.id)).length;
      if (incorrectSelectedCount > 1) {
        // 用户选择了多于2张其他不是正确答案的图片
        warning.style.display = 'block';
        this.warningText = "请重试。";
        this.loadRandomData();
        return;
      } else if (correctSelectedCount > 0 && incorrectSelectedCount > 0) {
        warning.style.display = 'block';
        this.warningText = "请重试。";
        this.loadRandomData();
        return;
      } else if (incorrectSelectedCount > 0) {
        // 用户选择了少于或等于2张其他不是正确答案的图片
        warning.style.display = 'block';
        this.warningText = "请选择所有相符的图片。";
        return;
      }

      if (selectedCount === 0) {
        // 用户没有选择任何图片
        warning.style.display = 'block';
        this.warningText = "请选择所有相符的图片。";
        return;
      } else {
        // 用户选择了图片
        warning.style.display = 'none';
      }

      if (correctSelectedCount !== this.correctImageIds.length) {
        // 用户只选择了正确图片的一部分
        warning.style.display = 'block';
        this.warningText = "请选择所有相符的图片。";
        return;
      }

      const selectedIds = this.images.filter(image => image.selected).map(image => image.id);
      const isSubset = this.correctImageIds.every(id => selectedIds.includes(id));
      const isSuperset = selectedIds.every(id => this.images.some(image => image.id === id)) && !this.correctImageIds.some(id => !selectedIds.includes(id));
      if (!isSubset) {
        // 用户选择的图片不包含正确的图片
        warning.style.display = 'block';
        this.warningText = "答案错误。";
      } else if (!isSuperset) {
        // 用户选择的图片包含正确的图片，但是还包含其他不属于正确图片的图片
        warning.style.display = 'block';
        this.warningText = "请重试。";
        this.loadRandomData();
      } else {
        // 用户选择的图片与正确图片完全匹配
        console.log('答案正确');
        this.$emit('update:ispass', true);

      }
    }
  }
}
</script>
<style>
.ct-warning {
  color: #d14836;
  font-size: 14px;
  padding: 7px 0;
  text-align: center;
  width: 100%;
  background-color: white;
  display: none;
}
</style>