<template>
  <div>

    <ul class="store">
      <li v-for="(item,index) in ulDatas" :key="item+index" >
      <span v-text="item"></span>
      <i class="fa fa-times " @click="del(index)"></i>
      </li>
      <li><input class="search" v-model="searchStr" /></li>
    </ul>

    <ul class="searchData">
      <li v-for="item in searchData" :key="item" v-text="item" @click="addToUl(item)"> </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'selectMe',
  props: ['search', 'items'],
  data () {
    return {
      searchStr: this.search,
      ulDatas: []
    }
  },
  computed: {
    searchData: function () {
      if (this.searchStr) {
        return this.items.filter(item => {
          return item.indexOf(this.searchStr) > -1
        })
      }
      return []
    }
  },
  methods: {
    addToUl (item) {
      this.ulDatas.push(item)
    },
    del (index) {
      this.ulDatas.splice(index, 1)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.search {
  border: 1px solid #000000;
  box-sizing: border-box;
  /* outline:none; */

}
.searchData {
  list-style: none;
  margin: 4px;
  padding: 0;
  background: #fff;
}
.searchData li {
  background: #fff;
  /* border:1px solid #b3b3b3; */
  box-sizing: border-box;
  border-radius: 3px;
  padding: 5px;
}
.searchData li:hover {
  background: #efefef;
}
.store {
  list-style: none;
  padding: 5px;
  border: 1px solid #bbb9b9eb;
  box-sizing: border-box;
  margin: 4px;
border-radius: 5px;
}
.store li {
  display: inline-block;
  background: #fff;
  border:1px solid #b3b3b3;
  box-sizing: border-box;
  border-radius: 3px;
  padding: 5px;
  margin-left: 5px;
}
.store li:last-child{
 border:none;
 padding: 0;
 margin: 0;
}
.store li:last-child  input{
  border:none;
   outline: none;
}
.store li i{
cursor: pointer;
}
</style>
