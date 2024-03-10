<template>
  <div class="container">
    <div class="box">
      <div class="form-floating mb-3">
        <input
        type="url"
        class="form-control mt-5"
        id="form"
        placeholder="url ... "
        :value="url"
        @input="url = $event.target.value"
        />
        <label for="form">
          URL
        </label>
        <button class="btn btn-primary center" @click="viewImage">
          View Image
        </button>
      </div>
    </div>
    <div class="img" v-for="url in urlDb" v-bind:key="Date.now()">
      <img :src="url.url" alt="image not found"/>
    </div>
  </div>
</template>
<script>
export default {
  data(){
    return{
      url:"",
      urlDb:[]
    }
  },
  methods:{
    viewImage(){
      const newUrl = {
        url: this.url
      }
      this.urlDb.pop()
      this.urlDb.push(newUrl)
      this.url = ""
    }
  }
}
</script>
<style>
.center {
  display: inline-block;
  width: 30%;
  margin-top: 0;
  margin-left: 35%;
  margin-right: 35%;
}
.box {
  width: 100%;
  height: 30vh;
  border-radius: 10px;
  border: 1px solid white;
  margin-top: 5vh;
}
[alt]{
  color:white;
  font-size: 2em;
}
img {
  width: 100%;
  height: auto;
}
</style>