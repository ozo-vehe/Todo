<template>
  <div class="headerComponent-container">
    <div class="todo-title">
      <h2 class="header-title">Hello {{ name }} <br> welcome back</h2>
      <p class="curr-date">{{ currentDate }}</p>
    </div>

    <div class="todo-sum">
      <div class="personal">
        <h2 class="personal-count">{{ personalCount }}</h2>
        <p>personal</p>
      </div>

      <div class="business">
        <h2 class="business-count">{{ businessCount }}</h2>
        <p>business</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HeaderComponent',
  props: [ 'name' ],
  data() {
    return {
      businessCount: 0,
      personalCount: 0,
      currentDate: null,
      months: [
        'jan',
        'feb',
        'mar',
        'apr',
        'may',
        'jun',
        'jul',
        'aug',
        'sep',
        'oct',
        'nov',
        'dec'
      ]
    }
  },
  methods: {
    changeNumber() {
      this.personalCount = 20
    },
    getDate () {
      let newCurrentDate = new Date
      let month = newCurrentDate.getMonth()
      let date = newCurrentDate.getDate()
      let year = newCurrentDate.getFullYear()

      this.currentDate = `${this.months[month]} ${date}, ${year}`
    }
  },
  mounted () {
    this.getDate()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .headerComponent-container {
    color: #ffffff;
    background-image: url('../assets/bg.jpg');
    background-position: center;
    background-size: cover;
    width: 100%;
    height: 100vh;
    display: flex;
    justify-content: space-between;
  }
  .headerComponent-container .todo-title {
    width: 65%;
    padding: 10%;
    box-sizing: border-box;
    display: flex;
    align-items: flex-start;
    justify-content: center;
    flex-direction: column;
  }
  .todo-title h2 {
    font-size: 4.1rem;
    line-height: 1.5;
    font-weight: 600;
    text-transform: capitalize;
  }
  .todo-title p {
    font-size: 1.5rem;
    text-transform: capitalize;
  }

  .headerComponent-container .todo-sum {
    box-sizing: border-box;
    width: 35%;
    display: flex;
    align-items: center;
    justify-content: space-between;
    background-color: #00000060;
  }
  .todo-sum div {
    width: 50%;
    text-transform: capitalize;
    text-align: center;
  }
  .todo-sum div h2 {
    font-size: 3rem;
    margin: 0px;
  }
  .todo-sum div p {
    margin: 5px;
  }
</style>
