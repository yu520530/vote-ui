<template>
  <div class="home container">
    <h1>參與投票</h1>
    <form>
      <div class="column">
        <label class="form-label" for="userName" >姓名</label>
        <input class="" id="userName" required v-model="name" />
      </div>
      <table class="table">
        <thead>
        <th>投票選取</th>
        <th>項目名稱</th>
        <th>累積票數</th>
        </thead>
        <tbody>
        <tr v-for="item in items" v-bind:key="item.id">
          <td>
<!--            <div class="form-check">-->
              <input class="form-check-input" type="checkbox" :value="item.id" :id="'check'+item.id" v-model="votes">
<!--            </div>-->
          </td>
          <td>{{ item.name }}</td>
          <td>{{item.records.length}}</td>
        </tr>
        </tbody>
      </table>
      <button type="button" class="btn btn-primary" @click="creteVotingItemAndRecords">送出投票</button>
    </form>
  </div>
</template>

<script>
import sweetalert from "sweetalert";

const axios = require("axios");

export default {
  data() {
    return {
      baseURL: "localhost:8080",
      items: [],
      votes:[],
      name:""
    };
  },
  methods:{
    getVotingItemsWithRecords() {
      return axios.get(this.baseURL + "/home/records").then((response) => {
        this.items = response.data;
      });
    },
    creteVotingItemAndRecords(){
      const newForm ={
        name: this.name,
        votes: this.votes
      };
      console.log(JSON.stringify(newForm))
      const baseURL= "localhost:8080";

      axios({
        method: 'post',
        url: `${baseURL}/home/records`,
        data: JSON.stringify(newForm),
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

    }
  },
  created() {
    this.getVotingItemsWithRecords()
  }
}
</script>
