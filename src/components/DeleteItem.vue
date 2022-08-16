<template>
  <div>
    <div v-for="(item, index) in list" :key="index">
      <v-touch v-on:swipeleft="onSwipeLeft(item)" class="item">
        <span>{{ item.name }}</span>
        <span>{{ item.description }}</span>
      </v-touch>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "DeleteItem",
  data() {
    return {
      list: [
        { id: 1, name: "neko", description: "这是猫猫1" },
        { id: 2, name: "rabbitmq", description: "这是喵喵2" },
        { id: 3, name: "redis", description: "这是喵喵喵3" },
      ],
    };
  },

  methods: {
    onSwipeLeft(item) {
      // 删除接口URL
      const url = "http://192.168.3.54:8089/api/test/Delete/" + item.id;

      // 配置
      const config = {
        method: "delete",
        url,
      };

      // 向后端发请求
      axios(config)
        .then((response) => {
          // 查看后端返回结果
          console.log(JSON.stringify(response.data));

          // 前端删除
          const res = this.list.filter((list_item) => {
            return list_item.id !== item.id;
          });
          this.list = res;
        })
        .catch((error) => {
          // 出错查看错误
          console.log(error);
        });
    },
  },
};
</script>

<style>
span {
  margin: 10px;
}

.item {
  padding: 0 auto;
  margin-bottom: 10px;
  border: 1px solid black;
}
</style>
