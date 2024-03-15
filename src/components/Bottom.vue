<script setup lang="ts">
import BottomRight from "./BottomRight.vue";
const tableData = [
  {
    time: "2023-9-14",
    no: "0122",
    name: "空调22",
    type: "aircon",
    way: "定时调温策略2",
    range: "查看",
  },
  {
    time: "2023-9-14",
    no: "0122",
    name: "空调22",
    type: "aircon",
    way: "定时调温策略2",
    range: "查看",
  },
  {
    time: "2023-9-14",
    no: "0122",
    name: "空调22",
    type: "cooling",
    way: "定时调温策略2",
    range: "查看",
  },
  {
    time: "2023-9-14",
    no: "0122",
    name: "空调22",
    type: "aircon",
    way: "定时调温策略2",
    range: "查看",
  },
];
const filterTag = (value: any, row: any) => {
  return row.type === value;
};
</script>
<template>
  <div class="Bottom">
    <el-card>
      <div class="content">
        <div class="bottom-l">
          <div class="title">湿度传感器</div>
          <el-table :data="tableData" border style="width: 100%">
            <el-table-column width="100px" prop="time" label="时间" />
            <el-table-column width="100px" prop="no" label="设备编号" />
            <el-table-column width="100px" prop="name" label="设备名称" />
            <el-table-column
              prop="type"
              label="设备类型"
              width="100"
              :filters="[
                { text: 'aircon', value: 'aircon' },
                { text: 'cooling', value: 'cooling' },
              ]"
              :filter-method="filterTag"
              filter-placement="bottom-end"
            >
              <template #default="scope">
                <el-tag
                  :type="scope.row.type === 'aircon' ? 'success' : ''"
                  disable-transitions
                  >{{ scope.row.type }}</el-tag
                >
              </template>
            </el-table-column>
            <el-table-column width="100px" prop="way" label="执行策略" />
            <el-table-column width="100px" prop="range" label="节能幅度">
              <template #default="scope">
                <el-button>{{ scope.row.range }}</el-button>
              </template>
            </el-table-column>
          </el-table>
        </div>
        <div class="bottom-r">
          <BottomRight />
        </div>
      </div>
    </el-card>
  </div>
</template>
<style scoped lang="scss">
.Bottom {
  width: 100%;
  height: 45vh;
  padding: 5px 10px;
  :deep(.el-card__body) {
    padding: 5px 10px;
  }
  .title {
    margin-bottom: 20px;
  }
  .content {
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: space-between;
    .bottom-l {
      width: 40%;
    }
    .bottom-r {
      width: 50%;
    }
  }
}
</style>
