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
    </div>
    <div class="ctrl-box">
      <div class="left-box">
        <button class="reset icon">
          <svg viewBox="0 0 24 24">
            <path d="M21,3v7h-7l2.9-2.9C15.7,5.8,13.9,5,12,5c-3.9,0-7,3.1-7,7s3.1,7,7,7c3.2,0,5.9-2.2,6.8-5.2l2,0.4
                  c-1,3.9-4.5,6.7-8.7,6.7c-5,0-9-4-9-9s4-9,9-9c2.5,0,4.7,1,6.4,2.6L21,3z">
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
  data () {
    return {
      character: "天天座理世",
      images: [
        { id: 1, url: '/assets/test/1.jpg', selected: false, selected: false },
        { id: 2, url: '/assets/test/2.jpg', selected: false, selected: false },
        { id: 3, url: '/assets/test/3.jpg', selected: false, selected: false },
        { id: 4, url: '/assets/test/4.jpg', selected: false, selected: false },
        { id: 5, url: '/assets/test/5.jpg', selected: false, selected: false },
        { id: 6, url: '/assets/test/6.jpg', selected: false, selected: false },
        { id: 7, url: '/assets/test/7.jpg', selected: false, selected: false },
        { id: 8, url: '/assets/test/8.jpg', selected: false, selected: false },
        { id: 9, url: '/assets/test/9.jpg', selected: false, selected: false }
      ],
      correctImageIds: [1, 7],
    }
  },
  methods: {
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
      if (selectedCount === this.correctImageIds.length) {
        // 用户选择的图片数量与正确图片数量相等
        console.log('答案正确');
      } else {
        // 用户选择的图片数量与正确图片数量不相等
        console.log('答案错误');
      }
    }
  }
}
</script>