<script setup>
import {ref} from "vue";

let set = ref(false)
const sellectItem = ref({
  name: '',
  value: ''
})

const items =ref( [
  {
    "name": "foo1",
    "value": "bar1",
  },
  {
    "name": "foo2",
    "value": "bar2",
  },
  {
    "name": "foo3",
    "value": "bar3",
  },
  {
    "name": "foo4",
    "value": "bar4",
  },
])

</script>

<template>
  <div class="common-layout">
    <el-container>
      <el-main>
        <el-select v-model="sellectItem" class="select" placeholder="Select" size="large">
          <el-option
              v-for="item in items"
              :key="item.name"
              :label="item.name"
              :value="item"
          />
        </el-select>
        <div v-if="sellectItem.name" class="select-item">
          <el-card class="box-card">
            <template #header>
              <div >
                <span>{{ sellectItem.name }}</span>

              </div>
            </template>
            <div class="card-content">
              <div v-if="!set">{{sellectItem.value}}</div>
              <el-input v-else v-model="sellectItem.value"/>
              <el-button @click="set = !set" class="button" text>{{set ? 'Сохранить':'Изменить' }}</el-button>
            </div>
          </el-card>
        </div>
      </el-main>
    </el-container>
  </div>
</template>

<style scoped>

.select {
  margin-bottom: 10px;
}
.box-card {
  width: 480px;
}
.card-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>
