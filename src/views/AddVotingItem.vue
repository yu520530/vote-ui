<template>
  <div class="container">
    <div class="row">
      <div class="col-12 text-center">
        <h3 class="pt-3">新增</h3>
      </div>
    </div>
    <div class="row">
      <div class="col-5 mt-2"></div>
      <div class="col-2 mt-2">
        <form>
          <div class="form-group">
            <label class="text-black">投票項目名稱</label>
            <input type="text" class="form-control" v-model="name"/>
          </div>
          <button type="submit" class="btn btn-primary mt-3">送出</button>
        </form>
      </div>
      <div class="col-5 mt-2"></div>
    </div>

  </div>
</template>

<script>
  export default {
    data(){
      return{
        name:"",
      }
    },
  }
</script>

<style scoped>

</style>