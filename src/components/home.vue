<template>
    <div class="hello">
        <h1>{{ msg }}</h1>
        <h2>Ecosystem</h2>
        <ul>
            <li v-for="item in webs">
                <img v-bind:src="item.logo" width="60" height="60" />
                <a :href=item.url target="_blank"> {{item.name}}
                </a>
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
      webs:images
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
    margin: 0 10px;
}
a {
    color: #42b983;
}
img {
    height: 120;
    width: 120;
}
</style>
