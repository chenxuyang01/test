<template>
  <div id="index">
    <dv-full-screen-container class="bg">
      <dv-loading v-if="loading">Loading...</dv-loading>
      <div v-else class="host-body">
        <div class="d-flex jc-center">
          <dv-decoration-10 style="width:33.3%;height:.0625rem;" />
          <div class="d-flex jc-center">
            <dv-decoration-8 :color="['#568aea', '#000000']" style="width:2.5rem;height:.625rem;" />
            <div class="title">
              <span class="title-text">探矿系统</span>
              <dv-decoration-6
                class="title-bototm"
                :reverse="true"
                :color="['#50e3c2', '#67a1e5']"
                style="width:3.125rem;height:.1rem;"
              />
            </div>
            <dv-decoration-8
              :reverse="true"
              :color="['#568aea', '#000000']"
              style="width:2.5rem;height:.625rem;"
            />
          </div>
          <dv-decoration-10 style="width:33.3%;height:.0625rem; transform: rotateY(180deg);" />
        </div>

        <!-- 第二行 -->
        <div class="d-flex jc-between px-2">
          <div class="d-flex" style="width: 40%">
            
            <div
              class="react-right ml-4"
              style="width: 6.25rem; text-align: left;background-color: #0f1325;"
            >
              <span class="react-before"></span>
              <span class="text">勘查项目登记</span>
            </div>
            <div class="react-right ml-3" style="background-color: #0f1325;">
              <span class="text">地理区域显示</span>
            </div>
          </div>
          <div style="width: 40%" class="d-flex">
            <div class="react-left bg-color-blue mr-3">
              <span class="text fw-b">统计视图</span>
            </div>
            <div
              class="react-left mr-4"
              style="width: 6.25rem; background-color: #0f1325; text-align: right;"
            >
              <span class="react-after"></span>
              <span class="text">{{dateYear}} {{dateWeek}} {{dateDay}}</span>
            </div>
          </div>
        </div>

        <div class="body-box">
          <!-- 第三行数据 -->
          <div class="content-box">
            <div>
              <!-- 搜索框 -->
              <dv-border-box-12>
                <bottomLeftCapacity />
              </dv-border-box-12>
            </div>
            <div>
              <dv-border-box-8 dur=8>
                <centerLeftMap />
              </dv-border-box-8>
            </div>
            <div>
              <!-- 搜索框 -->
              <dv-border-box-12>
                <centerRightChart />
              </dv-border-box-12>
            </div>
          </div>

          <div class="bottom-box">
            <dv-border-box-12>
              <bottomLeftChart />
            </dv-border-box-12>
            <dv-border-box-12>
              <bottomXiangxixinxi/>
            </dv-border-box-12>
            <dv-border-box-12>
              <bottomRightChart/>
            </dv-border-box-12>
          </div>
        </div>

      </div>
    </dv-full-screen-container>
  </div>
</template>

<script>
import { formatTime } from '../utils/index.js'
import centerLeftMap from './centerLeftMap'
import bottomLeftCapacity from './bottomLeftCapacity'
import bottomRightChart from './bottomRightChart'
import bottomXiangxixinxi from './bottomXiangxixinxi'
import centerRightChart from './centerRightChart'
import bottomLeftChart from './bottomLeftChart'
// import centerLeft1 from "./centerLeft1";
// import centerLeft2 from "./centerLeft2";
// import centerRight1 from "./centerRight1";
// import centerRight2 from "./centerRight2";
// import centerRight3 from "./centerRight3";
// import center from "./center";
// import bottomLeft from "./bottomLeft";
// import bottomRight from "./bottomRight";
export default {
  data () {
    return {
      loading: true,
      dateDay: null,
      dateYear: null,
      dateWeek: null,
      weekday: ["周日", "周一", "周二", "周三", "周四", "周五", "周六"],
    };
  },
  components: {
    centerLeftMap,
    bottomLeftCapacity,
    bottomRightChart,
    bottomXiangxixinxi,
    centerRightChart,
    bottomLeftChart,
    // centerTable
    // centerLeft1,
    // centerLeft2,
    // centerRight1,
    // centerRight2,
    // centerRight3,
    // center,
    // bottomLeft,
    // bottomRight
  },
  mounted () {
    this.timeFn();
    this.cancelLoading();
  },
  methods: {
    timeFn () {
      setInterval(() => {
        this.dateDay = formatTime(new Date(), 'HH: mm: ss');
        this.dateYear = formatTime(new Date(), 'yyyy-MM-dd');
        this.dateWeek = this.weekday[new Date().getDay()];
      }, 1000)
    },
    cancelLoading () {
      setTimeout(() => {
        this.loading = false;
      }, 500);
    }
  }
};
</script>

<style lang="scss">
@import '../assets/scss/index.scss';
</style>