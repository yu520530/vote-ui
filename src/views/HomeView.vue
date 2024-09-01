<template>
  <div class="home container">
    <h1>參與投票</h1>
    <form>
      <div class="column">
        <label class="form-label" for="userName">姓名</label>
        <input class="" id="userName"/>
      </div>
      <table class="table">
        <thead>
        <th>投票選取</th>
        <th>項目名稱</th>
        <th>累積票數</th>
        </thead>
        <tbody>
        <td>
          <div class="form-check">
            <input class="form-check-input" type="checkbox" value="" id="flexCheckDefault">
          </div>
        </td>
        <td>A</td>
        <td>5</td>
        </tbody>
      </table>
      <button type="submit" class="btn btn-primary">送出投票</button>
    </form>
  </div>
</template>

<script>

export default {
  name: 'HomeView',
  components: {}
}
</script>
