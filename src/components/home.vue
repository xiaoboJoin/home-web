<template>
    <div class="hello">
        <h1>{{ msg }}</h1>
        <h2>Ecosystem</h2>
        <ul>
            <li v-for="item in webs">
                <div class="item" @click="tap(item)">
                    <img v-bind:src="item.logo" width="80" height="80" />
                    <a class="name" :href=item.url> {{item.name}}</a>
                </div>

            </li>
        </ul>
        <a href="">Vue</a>
    </div>
</template>
<script>
import images from './data.json'
export default {
  name: 'Home',
  data () {
    return {
      msg: '首页',
      webs:require("./data.json")
    }
  },
  methods:{
      tap:function(item){
        //    window.location.href = item.url;
        window.open(item.url)

      }

  }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
    font-weight: normal;
}
ul {
    list-style-type: none;
    padding: 0;
}
li {
    flex-direction: column;
    display: inline-block;
    margin: 40px 40px;
}
a {
    color: #666666;
    font-size: 24pt;
    font-weight: bold;
}
img {
    height: 240;
    width: 240;
    border-radius: 80px;
}
.item {
    display: flex;
    flex-direction: column;
    align-items: center;
}

.name {
    font-size: 24px;
    text-decoration: none;
}
</style>
