<template>
  <div class="first">
    <div class="blok">
      <div>
        <p>Write your name</p>
        <input type="text" v-model="name" />
        <p>Write your surname</p>
        <input type="text" v-model="surname" />
        <p>Write your email</p>
        <input type="email" v-model="email" />

        <div class="buttons">
          <button @click="testFunc">Submit</button>
          <button @click="hide">Reset</button>
          <button @click="showHide">Show/hide</button>
          <button @click="pokreniGaleriju">Pokreni</button>
          <button @click="zaustaviGaleriju">Zaustavi</button>
        </div>
      </div>

      <div class="blok2" v-if="showData">
        <p>{{ name }}</p>
        <p>{{ surname }}</p>
        <p>{{ email }}</p>
        <p>{{ niz[brojSlike] }}</p>
      </div>
    </div>
    <ImageComponent></ImageComponent>
  </div>
</template>

<script>
// import slika from "../assets/hram.jpg";
import ImageComponent from "./imageComponent.vue";

export default {
  components: {
    ImageComponent: ImageComponent,
  },
  data() {
    return {
      email: "",
      surname: "",
      name: "",
      showData: false,
      niz: ["jedan", "dva", "tri", "cetiri", "pet"],
      brojSlike: 0,
      interval: null,
    };
  },
  methods: {
    testFunc() {
      if (this.name.length < 5 || this.name.length > 20) {
        this.showData = false;
        setTimeout(() => {
          alert("Hello Vue Simple Alert.");
        }, 100);
      } else this.showData = true;
    },
    hide() {
      this.name = "";
      this.surname = "";
      this.email = "";
    },
    showHide() {
      this.showData = !this.showData;
    },
    pokreniGaleriju() {
      this.interval = setInterval(() => {
        if (this.brojSlike < 4) {
          this.brojSlike += 1;
        } else {
          clearInterval(this.interval);
        }
      }, 3000);
    },
    zaustaviGaleriju() {
      clearInterval(this.interval);
    },
  },
};
</script>

<style>
.blok {
  width: 700px;
  border: 5px;
  border-color: rgb(0, 14, 72);
  color: red;
  background-color: rgb(147, 237, 237);
  display: flex;
}
.blok2 {
  width: 400px;
  background-color: rgb(112, 151, 222);
  border: 5px;
}
.buttons {
  display: block;
  padding-top: 10px;
}
.first {
  float: left;
}
</style>
