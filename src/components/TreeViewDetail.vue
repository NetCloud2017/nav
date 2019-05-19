<template>
  <div>
    <h3>这里是{{currentRoute}}导航详情</h3>
    <ol>
      <li v-for="(item, index) in refsDatas" :key="index">
        <div @click="getRefs">{{item.name}}</div>
        <ul ref="subname">
          <li v-for="(ele, index) in item.nameList" :key="index">
            <span>{{ele.subname}}</span>
          </li>
        </ul>
      </li>
    </ol>
  </div>
</template>
<script>
export default {
  name: "TreeViewDetail",
  data() {
    return {
      currentRoute: this.$route.path,
      refsDatas: [
        {
          name: 'dds',
          nameList: [
            {
              subname: 'hyuan'
            },
            {
              subname: 'hyn'
            },
            {
              subname: 'han'
            }                        
          ]
        },
        {
          name: '黄s',
          nameList: [
            {
              subname: '安提uan'
            },
            {
              subname: '里格'
            },
            {
              subname: '马缇抐'
            },{
              subname: '萨马他'
            }                    
          ]
        }        
      ]
    };
  },
  methods: {
    getRefs () {
      let eleDom = this.$refs.subname[1];
      let lis = eleDom.querySelectorAll('li');
      console.log(eleDom, lis);
      for (let i = 0; i< lis.length ; i++) {
        lis[i].className = ''
      }
      eleDom.className = 'currentTag';
      lis[0].className = 'currentTag';
    }
  },
  watch: {
    //监听路由，只要路由有变化(路径，参数等变化)都有执行下面的函数
    $route: {
      handler: function(val, oldVal) {
        this.currentRoute = val.name;
      },
      deep: true
    }
  }
};
</script>
<style scoped>
h3 {
  margin-top: 10px;
  font-weight: normal;
}
.currentTag{
  color: aqua;
}
</style>