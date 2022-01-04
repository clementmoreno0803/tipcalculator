<template>
  <div class="app_container">
    <svg xmlns="http://www.w3.org/2000/svg" width="87" height="54">
      <path
        fill="#3D6666"
        d="M6.72 17.472c.944 0 1.792-.12 2.544-.36s1.392-.584 1.92-1.032a4.476 4.476 0 001.212-1.62c.28-.632.42-1.34.42-2.124v-.288c0-1.472-.464-2.584-1.392-3.336-.928-.752-2.272-1.288-4.032-1.608a14.615 14.615 0 01-1.74-.408c-.456-.144-.824-.308-1.104-.492-.28-.184-.476-.392-.588-.624a1.771 1.771 0 01-.168-.78c0-.56.232-1.004.696-1.332.464-.328 1.096-.492 1.896-.492.944 0 1.676.248 2.196.744.52.496.78 1.08.78 1.752v.576h3.168v-.864a5 5 0 00-.396-1.968 4.762 4.762 0 00-1.176-1.656C10.436 1.08 9.792.7 9.024.42 8.256.14 7.376 0 6.384 0c-.88 0-1.676.12-2.388.36s-1.32.576-1.824 1.008c-.504.432-.896.94-1.176 1.524-.28.584-.42 1.22-.42 1.908v.144c0 .832.144 1.536.432 2.112a3.978 3.978 0 001.212 1.44c.52.384 1.132.692 1.836.924.704.232 1.48.42 2.328.564.64.112 1.168.248 1.584.408.416.16.744.34.984.54s.408.424.504.672c.096.248.144.508.144.78 0 .576-.232 1.072-.696 1.488-.464.416-1.176.624-2.136.624-1.232 0-2.14-.3-2.724-.9-.584-.6-.876-1.404-.876-2.412v-.576H0v.72c0 .88.144 1.692.432 2.436a5.47 5.47 0 001.272 1.944c.56.552 1.26.984 2.1 1.296.84.312 1.812.468 2.916.468zm22-.336V10.8h3.408c.864 0 1.616-.144 2.256-.432a4.707 4.707 0 001.596-1.14 4.833 4.833 0 00.96-1.608c.216-.6.324-1.212.324-1.836v-.576c0-.608-.108-1.204-.324-1.788a4.625 4.625 0 00-.96-1.56A4.737 4.737 0 0034.384.756c-.64-.28-1.392-.42-2.256-.42h-6.576v16.8h3.168zm3.096-9.36H28.72V3.36h3.096c.704 0 1.26.192 1.668.576.408.384.612.88.612 1.488v.288c0 .608-.204 1.104-.612 1.488-.408.384-.964.576-1.668.576zm29.464 9.36v-3.024h-7.632V.336H50.48v16.8h10.8zm24.88 0v-3.024h-4.032V3.36h4.032V.336H74.928V3.36h4.032v10.752h-4.032v3.024H86.16zm-78.096 36V39.36h4.464v-3.024H.432v3.024h4.464v13.776h3.168zm24.688 0V39.36h4.464v-3.024H25.12v3.024h4.464v13.776h3.168zm28.624 0v-3.024h-7.728v-3.888H60.8V43.2h-7.152v-3.84h7.44v-3.024H50.48v16.8h10.896zm16.744 0V46.8h3.648c.464 0 .796.12.996.36.2.24.3.552.3.936v5.04h3.168v-5.808c0-.56-.164-1.024-.492-1.392-.328-.368-.772-.584-1.332-.648v-.432c.768-.32 1.336-.78 1.704-1.38a3.63 3.63 0 00.552-1.932v-.576c0-.64-.116-1.24-.348-1.8a4.332 4.332 0 00-1.008-1.476c-.44-.424-.988-.756-1.644-.996-.656-.24-1.416-.36-2.28-.36h-6.432v16.8h3.168zm3.024-9.36H78.12V39.36h3.024c.768 0 1.352.204 1.752.612.4.408.6.892.6 1.452v.288c0 .656-.2 1.164-.6 1.524-.4.36-.984.54-1.752.54z"
      />
    </svg>
    <div class="calculator_container">
      <div class="left-part">
        <div class="input_calculator">
          <label for="bill">Bill</label>
          <div class="input_with_icon">
            <img src="./assets/icon-dollar.svg" alt="" />
            <input type="text" name="bill" v-model="bill" placeholder="0" />
          </div>
        </div>
        <div class="input_calculator">
          <label for="tip">Select Tip %</label>
          <div class="tips-amount">
            <tipsbuton @val="tipval"></tipsbuton>
            <input
              type="text"
              id="custometip"
              v-model="customtip"
              placeholder="Custom"
            />
          </div>
        </div>
        <div class="input_calculator">
          <label for="person">Number of People</label>
          <div class="input_with_icon">
            <img src="./assets/icon-person.svg" alt="" />
            <input type="text" name="person" v-model="person" placeholder="0" />
            <div v-if="person == '0'"></div>
          </div>
        </div>
      </div>
      <div class="tips_container">
        <div class="amount">
          <div class="tips_title">
            <h3>Tip Amount</h3>
            <span>/person</span>
          </div>
          <div>
            <h2 v-if="bill != 0 && person != 0 && customtip != ''">
              {{ tipscustom }}
            </h2>
            <h2 v-else-if="bill != 0 && person != 0">{{ tipsperperson }}</h2>
            <h2 v-else>$ 0,00</h2>
          </div>
        </div>
        <div class="amount">
          <div class="tips_title">
            <h3>Total</h3>
            <span>/person</span>
          </div>
          <div>
            <h2 v-if="bill != 0 && person != 0">{{ totaltips }}</h2>
            <h2 v-else>$ 0,00</h2>
          </div>
        </div>
        <div class="reset_btn" @click="bill = 0">
          <h3>{{ reset }}</h3>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import tipsbuton from "./components/tip.vue";
