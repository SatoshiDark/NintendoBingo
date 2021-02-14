<template>
  <div class="nes-container">
    <div class="nes-container with-title is-centered">
      <p class="title ">Bingo Machine GO!</p>
      <button v-on:click="restart" type="button" class="nes-btn is-error">Restart</button>
      <button v-on:click="select" type="button" class="nes-btn is-success"><i class="nes-icon coin is-large"></i> Select</button>
    </div>
    <!-- <h1>{{ msg }}</h1> -->
    <!-- <h3>Bingo Machine GO!</h3> -->
    <!-- <button v-on:click="restart">Restart</button> -->
    <!-- <button v-on:click="select" style="width: 300px; height: 100px;">Select</button> -->

    <h3>Latest:</h3>
    <div v-if="latest === 'empty'"><i class="nes-mario"></i></div>
    <div v-else><img :alt="this.latest" :src="'./assets/' + this.latest + '.png'" style="width: 25%;"></div>

    <table class="nes-table is-bordered is-centered" style="width: 100%;">
      <tr>
        <th>B</th>
        <th>I</th>
        <th>N</th>
        <th>G</th>
        <th>O</th>
      </tr>
      <tr>
        <td>
          <li v-for="item in selected.b" :key="item">
            <img :alt="item" :src="'./assets/' + item + '.png'" style="width: 25%;">
            <!-- <img :alt="item" v-bind:src="`../assets/${item}.png`"> -->
          </li>
        </td>
        <td>
          <li v-for="item in selected.i" :key="item">
            <img :alt="item" :src="'./assets/' + item + '.png'" style="width: 25%;">
            <!-- <img :alt="item" v-bind:src="`../assets/${item}.png`"> -->
          </li>
        </td>
        <td>
          <li v-for="item in selected.n" :key="item">
            <img :alt="item" :src="'./assets/' + item + '.png'" style="width: 25%;">
            <!-- <img :alt="item" v-bind:src="`../assets/${item}.png`"> -->
          </li>
        </td>
        <td>
          <li v-for="item in selected.g" :key="item">
            <img :alt="item" :src="'./assets/' + item + '.png'" style="width: 25%;">
            <!-- <img :alt="item" v-bind:src="`../assets/${item}.png`"> -->
          </li>
        </td>
        <td>
          <li v-for="item in selected.o" :key="item">
            <img :alt="item" :src="'./assets/' + item + '.png'" style="width: 25%;">
            <!-- <img :alt="item" v-bind:src="`../assets/${item}.png`"> -->
          </li>
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data: function () {
    return {
      toSelect: [],
      selected: {
        b: [],
        i: [],
        n: [],
        g: [],
        o: []
      },
      latest: "empty"
    }
  },
  created() {
    console.log("Hello Bruno")
    this.restart()
  },
  methods: {
    restart: function () {
      this.toSelect = []
      "bingo".split('').forEach(letter => {
        for (let i = 1; i <= 16; i++) {
          this.toSelect.push(letter + i)
        }
      });
      this.selected.b = []
      this.selected.i = []
      this.selected.n = []
      this.selected.g = []
      this.selected.o = []
      this.latest = "empty"
      // alert('Hello ' + this.latest + '!')

    },
    select: function () {
      console.log("this is the error: " + this.toSelect.length)
      this.latest = this.toSelect[Math.floor(Math.random() * this.toSelect.length)];
      console.log(this.latest)
      switch(this.latest.charAt(0)) {
        case "b":
          this.selected.b.push(this.latest)
          break;
        case "i":
          this.selected.i.push(this.latest)
          break;
        case "n":
          this.selected.n.push(this.latest)
          break;
        case "g":
          this.selected.g.push(this.latest)
          break;
        case "o":
          this.selected.o.push(this.latest)
          break;
      }

      // alert('Selected ' + this.latest + '.png')
      var value=this.latest
      this.toSelect = this.toSelect.filter(function(item) {
          return item !== value
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
/* h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
} */
</style>
