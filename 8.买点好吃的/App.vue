<template>
  <div>
    <p>商品清单如下:</p>
    <div v-for="(obj, index) in list" :key="index">
      {{ obj.shopName }} -- {{ obj.price }}元/份
    </div>
    <p>请选择购买数量:</p>
    <Food
      v-for="(obj, index) in list"
      :key="index + ' '"
      :goodsname="obj.shopName"
      :index="index"
      :count="obj.count"
      @addE="addFn"
      @secE="secFn"
    >
    </Food>
    <p>总价为: {{ allPrice }}</p>
  </div>
</template>

<script>
import Food from "@/components/food.vue";
export default {
   components: {
    Food,
  },
  data() {
    return {
      // 商品数据
      list: [
        {
          shopName: "可比克薯片",
          price: 5.5,
          count: 0,
        },
        {
          shopName: "草莓酱",
          price: 3.5,
          count: 0,
        },
        {
          shopName: "红烧肉",
          price: 55,
          count: 0,
        },
        {
          shopName: "方便面",
          price: 12,
          count: 0,
        },
      ],
    };
  },
 
  methods: {
    addFn(index){
      this.list[index].count++
    },
    secFn(ind){
      this.list[index].count > 0 && this.list[index].count--
    }
  },
  computed: {
    allPrice(){
      return this.list.reduce((sum, obj) => sum += obj.count * obj.price, 0)
    }
  }
};
</script>