<template>
  <Comandoo>
    <div>
      <a>{{ sbtitle }}{{ test_props }}</a>
      <p>Comand!!!</p>
      <button v-on:click="testfnc">testfnc</button>
      <p v-on:click="testfnc2">return</p>
      <li v-for="loops in arr" :key="loops.name">{{ loops.name }}</li>
      <button v-on:click="fetchfnc">fetch</button>
      <div>
        <!-- <li v-for="j_loop in json_arr" :key="j_loop.id">
        {{ j_loop.id }} - {{ j_loop.name }} - {{ j_loop.mail }} -
        {{ j_loop.tell }} - {{ j_loop.address }}
      </li> -->
        <div v-for="j_loop in json_arr" :key="j_loop.id">
          <li class="{{j_loop.id}}">
            {{ j_loop.id }} - {{ j_loop.name }} - {{ j_loop.mail }} -
            {{ j_loop.tell }} - {{ j_loop.address }}
            <button v-on:click="funconClick" v-bind:class="json_arr[0]['id']">
              XXX
            </button>
            <ListComponents
              :id_props="j_loop.name"
              :name_props="j_loop.name"
              :mail_props="j_loop.mail"
              :tell_props="j_loop.tell"
              :address_props="j_loop.adress"
              :time_props="j_loop.ordertime"
            ></ListComponents>
          </li>
        </div>
      </div>
    </div>
  </Comandoo>
</template>


<script>
import ListC from "./listcomponent.vue";

// エクスポートすることで<template>のタグ構造が使用できる
export default {
  name: "test",
  props: {
    test_props: String,
  },
  components: {
    ListComponents: ListC,
  },
  // data関数内で変数（State?）宣言
  data() {
    return {
      sbtitle: "The SunDay Movie Time...",
      arr: [{ name: "a" }, { name: "b" }, { name: "c" }],
      json_arr: {},
    };
  },
  methods: {
    testfnc: function () {
      this.sbtitle = "!!!!";
      console.log("!!!!!");
    },
    testfnc2: function () {
      this.sbtitle = "The SunDay Movie Time...";
      this.arr = [
        { name: "Nichiyou" },
        { name: "Youga" },
        { name: "Gekijouo!" },
      ];
    },
    fetchfnc: function () {
      fetch("http://localhost:4000/showorder")
        .then((response) => {
          var t = response.json();
          console.log(t);
          return t;
        })
        .then((data) => {
          var r = data;
          console.log(r);
          this.json_arr = r;
        });
    },
    funconClick: function (event) {
      console.log(event.target);
    },
  },
};
</script>>