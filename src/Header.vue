<template>
  <div class="sc-header" :style="{background: colors.header.bg, color: colors.header.text}">
    <img class="sc-header--img" :src="imageUrl" alt="" v-if="imageUrl" />
    <div class="sc-header--title"> {{title}} </div>
  </div>
</template>
<script>

export default {
  props: {
    imageUrl: {
      type: String,
      required: true
    },
    title: {
      type: String
    },
    colors: {
      type: Object,
      required: true
    }
  },
  methods: {
  },
  data() {
    return {
      inUserList: false
    }
  }
}
</script>
<style scoped>
.sc-header {
  min-height: 75px;
  position: relative;
  box-sizing: border-box;
  display: flex;
  border-radius: 4px;
}

.sc-header--img {
  border-radius: 50%;
  align-self: center;
  padding: 10px;
}

.sc-header--title {
  align-self: center;
  padding: 10px;
  flex: 1;
  user-select: none;
  cursor: pointer;
  border-radius: 5px;
}
</style>
