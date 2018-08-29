<template>
  <div id="example">
    <p>Original message: "{{ message }}"</p>
    <input placeholder="Enter your username" v-model="name"></input>
    <div id="databinding">
      <button v-on:click="show = !show">点我</button>
      <transition name="slide-fade">
        <p v-show="show" v-bind:style="styleobj">动画实例</p>
      </transition>
    </div>
    <p>Computed reversed message: "{{ reversedMessage }}"</p>
    <p>{{msg}}</p>
    <router-link to="/home">About</router-link>
    <button @click="change()">change</button>
    <h1 v-if="ok">Yes</h1>
    <h1 v-else>No</h1>
    <div v-if="Math.random() > 0.5">
      Now you see me
    </div>
    <div v-else>
      Now you don't
    </div>
    <input type="checkbox" id="checkbox" v-model="checked">
    <label for="checkbox">{{ checked }}</label>
    <template v-if="loginType === 'username'">
      <label>Username</label>
      <input placeholder="Enter your username">
    </template>
    <template v-else>
      <label>Email</label>
      <input placeholder="Enter your email address">
    </template>
    <button @click="type()">登录方式</button>
    <ul id="example-1">
      <li v-for="item in items">
        {{ item.message }}
      </li>
    </ul>
    <div v-for="(value, key) in student">
      {{ key }}: {{ value }}
    </div>
    <button v-on:click="counter += 1">Add 1</button>
    <p>The button above has been clicked {{ counter }} times.</p>
    <textarea v-model="lines" placeholder="add multiple lines"></textarea>
    <p>{{lines}}</p>

  </div>
</template>

<script>
export default {
  name: 'Example',
  data() {
    return{
      name:'',
      styleobj :{
            fontSize:'30px',
            color:'red'
        },
      checked:true,
      lines:"",
      message: 'Welcome to Your Vue.js App',
      msg:'a',
      counter:1,
      ok:false,
      show:true,
      loginType:"username",
      student:{
        name:"jack",
        age:18,
      },
      items: [
      { message: 'Foo' },
      { message: 'Bar' } ]
    }
  },
  computed: {
    // 计算属性的 getter
    reversedMessage: function () {
      // `this` 指向 vm 实例
      return this.message.split('').reverse().join('')
    }
  },
  watch:{
    name:function(newName,oldName){
      this.msg = newName;
    }
  },
  methods:{
    change:function(){
       warn('Hello ' + this.name + '!')
      this.msg = 'changed'+Date.now();
    },
    type:function(){
      if (this.loginType == 'username') {
        this.loginType = 'email'
      } else {
        this.loginType = 'username'  
      }
    }
  },
   created: function () {
    // `_.debounce` 是一个通过 Lodash 限制操作频率的函数。
    // 在这个例子中，我们希望限制访问 yesno.wtf/api 的频率
    // AJAX 请求直到用户输入完毕才会发出。想要了解更多关于
    // `_.debounce` 函数 (及其近亲 `_.throttle`) 的知识，
    // 请参考：https://lodash.com/docs#debounce
    this.msg = Date.now();
  },
 
}
</script>
<style>
/* 可以设置不同的进入和离开动画 */
/* 设置持续时间和动画函数 */
.slide-fade-enter-active {
  transition: all .3s ease;
}
.slide-fade-leave-active {
  transition: all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}
.slide-fade-enter, .slide-fade-leave-to
/* .slide-fade-leave-active 用于 2.1.8 以下版本 */ {
  transform: translateX(10px);
  opacity: 0;
}
#example {
    background-color: white;
}
</style>


