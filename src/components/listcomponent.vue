<template>
  <ListComp>
    <div v-bind:class="style_coler">
      <li>
        {{ id_props }} - {{ name_props }} - {{ mail_props }} -
        {{ tell_props }} - {{ address_props }} -
        {{ time_props }}
      </li>
      <a v-on:click="testfnc">{{ flg }}</a>
    </div>
  </ListComp>
</template>


<script>
// エクスポートすることで<template>のタグ構造が使用できる
export default {
  name: "list_test",
  props: {
    id_props: String,
    name_props: String,
    mail_props: String,
    address_props: String,
    tell_props: String,
    time_props: String,
  },
  // data関数内で変数（State?）宣言
  data() {
    return {
      flg: false,
      style_coler: "no-mk",
    };
  },
  methods: {
    testfnc: function () {
      var tmp = this.flg;
      var c = this.style_coler;
      this.flg = !tmp;

      if (this.flg) {
        this.style_coler = "mk";
      } else {
        this.style_coler = "no-mk";
      }

      console.log("flg" + ":" + tmp + " => " + !tmp);
      console.log("style" + ":" + c + " => " + this.style_coler);
    },
    testfnc2: function () {},
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
<style >
.mk {
  background-color: red;
}

div {
  background-color: "red";
}
</style>>