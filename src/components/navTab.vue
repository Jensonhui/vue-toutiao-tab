<template>
  <div>
    <div class='navbox'>
      <div class="time-box-container" ref="timeBoxCont">
        <ul class='nav-list' ref='timeBox'>
          <li
            v-for='(item, index) in navList'
            :key='index'
            @click='changeNav(index, item.statue)'
            :class='{active:navIndex==index}'
          >
            <h4>{{item.time}}</h4>
            <h6>{{item.name}}</h6>
          </li>
        </ul>
      </div>
    </div>

    <v-touch
      class="wrapper"
      @swipeleft="swiperleft"
      @swiperight="swiperright"
      :swipe-options="{direction: 'horizontal'}"
    >
      <transition-group
        enter-active-class="animated fadeInRight faster"
        leave-active-class=""
        tag="div"
      >
      <ul class="seckill-list" v-for="(itemOne,indexOne) in shopList" :key="indexOne + 1" v-show="indexOne == navIndex">
        <li v-for="(itemTwo, indexTwo) in itemOne" :key="indexTwo + 1">
          <h5>{{itemTwo.subTitle}}</h5>
          <h6>{{itemTwo.seckillPrice}}</h6>
        </li>
      </ul>
      </transition-group>
    </v-touch>
  </div>
</template>

