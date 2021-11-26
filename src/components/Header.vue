<template>
  <div class="header">
    <span>logo</span>
  </div>
</template>

<script>


export default {
  name:'Header'
}
</script>

<style lang="scss" scoped>
  .header{
    background-color:#62646B ;
    width: 100%;
    height: 40px;
    span{
      line-height: 40px;
      text-transform: uppercase;
      color: white;
      margin-left: 20px
    };
  };
</style>