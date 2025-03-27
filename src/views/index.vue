<template>
  <div class="app-container home h-full flex flex-col">
    <div class="home-top flex h-150px">
      <div class="card-a w-300px rounded-2xl"></div>
      <div class="card-b flex-1 rounded-2xl ml-20px flex-around-center">
        <div class="flex">
          <el-progress
            color="#23d5e2"
            :width="100"
            :show-text="false"
            type="circle"
            :percentage="40"
            :stroke-width="20"
            stroke-linecap="square"
          />
          <div class="flex flex-col justify-center ml-20px">
            <div class="text-12px">指标名称</div>
            <div class="text-24px">40%</div>
          </div>
        </div>
        <div class="flex">
          <el-progress
            color="#2a61ff"
            :show-text="false"
            :width="100"
            type="circle"
            :percentage="70"
            :stroke-width="20"
            stroke-linecap="square"
          />
          <div class="flex flex-col justify-center ml-20px">
            <div class="text-12px">指标名称</div>
            <div class="text-24px">40%</div>
          </div>
        </div>
        <div class="flex">
          <el-progress
            color="#ef7642"
            :show-text="false"
            :width="100"
            type="circle"
            :percentage="60"
            :stroke-width="20"
            stroke-linecap="square"
          />
          <div class="flex flex-col justify-center ml-20px">
            <div class="text-12px">指标名称</div>
            <div class="text-24px">40%</div>
          </div>
        </div>
      </div>
    </div>
    <div class="flex-1 grid grid-cols-2 gap-20px mt-20px">
      <div>
        <Echart class="card-shadow rounded-2xl" :options="options"></Echart>
      </div>
      <div>
        <Echart class="card-shadow rounded-2xl" :options="options"></Echart>
      </div>
    </div>
    <div class="flex-1 grid grid-cols-2 gap-20px mt-20px">
      <div>
        <Echart class="card-shadow rounded-2xl" :options="options"></Echart>
      </div>
      <div>
        <Echart class="card-shadow rounded-2xl" :options="options"></Echart>
      </div>
    </div>
  </div>
</template>

<script setup name="Index">
import Echart from '@/components/Echart'
import * as echarts from 'echarts'

const options = reactive({
  title: {
    text: ''
  },
  tooltip: {
    trigger: 'axis',
    axisPointer: {
      type: 'cross',
      label: {
        backgroundColor: '#6a7985'
      }
    }
  },
  legend: {
    show: false,
    data: ['Email', 'Union Ads', 'Video Ads']
  },
  grid: {
    top: '10%',
    left: '3%',
    right: '4%',
    bottom: '5%',
    containLabel: true
  },
  xAxis: [
    {
      type: 'category',
      boundaryGap: false,
      data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
    }
  ],
  yAxis: [
    {
      type: 'value'
    }
  ],
  series: [
    {
      name: 'Email',
      type: 'line',
      // stack: 'Total',
      smooth: true,
      areaStyle: {
        color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
          { offset: 0, color: '#2a61ff' },
          { offset: 0.2, color: 'rgba(42, 97, 255, 0.3)' },
          { offset: 1, color: 'rgba(42, 97, 255,0)' }
        ])
      },
      emphasis: {
        focus: 'series'
      },
      data: [120, 132, 290, 134, 90, 430, 210]
    },
    {
      name: 'Union Ads',
      type: 'line',
      // stack: 'Total',
      smooth: true,
      areaStyle: {
        color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
          { offset: 0, color: '#23d5e2' },
          { offset: 0.2, color: 'rgba(35,213,226, 0.3)' },
          { offset: 1, color: 'rgba(35,213,226,0)' }
        ])
      },
      emphasis: {
        focus: 'series'
      },
      data: [220, 182, 191, 234, 290, 330, 310]
    }
  ]
})
</script>

<style lang="scss">
.home {
  .card-shadow {
    background: rgba($color: #ebf3fc, $alpha: 0.2);
    box-shadow: inset 0 0 2px 1px #fff;
  }
  .card-a {
    background: var(--theme-success-color);
  }
  .card-b {
    // background: raba($color: #f3f9fe, $alpha: 0.8);
    background: rgba($color: #ebf3fc, $alpha: 0.2);
    // backdrop-filter: blur(10px);
    // -webkit-backdrop-filter: blur(10px);
    box-shadow: inset 0 0 2px 1px #fff;
  }
}
</style>
