<template lang='pug'>
  div
    h1 {{ msg }}
    .list-shopping
      .list-shopping__wrap
        .list-shopping__col
          item-list(
            v-for="item in list",
            v-if="!item.done",
            :itemInfo="item",
            @remove="list.splice(index, 1)",
            @edit="editItem(itemInfo.done)"
          )
        .list-shopping__col
          item-list(
            v-for="(item, index) in list",
            v-if="item.done",
            :itemInfo="item",
            @remove="list.splice(index, 1)"
          )

      .list-shopping__nav
        .list-shopping__col
          button(@click="clearList").btn clear all
          button(@click="allDone(list, true)").btn >
        .list-shopping__col
          button(@click="allDone(list, false)").btn <
          button(@click="removeDone").btn clear



</template>



<script>
  import itemList from './itemList'

export default {
  name: 'ListSopping',
  props: {
    msg: String
  },
  components: {
    'item-list': itemList
  },

  data() {
    return {
      list: [
        {
          id: '0',
          val: 'itam name-1',
          done: false,
          edit: false,
        },
        {
          id: '1',
          val: 'itam name-2',
          done: true,
          edit: false,
        },
        {
          id: '2',
          val: 'itam name-3',
          done: false,
          edit: false,
        },
        {
          id: '3',
          val: 'itam name-4',
          done: false,
          edit: false,
        },
        {
          id: '4',
          val: 'itam name-5',
          done: true,
          edit: false,
        },
        {
          id: '5',
          val: 'itam name-6',
          done: true,
          edit: false,
        },
        {
          id: '6',
          val: 'itam name-7',
          done: true,
          edit: false,
        }
      ]
    }
  },

  methods: {

    allDone: function (arrList, state) {
      arrList.forEach(function(itemList) {
        itemList.done = state
      });
    },

    removeDone: function () {

      this.list = this.list.filter(item => item.done == false)

    },

    clearList: function () {
      this.list = []
    },

    editItem: function (i) {
      // itemInfo.edit = !itemInfo.edit
      // list.splice(index, 1)
      console.log(i);
    }

  }


}

</script>



<style lang="scss">

  .list-shopping{
    margin: 40px auto;

    &__wrap{
      display: flex;
      border: 1px solid #ccc;
      min-height: 500px;
      background: #eee;
    }

    &__col{
      padding: 12px;
      width: 50%;
      &:first-of-type{
        border-right: 1px solid #ccc;
      }
    }

    &__nav{
      display: flex;
      border: 1px solid #ccc;
      border-top: none;
      background: #eee;
    }
  }

</style>
