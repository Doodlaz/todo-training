<template lang='pug'>
  #app
    .header
      img(alt="Vue logo" src="./assets/logo.png").header__logo
    main.main
      section
        .container
          list-sopping(msg="List name")
  </div>
</template>

<script>
import listSopping from './components/listSopping'

export default {
  name: 'app',
  components: {
    'list-sopping': listSopping,
  },
}
</script>

<style lang="scss">

  p{
    margin: 0;
  }
  input{
    outline: none;
  }

  .btn{
    cursor: pointer;
    background: #eee;
    border: 1px solid #ddd;
    color: #999;
    min-width: 26px;
    height: 26px;
    margin: 0 2px;
    transition: .2s;
    outline: none;

    &:hover{
      color: #444;
      border-color: #999;
    }

    &__edit{
      font-size: 16px;
      transform: rotate(35deg);
      display: block;
      font-weight: 600;
      margin-bottom: -3px;
    }
    &__ok{
      color: green;
    }
  }

  #app{
    font-family: Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #000d30;
    margin-top: 60px;
  }

  .header {
   position: fixed;
    top: 0;
    left: 0;
    right: 0;
    height: 60px;
    background: #f0f0f0;
    &__logo{
      position: absolute;
      left: 40px;
      top: 0;
      bottom: 0;
      max-height: 40px;
      margin: auto;
    }
  }

  .main{
    margin-top: 60px;
  }

  .container{
    max-width: 1200px;
    padding: 20px 0;
    margin: 0 auto;
  }

</style>
