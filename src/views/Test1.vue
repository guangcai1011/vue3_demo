<template>
  <div>0000</div>
  <div>
    <input
      type="checkbox"
      class="input-checkbox"
      ：checked="fruitIds.length === fruits.length"
      @click="checkedAll()"
    />全选
    <div v-for="(fruit, index) in fruits" :key="index">
      <!--判断fruitIds是否包含当前fruit，fruitIds.indexOf(fruit.fruitId)返回包含fruit的下标, 若不包含则返回-1-->
      <input
        type="checkbox"
        :checked="fruitIds.indexOf(fruit.fruitId) >= 0"
        name="checkboxinput"
        class="input-checkbox"
        @click="checkedOne(fruit.id)"
      />
    </div>
    <!--默认删除按钮不能点击, 当选中某一checkbox时可以删除-->
    <button
      :disabled="!fruitIds.length > 0"
      value="Delete"
      @click="deleteFruits()"
    >
      Delete
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      fruits: [
        {
          id: "1",
          value: "苹果",
        },
        {
          id: "2",
          value: "荔枝",
        },
        {
          id: "3",
          value: "香蕉",
        },
        {
          id: "4",
          value: "火龙果",
        },
      ],
      fruitIds: ["1", "3", "4"],
      // 初始化全选按钮, 默认不选
      isCheckedAll: false,
    };
  },
  methods: {
    checkedOne(fruitId) {
      let idIndex = this.fruitIds.indexOf(fruitId);
      if (idIndex >= 0) {
        // 如果已经包含了该id, 则去除(单选按钮由选中变为非选中状态)
        this.fruitIds.splice(idIndex, 1);
      } else {
        // 选中该checkbox
        this.fruitIds.push(fruitId);
      }
    },
    checkedAll() {
      this.isCheckedAll = !this.isCheckedAll;
      if (this.isCheckedAll) {
        // 全选时
        this.fruitIds = [];
        this.fruits.forEach(function (fruit) {
          this.fruitIds.push(fruit.fruitId);
        }, this);
      } else {
        this.fruitIds = [];
      }
    },
    deleteFruits() {},
  },
};
</script>

<style lang="sass" scoped></style>
