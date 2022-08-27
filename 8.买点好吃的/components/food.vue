<template>
  <div>
    <span>{{ goodsname }}</span>
    <button @click="add(index)">+</button>
    <span> {{ count }} </span>
    <button @click="sec(index)">-</button>
  </div>
</template>

<script>
export default {
    props: ['goodsname', 'index', 'count'], // 商品名,索引,数量
    methods: {
        add(index){
            this.$emit('addE', index)
        },
        sec(index){
            this.$emit("secE", index)
        }
    }
};
</script>