<template>
  <div id="app">
    <img :src="link"/>
    <p v-text="hello"></p>
    <p v-html="hello"></p>
    {{num+1}}
    {{status?'sucsess':'error'}}
    <ul>
      <li v-for="(item,index) in list" v-text="item.name+index"></li>
    </ul>
       <ul v-for="item in list">
      <li>{{item.name}}</li>
    </ul>
    <ul>
      <li v-for="(value,key) in objList" v-text="key + value"></li>
    </ul>
    <componenA :msg="msg" v-for="item in objList"></componenA>
    <button v-on:click="addSet">我是按钮</button>
  </div>
</template>

<script>
  import componenA from './components/HelloWorld';
  import Vue from 'vue';

  export default {
    components: {componenA},
    data() {
      return {
        hello: '<p><img src="">hello</p>',
        num: 1,
        status: true,
        link: 'http://gb.cri.cn/mmsource/images/2007/06/21/bc070621072.jpg',
        msg: '我是APP的msg',
        list: [
          {name: 'name1'},
          {name: 'name2'},
          {name: 'name3'},
        ],
        objList: {
          name: 'objname',
          age: 125,
          adress: 'north of china'
        }
      }
    },
    methods: {
      add() {
        this.list.push({name: 'name4'});
        console.info(this.list);
      },
      addSet() {
        Vue.set(this.list, 1, {name: 'changed'});
      }
    }
  }
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
