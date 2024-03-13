<script setup lang="ts">
const airTemp = [
  {
    name: "空调1",
    list: {
      temperature: {
        icon: "iconfont icon-wendu",
        value: "温度 20",
      },
      humidity: {
        icon: "iconfont icon-shidu1",
        value: "湿度 20%",
      },
      status: {
        icon: "iconfont icon-shezhi",
        value: "状态 制冷",
      },
    },
    list2: {
      wind: {
        icon: "iconfont icon-feng",
        value: "回风 25",
      },
      humidity: {
        icon: "iconfont icon-shidu",
        value: "回湿 40%",
      },
      wind2: {
        icon: "iconfont icon-fengshan",
        value: "风机 on",
      },
    },
  },
];
const tableData = [
  {
    number: "T098j",
    temp: 24.56,
    box: "rack10",
    type: 1,
  },
  {
    number: "T910d",
    temp: 23.09,
    box: "rack36",
    type: 0,
  },
  {
    number: "T237j",
    temp: 26.34,
    box: "rack4",
    type: 0,
  },
  {
    number: "T217j",
    temp: 24.21,
    box: "rack18",
    type: 0,
  },
  {
    number: "T217j",
    temp: 24.21,
    box: "rack18",
    type: 0,
  },
  {
    number: "T217j",
    temp: 24.21,
    box: "rack18",
    type: 0,
  },
];
const tableData2 = [
  {
    number: "H98",
    humidness: 45.65,
    box: "rack33",
    type: 1,
  },
  {
    number: "H30",
    humidness: 43.23,
    box: "rack54",
    type: 1,
  },
  {
    number: "H24",
    humidness: 49.94,
    box: "rack34",
    type: 0,
  },
  {
    number: "H90",
    humidness: 43.39,
    box: "rack8",
    type: 0,
  },
  {
    number: "H90",
    humidness: 43.39,
    box: "rack8",
    type: 0,
  },
  {
    number: "H90",
    humidness: 43.39,
    box: "rack8",
    type: 0,
  },
];
</script>