export default {
  name: "App",
  components: { tipsbuton },
  data() {
    return {
      bill: "",
      person: "",
      customtip: "",
      reset: "RESET",
    };
  },
  computed: {
    tipsperperson() {
      return (
        "$ " +
        (
          (parseInt(this.bill) * this.tipsamount - this.bill) /
          parseInt(this.person)
        ).toFixed(2)
      );
    },
    tipscustom() {
      return (
        "$" +
        (
          (("1" + parseInt(this.customtip) / 10) * parseInt(this.bill)) /
            10 /
            this.person -
          this.bill / this.person
        ).toFixed(2)
      );
    },
    totaltips() {
      if (this.customtip != "") {
        return (
          "$ " +
          (
            this.bill / this.person +
            ((("1" + parseInt(this.customtip) / 10) * parseInt(this.bill)) /
              10 /
              this.person -
              this.bill / this.person) /
              parseInt(this.person)
          ).toFixed(2)
        );
      } else {
        return (
          "$ " +
          (
            this.bill / this.person +
            (parseInt(this.bill) * this.tipsamount - this.bill) /
              parseInt(this.person)
          ).toFixed(2)
        );
      }
    },
  },
  methods: {
    tipval(payload) {
      this.tipsamount = payload.tipsamount;
      console.log(this.tipsamount);
    },
    resetAll() {
      return this.bill == 0;
    },
    alertZero() {
      alert("ceci ne peut pas être");
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@300;500;700&display=swap");

:root {
  --primary: #c5e4e8;
  --secondary: #fff;
  --thirdly: #0b676d;
  --forthly: #00474b;
  --fifty: #7ccccb;
}

body {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}
/* -------- FONT ------- */
h2 {
  color: var(--fifty);
  font-family: "Montserrat";
  font-weight: 500;
  font-size: 1.9rem;
}

h3 {
  color: var(--secondary);
  font-family: "Montserrat";
  font-weight: 500;
  font-size: 0.9rem;
  margin: 0;
}

span {
  color: var(--forthly);
  font-family: "Montserrat";
  font-weight: 400;
  font-size: 0.9rem;
}

label {
  color: var(--thirdly);
  font-family: "Montserrat";
  font-weight: 400;
  font-size: 0.9rem;
}
/* ------ GENERALE ------ */
.app_container {
  width: 100vw;
  height: 100vh;
  background: var(--primary);
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  flex-direction: column;
}

/* ----Left part ---- */
.calculator_container {
  width: 50%;
  height: 50%;
  background: var(--secondary);
  display: flex;
  padding: 20px;
  justify-content: space-between;
  align-items: center;
  border-radius: 8px;
}
.left-part {
  width: 45%;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  height: 100%;
}
.input_calculator {
  display: flex;
  flex-direction: column;
}
.input_with_icon img {
  position: absolute;
  z-index: 99;
  padding: 15px;
}
input {
  padding: 10px 15px;
  border: 1px solid grey;
  border-radius: 8px;
  text-align: right;
  font-family: "Montserrat";
  font-size: 1.2rem;
  color: var(--forthly);
  width: -webkit-fill-available;
}

/* .tip_button{
  width: calc( 95% / 3);
    background: var(--thirdly);
    margin: 2px;
    color: white;
    font-size: 1rem;
    font-family: 'Montserrat';
} */

input:focus {
  outline: none !important;
  border: 1px solid var(--fifty);
}
input.invalid {
  outline: none !important;
  border: 1px solid red;
}
button {
  width: calc(90% / 3);
  background: var(--thirdly);
  margin: 5px;
  font-family: "Montserrat";
  font-size: 1rem;
  height: 30px;
  border: none;
  color: var(--secondary);
  border-radius: 5px;
}
#custometip {
  position: relative;
  width: calc(63% / 3);
  height: 9px;
  text-align: center;
  left: 5px;
  top: 2px;
}
/* ----Right part---- */
.tips_container {
  background: var(--thirdly);
  height: 100%;
  width: 45%;
  border-radius: 8px;
  padding: 0 20px;
  position: relative;
}
.amount {
  display: flex;
  margin: 5%;
  justify-content: space-between;
  align-items: center;
  margin: 5%;
}
.reset_btn {
  position: absolute;
  bottom: 20px;
  width: calc(100% - 70px);
  background: var(--forthly);
  padding: 15px;
  display: flex;
  border-radius: 8px;
  justify-content: center;
  align-items: center;
}
.reset_btn:hover {
  background: var(--fifty);
  transition: all 0.2s ease-in-out;
}
</style>
