<template lang='pug'>

  .list-item
    button.btn(v-if="itemInfo.done", @click="moveInCompleted(itemInfo)") ◄
    button.btn(v-if="!itemInfo.done", @click="$emit('remove')") Х
    button.btn(v-if="!itemInfo.done", @click="$emit('edit')")
      span.btn__ok(v-if="itemInfo.edit") ✔
      span.btn__edit(v-if="!itemInfo.edit") i
    .list-item__val(v-if="itemInfo.done")
      p {{ itemInfo.val }}
    .list-item__val(v-else)
      p(v-if="!itemInfo.edit") {{ itemInfo.val }}
      input.list-item__input(v-else, v-model="itemInfo.val")

    button.btn(v-if="itemInfo.done", @click="$emit('remove')") Х
    button.btn(v-if="!itemInfo.done", @click="moveInCompleted(itemInfo), itemInfo.edit = false") ►

</template>



<script>

export default {
  name: 'ItemList',
  props: ['itemInfo'],

  methods: {

    moveInCompleted: function (itemInfo) {
      itemInfo.done = !itemInfo.done
    },

  }
}

</script>



<style lang="scss">

  .list-item{
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 12px 12px;
    border-bottom: 1px solid #ddd;
    &:first-of-type{
      border-top: 1px solid #ddd;
    }

    &__val{
      width: 100%;
      font-size: 16px;
      line-height: 1;
      letter-spacing: 0;
      color: #444;
      padding: 0 12px;
    }
    &__input{
      width: 100%;
      color: #111;
      border: none;
      background: none;
      text-align: center;
      background: #f6f6f6;
      height: 24px;
      font-size: 16px;
      line-height: 1;
      letter-spacing: 0;
      text-indent: 0;
    }
  }

</style>