<template>
  <div class="top">
    <div class="topLeft">
      <div class="allTitle">空调温度:</div>
      <!-- 因为传入的值需要加"".且是一个对象的时候，属性值是字符串需要加‘’ -->
      <el-card style="margin-bottom: 10px">
        <div class="title"><span> 空调1 </span> <span>开关</span></div>
        <div class="listBox">
          <div>
            <p
              v-for="(item, index) in airTemp[0].list"
              :key="item"
              class="text item"
            >
              <i :class="item.icon"></i>
              {{ item.value }}
            </p>
          </div>
          <div style="margin-left: 20px">
            <p
              v-for="(item, index) in airTemp[0].list2"
              :key="item"
              class="text item"
            >
              <i :class="item.icon"></i>
              {{ item.value }}
            </p>
          </div>
        </div>
      </el-card>
      <el-card style="margin-bottom: 10px">
        <div class="title">空调2</div>
        <div class="listBox">
          <div>
            <p
              v-for="(item, index) in airTemp[0].list"
              :key="item"
              class="text item"
            >
              <i :class="item.icon"></i>
              {{ item.value }}
            </p>
          </div>
          <div style="margin-left: 20px">
            <p
              v-for="(item, index) in airTemp[0].list2"
              :key="item"
              class="text item"
            >
              <i :class="item.icon"></i>
              {{ item.value }}
            </p>
          </div>
        </div>
      </el-card>
      <el-card>
        <div class="title">空调3</div>
        <div class="listBox">
          <div>
            <p
              v-for="(item, index) in airTemp[0].list"
              :key="item"
              class="text item"
            >
              <i :class="item.icon"></i>
              {{ item.value }}
            </p>
          </div>
          <div style="margin-left: 20px">
            <p
              v-for="(item, index) in airTemp[0].list2"
              :key="item"
              class="text item"
            >
              <i :class="item.icon"></i>
              {{ item.value }}
            </p>
          </div>
        </div>
      </el-card>
      <el-card>
        <div class="title">空调4</div>
        <div class="listBox">
          <div>
            <p
              v-for="(item, index) in airTemp[0].list"
              :key="item"
              class="text item"
            >
              <i :class="item.icon"></i>
              {{ item.value }}
            </p>
          </div>
          <div style="margin-left: 20px">
            <p
              v-for="(item, index) in airTemp[0].list2"
              :key="item"
              class="text item"
            >
              <i :class="item.icon"></i>
              {{ item.value }}
            </p>
          </div>
        </div>
      </el-card>
    </div>
    <div class="topRight">
      <el-card
        :body-style="{ width: '100%', height: '100%' }"
        style="width: 100%; height: 100%; padding: 5px 5px"
      >
        <div class="topRightInner">
          <div class="top-l">
            <div class="title">温度传感器</div>
            <div class="content">
              <span>传感器数量:&nbsp;32</span>
              <img src="../assets/images/温度.png" alt="" />
            </div>

            <el-table :data="tableData" border style="width: 100%">
              <el-table-column width="100px" prop="number" label="设备编号" />
              <el-table-column width="100px" prop="temp" label="温度" />
              <el-table-column width="100px" prop="box" label="所属机柜" />
              <el-table-column width="100px" prop="type" label="类型">
                <template #default="scope">
                  <el-tag
                    :type="scope.row.type === 1 ? 'success' : 'warning'"
                    >{{ scope.row.type === 1 ? "入风" : "出风" }}</el-tag
                  >
                </template>
              </el-table-column>
            </el-table>
          </div>
          <div class="top-r">
            <div class="title">湿度传感器</div>
            <div class="content">
              <span>传感器数量:&nbsp;13</span>
              <img src="../assets/images/湿度.png" alt="" />
            </div>
            <el-table :data="tableData2" border style="width: 100%">
              <el-table-column width="100px" prop="number" label="设备编号" />
              <el-table-column width="100px" prop="humidness" label="湿度" />
              <el-table-column width="100px" prop="box" label="所属机柜" />
              <el-table-column width="100px" prop="type" label="类型">
                <template #default="scope">
                  <el-tag
                    :type="scope.row.type === 1 ? 'success' : 'warning'"
                    >{{ scope.row.type === 1 ? "入风" : "出风" }}</el-tag
                  >
                </template>
              </el-table-column>
            </el-table>
          </div>
        </div>
      </el-card>
    </div>
  </div>
</template>

<style scoped lang="scss">
.top {
  display: flex;
  padding: 10px 10px;
  width: 100%;
  height: 50vh;
  .topLeft {
    display: flex;
    flex-wrap: wrap;
    width: 560px;
    justify-content: space-around;
    background-color: rgb(245, 245, 245); /*  */
    padding: 5px 5px;
    :deep(.el-card) {
      border-radius: 20px;
    }
    :deep(.el-card__body) {
      padding: 5px 10px;
    }
    .allTitle {
      flex: 0 0 100%;
      font-weight: bolder;
      font-size: larger;
      margin-bottom: 15px;
    }
    .title {
      display: flex;
      font-size: larger;
      justify-content: space-between;
    }
  }
  .topRight {
    width: 60%;
    background-color: pink;
    margin-left: 20px;
    .topRightInner {
      display: flex;
      justify-content: space-around;
      .top-l {
        height: 200px;
        .content {
          height: 70px;
          span {
            font-size: 19px;
            position: relative;
            bottom: 86px;
          }
          img {
            width: 200px;
            position: relative;
            bottom: 40px;
            left: 80px;
          }
        }
        .title {
          font-weight: bolder;
          font-size: larger;
          margin-bottom: 15px;
        }
      }
      .top-r {
        margin-left: 20px;
        .title {
          font-weight: bolder;
          font-size: larger;
          margin-bottom: 15px;
        }
        .content {
          height: 70px;
          span {
            font-size: 19px;
            position: relative;
            bottom: 86px;
          }
          img {
            width: 200px;
            position: relative;
            bottom: 40px;
            left: 80px;
          }
        }
      }
    }
  }
}

.listBox {
  display: flex;
}
</style>