<script>
export default {
  name: 'navTab',
  components: {},
  data () {
    return {
      navList: [
        { time: '12:00', name: '正在抢购', statue: true },
        { time: '14:00', name: '即将开始', statue: false },
        { time: '16:00', name: '即将开始', statue: false },
        { time: '18:00', name: '即将开始', statue: false },
        { time: '20:00', name: '即将开始', statue: false },
        { time: '22:00', name: '即将开始', statue: false },
        { time: '24:00', name: '即将开始', statue: false }
      ],
      // TabIndex
      navIndex: 0,
      navWidthArr: [],
      // LIST
      shopList: [
        [
          {
            status: true,
            subTitle: '陕西红富士苹果新鲜当季果园现摘冰糖心脆甜多汁',
            seckillPrice: '66.20'
          }, {
            status: true,
            subTitle: '陕西红富士苹果新鲜当季果园现摘冰糖心脆甜多汁',
            seckillPrice: '66.20'
          }, {
            status: true,
            subTitle: '陕西红富士苹果新鲜当季果园现摘冰糖心脆甜多汁',
            seckillPrice: '66.20'
          }
        ],
        [
          {
            status: true,
            subTitle: '陕西红富士苹果新鲜当季果园现摘冰糖心脆甜多汁',
            seckillPrice: '66.20'
          }
        ],
        [
          {
            status: true,
            subTitle: '陕西红富士苹果新鲜当季果园现摘冰糖心脆甜多汁',
            seckillPrice: '66.20'
          }, {
            status: true,
            subTitle: '陕西红富士苹果新鲜当季果园现摘冰糖心脆甜多汁',
            seckillPrice: '66.20'
          }, {
            status: true,
            subTitle: '陕西红富士苹果新鲜当季果园现摘冰糖心脆甜多汁',
            seckillPrice: '66.20'
          }, {
            status: true,
            subTitle: '陕西红富士苹果新鲜当季果园现摘冰糖心脆甜多汁',
            seckillPrice: '66.20'
          }
        ],
        [
          {
            status: true,
            subTitle: '陕西红富士苹果新鲜当季果园现摘冰糖心脆甜多汁',
            seckillPrice: '66.20'
          }, {
            status: true,
            subTitle: '陕西红富士苹果新鲜当季果园现摘冰糖心脆甜多汁',
            seckillPrice: '66.20'
          }
        ],
        [
          {
            status: true,
            subTitle: '陕西红富士苹果新鲜当季果园现摘冰糖心脆甜多汁',
            seckillPrice: '66.20'
          }, {
            status: true,
            subTitle: '陕西红富士苹果新鲜当季果园现摘冰糖心脆甜多汁',
            seckillPrice: '66.20'
          }, {
            status: true,
            subTitle: '陕西红富士苹果新鲜当季果园现摘冰糖心脆甜多汁',
            seckillPrice: '66.20'
          }
        ],
        [
          {
            status: true,
            subTitle: '陕西红富士苹果新鲜当季果园现摘冰糖心脆甜多汁',
            seckillPrice: '66.20'
          }, {
            status: true,
            subTitle: '陕西红富士苹果新鲜当季果园现摘冰糖心脆甜多汁',
            seckillPrice: '66.20'
          }, {
            status: true,
            subTitle: '陕西红富士苹果新鲜当季果园现摘冰糖心脆甜多汁',
            seckillPrice: '66.20'
          }, {
            status: true,
            subTitle: '陕西红富士苹果新鲜当季果园现摘冰糖心脆甜多汁',
            seckillPrice: '66.20'
          }, {
            status: true,
            subTitle: '陕西红富士苹果新鲜当季果园现摘冰糖心脆甜多汁',
            seckillPrice: '66.20'
          }, {
            status: true,
            subTitle: '陕西红富士苹果新鲜当季果园现摘冰糖心脆甜多汁',
            seckillPrice: '66.20'
          }
        ],
        [
          {
            status: true,
            subTitle: '陕西红富士苹果新鲜当季果园现摘冰糖心脆甜多汁',
            seckillPrice: '66.20'
          }, {
            status: true,
            subTitle: '陕西红富士苹果新鲜当季果园现摘冰糖心脆甜多汁',
            seckillPrice: '66.20'
          }, {
            status: true,
            subTitle: '陕西红富士苹果新鲜当季果园现摘冰糖心脆甜多汁',
            seckillPrice: '66.20'
          }
        ]
      ]
    }
  },
  mounted () {
    this.computeNavList()
  },
  methods: {
    // navlist列表个数宽
    computeNavList () {
      const childs = this.$refs.timeBox.children
      for (let i = 0, len = childs.length; i < len; i++) {
        const childPotion = {
          domWidth: childs[i].clientWidth,
          domLeft: childs[i].offsetLeft
        }
        this.navWidthArr.push(childPotion)
      }
      // 默认显示出NAV选中项
      // const boxWidth = (this.$refs.timeBox.clientWidth / 2)
      // const domLeft = this.navWidthArr[this.navIndex].domLeft
      // const domWidth = (this.navWidthArr[this.navIndex].domWidth / 2)
      // const leftNum = parseInt(domLeft + domWidth - boxWidth)
      // this.$refs.timeBoxCont.scrollLeft = leftNum
    },
    // 切换导航条
    changeNav (index, statue) {
      this.navIndex = index
      this.showImg = statue
      const boxWidth = (this.$refs.timeBox.clientWidth / 2)
      const domLeft = this.navWidthArr[this.navIndex].domLeft
      const domWidth = (this.navWidthArr[this.navIndex].domWidth / 2)
      const leftNum = parseInt(domLeft + domWidth - boxWidth)
      if (this.navList.length >= 3 && this.navIndex >= 3) {
        this.$refs.timeBoxCont.scrollLeft = leftNum
      }

      if (this.navIndex <= this.navList.length - 3) {
        this.$nextTick(() => {
          this.$refs.timeBoxCont.scrollLeft = parseInt(domLeft - boxWidth - domWidth)
        })
      }
    },
    // 左侧滑动
    swiperleft () {
      this.navIndex++
      if (this.navIndex >= this.navList.length - 1) {
        this.navIndex = this.navList.length - 1
        return false
      }

      if (this.navList.length >= 6 && this.navIndex >= 3) {
        const boxWidth = (this.$refs.timeBox.clientWidth / 2)
        const domLeft = this.navWidthArr[this.navIndex].domLeft
        const domWidth = (this.navWidthArr[this.navIndex].domWidth / 2)
        const leftNum = parseInt(domLeft + domWidth - boxWidth)
        this.$refs.timeBoxCont.scrollLeft = leftNum
      }
    },
    // 右侧滑动
    swiperright: function () {
      this.navIndex--
      if (this.navIndex <= 0) {
        this.navIndex = 0
        return false
      }

      const boxWidth = (this.$refs.timeBox.clientWidth / 2)
      const domLeft = this.navWidthArr[this.navIndex].domLeft
      const domWidth = (this.navWidthArr[this.navIndex].domWidth / 2)
      this.$nextTick(() => {
        this.$refs.timeBoxCont.scrollLeft = parseInt(domLeft - boxWidth - domWidth)
      })
    }
  }
}
</script>

<style lang="less" scoped>
ul{
  margin: 0;
  padding: 0;
}
ul li{
  list-style: none;
}
.wrapper{
  width: 100vw;
  height: 100vh;
}
.navbox{
  width: 100%;
  overflow: hidden;
  text-align: center;
  border-bottom: 1px solid #ccc
}
.navbox .time-box-container{
  overflow-x: scroll;
  overflow-y: hidden;
  -ms-overflow-style: none;
  overflow: -moz-scrollbars-none
}
.navbox .nav-list{
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.navbox .nav-list li{
  min-width: 17%;
  font-size: 1rem;
  font-weight: bold;
  white-space: nowrap;
  padding-right: 1rem;
}
.navbox .nav-list li h4,
.navbox .nav-list li h6{
  margin: 0.5rem 0
}
.navbox .nav-list li.active{
  color: red;
}
.seckill-list{
  font-size: 1rem;
}
.seckill-list li{
  display: flex;
  align-items: center;
  margin: 1rem 0;
  justify-content: space-around;
  border-bottom: 1px solid #ccc;
}
.tips{
  font-size: 0.6rem;
  line-height: 1.5rem;
}
</style>
