<template>
  <div>
    <table id="calculator" dir="ltr" style="text-align: center; margin: auto">
      <tr>
        <!-- table row -->
        <td colspan="5">
          <!-- span = امتداد داشتن -->
          <input
            v-model="screen"
            dir="ltr"
            id="result"
            type="number"
            style="padding: 5px; font-weight: bold; text-align: right"
          />
        </td>
        <!-- table data -->
      </tr>
      <tr>
        <td><button @click="digit(7)" class="digit">7</button></td>
        <td><button @click="digit(8)" class="digit">8</button></td>
        <td><button @click="digit(9)" class="digit">9</button></td>
        <td><button @click="div" id="div">/</button></td>
        <td><button @click="clear" id="clear">C</button></td>
      </tr>
      <tr>
        <td><button @click="digit(4)" class="digit">4</button></td>
        <td><button @click="digit(5)" class="digit">5</button></td>
        <td><button @click="digit(6)" class="digit">6</button></td>
        <td><button @click="mul" id="mul">*</button></td>
        <td><button @click="remove" id="remove">del</button></td>
      </tr>
      <tr>
        <td><button @click="digit(1)" class="digit">1</button></td>
        <td><button @click="digit(2)" class="digit">2</button></td>
        <td><button @click="digit(3)" class="digit">3</button></td>
        <td><button @click="minus" id="minus">-</button></td>
        <td><button @click="mod" id="mod">%</button></td>
      </tr>
      <tr>
        <td colspan="2"><button @click="digit(0)" class="digit">0</button></td>
        <td><button class="digit">.</button></td>
        <td><button @click="sum" id="sum">+</button></td>
        <td><button @click="equal" id="equal">=</button></td>
      </tr>
    </table>
  </div>
</template> 

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      screen: "",
      value1: Number,
      value2: Number,
      op: "",
    };
  },
  methods: {
    digit(n) {
      this.screen += n;
    },
    sum() {
      this.value1 = parseInt(this.screen, 10);
      this.op = "+";
      this.screen = "";
    },
    mul() {
      this.value1 = parseInt(this.screen, 10);
      this.op = "";
      this.screen = "";
    },
    minus() {
      this.value1 = parseInt(this.screen, 10);
      this.op = "-";
      this.screen = "";
    },
    mod() {
      this.value1 = parseInt(this.screen, 10);
      this.op = "%";
      this.screen = "";
    },
    clear() {
      this.screen = "";
    },
    remove() {
      this.screen = "";
    },
    div() {
      this.value1 = parseInt(this.screen, 10);
      this.op = "/";
      this.screen = "";
    },
    equal() {
      switch (this.op) {
        case "+":
          this.value2 = parseInt(this.screen, 10);
          this.screen = this.value2 + this.value1;
          break;
        case "-":
          this.value2 = parseInt(this.screen, 10);
          this.screen = this.value1 - this.value2;
          break;
        case "":
          this.value2 = parseInt(this.screen, 10);
          this.screen = this.value1 * this.value2;
          break;
        case "%":
          this.value2 = parseInt(this.screen, 10);
          this.screen = this.value1 % this.value2;
          break;
        case "/":
          this.value2 = parseInt(this.screen, 10);
          this.screen = this.value1 / this.value2;
          break;
        default:
          break;
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.digit {
  border: 1px solid black;
}
button {
  width: 100%;
}
</style>