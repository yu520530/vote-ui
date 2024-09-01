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
          <button type="button" class="btn btn-primary mt-3" @click="addVotingItem">送出</button>
        </form>
      </div>
      <div class="col-5 mt-2"></div>
    </div>

  </div>
</template>

<script>
  const axios = require("axios");
  const sweetalert = require("sweetalert")

  export default {
    data(){
      return{
        name:"",
      }
    },
    methods:{
      addVotingItem(){
        console.log(this.name);
        const newVotingItem ={
          name: this.name,
        };

        const baseURL = "https://9264-2001-b400-e7af-60b2-c48c-4bbe-1f0a-5c.ngrok-free.app";

        axios({
          method: 'post',
          url: `${baseURL}/cms/votingItems`,
          data: JSON.stringify(newVotingItem),
          headers: {
            'Content-Type': 'application/json'
          }
        })
        .then(() => {
          console.log('success')
          sweetalert({
            text: 'send success',
            icon: 'success',
          })
        })
        .catch((err) => {
          console.log(err);
        });
      },
    },
  }
</script>

<style scoped>

</style>