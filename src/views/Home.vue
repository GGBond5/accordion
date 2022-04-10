<template>
  <div class="home">
    <div class="navLeft" v-for="(item, index) in nav" :key="index" >
      <p :class="{Action: isAction == index}" @click="changeAction(index)">
        {{item.value}}
      </p>
      <ul ref="ulHeight">
        <li v-for="(v, i) in item.children" :key="i">{{v.value}}</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      nav: [
        {index: 0, value: "测试一", children: [
          {index: 0, value: "测试1-1"},
          {index: 1, value: "测试1-2"},
          {index: 2, value: "测试1-3"},
          {index: 3, value: "测试1-4"},
          {index: 4, value: "测试1-5"},
        ]},
        {index: 1, value: "测试二", children: [
          {index: 0, value: "测试222"},
          {index: 1, value: "测试222"},
          {index: 2, value: "测试222"},
          {index: 3, value: "测试222"},
          {index: 4, value: "测试222"},
        ]},
        {index: 1, value: "测试三", children: [
          {index: 0, value: "测试333"},
          {index: 1, value: "测试333"},
          {index: 2, value: "测试333"},
          {index: 3, value: "测试333"},
          {index: 4, value: "测试333"},
        ]},
        {index: 1, value: "测试四", children: [
          {index: 0, value: "测试444"},
          {index: 1, value: "测试444"},
          {index: 2, value: "测试444"},
          {index: 3, value: "测试444"},
          {index: 4, value: "测试444"},
        ]},
      ],
      isAction: -1,
    }
  },
  mounted () {
  },
  methods: {
    changeAction (index) {
      this.isAction = index
      //所有ul高度置0
      let uls = [...this.$refs.ulHeight]
      uls.map((val) => {
        val.style.height = '0px'
      })
      //指定的ul长高
      let h = this.$refs.ulHeight[index].children.length
      this.$refs.ulHeight[index].style.height = h * 60 + 'px'
    }
  }
}
</script>

<style lang="less" scoped>
.home {
  width: 200px;
  height: 100vh;
  background-color: pink;
  .navLeft {
    overflow: hidden;
    p {
      position: relative;
      z-index: 2;
      height: 60px;
      line-height: 60px;
      background-color: aquamarine;
      cursor: pointer;
    }
    ul li {
      height: 60px;
      line-height: 60px;
      background-color: #fff;
    }
    ul {
      height: 0px;
      transition: all 1s;
    }
  }
}
.Action {
  background-color: burlywood !important;
}
</style>