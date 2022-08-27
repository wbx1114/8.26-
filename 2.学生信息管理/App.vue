<template>
  <div id="app">
    <div>
      <span>姓名:</span>
      <input type="text" v-model="uname" />
    </div>
    <div>
      <span>年龄:</span>
      <input type="number" v-model="ages" />
    </div>
    <div>
      <span>性别:</span>
      <select v-model="sexs">
        <option value="男">男</option>
        <option value="女">女</option>
      </select>
    </div>
    <div>
      <button @click="addBtn">添加</button>
      <button @click="xiuBtn(index)">修改</button>

    </div>
    <div>
      <table border="1" cellpadding="10" cellspacing="0">
        <tr>
          <th>序号</th>
          <th>姓名</th>
          <th>年龄</th>
          <th>性别</th>
          <th>操作</th>
        </tr>
        <tr v-for="(item, index) in list" :key="index">
          <td>{{ index + 1 }}</td>
          <td>{{ item.name }}</td>
          <td>{{ item.age }}</td>
          <td>{{ item.sex }}</td>
          <td>
            <button @click="delBtn(index)">删除</button>
            <button @click="editBtn(item,index)">编辑</button>
          </td>
        </tr>
      </table>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      index:'',
      edit: false,
      uname: "",
      ages: "",
      sexs: "男",
      list: [
        {
          name: "妲己",
          age: 16,
          sex: "女",
        },
        {
          name: "王昭君",
          age: 17,
          sex: "女",
        },
        {
          name: "大鱼",
          age: 18,
          sex: "男",
        },
        {
          name: "小蔡",
          age: 12,
          sex: "女",
        },
      ],
    };
  },
  methods: {
  addBtn() {
        if (this.uname === "" || this.ages === "") {
          alert("请在输入框内输入内容");
        } else {
          const obj = {
            name: this.uname,
            age: this.ages,
            sex: this.sexs,
          };
          this.list.push(obj);
          this.uname = "";
          this.ages = "";
      }
    },
  delBtn(index) {
    this.list.splice(index, 1);
  },
  editBtn(item,index) {
    this.uname = item.name;
    this.ages = item.age;
    this.sexs = item.sex;
    this.index=index
  },
  xiuBtn(index){
this.list[index].name=this.uname
this.list[index].age=this.ages
this.list[index].sex=this.sexs
  }
  },
 
};
</script>
