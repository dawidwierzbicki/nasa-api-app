<template>
    <div :style="style" class="item" />
</template>
<script>
export default {
    name: 'Item',
    props: {
        item: {
            type: Object,
            required: true,
        },
    },
    data() {
        return {
            photo: this.item.links[0].href,
            title: this.item.data[0].title,
        };
    },
    computed: {
        style() {
            return `background-image: url("${this.photo}")`;
        },
    },
};
</script>
<style scoped>
  .item {
    width: 40vw;
    height: 150px;
    background-size: cover;
    background-repeat: no-repeat;
    background-position: 50%;
    box-shadow: 0px 0px 10px 1px #fff;
    margin-bottom: 30px;
  }
  @media (min-width: 768px) {
    .item {
      width: 25vw;
      height: 250px;
    }
  }
</style>
