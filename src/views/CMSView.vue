<template>
    <div class="container">
      <h1 class="text-center">投票項目</h1>
      <div class="d-flex flex-row m-3">
        <a href="/addVotingItem"> <button type="button" class="btn btn-primary">新增投票項目</button> </a>
      </div>

      <table class="table">
        <thead>
        <th>投票項目編號</th><th>投票項目名稱</th><th>操作</th>
        </thead>
        <tbody>
          <tr v-for="item in items" v-bind:key="item.id">
            <td>{{ item.id }}</td>
            <td>{{ item.name }}</td>
            <td><button type="button" class="btn btn-warning" @click="deleteItem(item)">delete</button></td>
          </tr>
        </tbody>
      </table>
    </div>
</template>
<script>
  const axios = require("axios");

  export default {
    data() {
      return {
        baseURL: "localhost:8080",
        items: []
      };
    },
    methods:{
      getVotingItems() {
        return axios.get(this.baseURL + "/cms/votingItems").then((response) => {
          this.items = response.data;
        });
      },
      async deleteItem(item){
        await axios.delete(`${this.baseURL}/cms/votingItems/${item.id}`)
      }
      // deleteItem(id){
      //   return axios.delete(this.baseURL+`/cms/votingItems/${id}`).then(()=>{
      //     console.log(`delete ${id}`)
      //   }).catch((err)=>console.log(err) )
      // }
    },
    created() {
      this.getVotingItems()
    }
  }
</script>