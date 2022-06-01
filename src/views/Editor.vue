<template>
  <div class="login-container">
    <div class="side-block">
      <div class="header">
        <h1>Mannr</h1>
      </div>
      <b-form-file
        v-model="file"
        :state="Boolean(file)"
        placeholder="Choose a file or drop it here..."
        @change="onChange($event)"
      ></b-form-file>
      <canvas id="c"></canvas>
    </div>
  </div>
</template>

<script>
// import router from "../router";
export default {
  name: "EditorView",
  data() {
    return {
      file: null,
      vueCanvas: null,
    };
  },
  mounted() {
    var c = document.getElementById("c");
    var ctx = c.getContext("2d");
    console.log(ctx);
    this.vueCanvas = ctx;
  },
  methods: {
    onChange(event) {
      var refer = this;
      let _URL = window.URL || window.webkitURL;
      let imageInput = event.target.files[0];
      let img = new Image();
      //drawing of the test image - img1
      img.onload = function () {
        //draw background image
        refer.vueCanvas.drawImage(img, 0, 0);
        //draw a box over the top
        // ctx.fillStyle = "rgba(200, 0, 0, 0.5)";
        // ctx.fillRect(0, 0, 500, 500);
      };
      img.src = _URL.createObjectURL(imageInput);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
