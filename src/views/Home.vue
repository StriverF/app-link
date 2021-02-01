<template>
  <div class="home">
    <img alt="PatPat Brand Poster" class="brand-poster" src="../assets/img/moment-of-glory.png">
    <div class="btn-box">
      <button id="uni-open-app" @click="openApp('unilink')">Universal link Open App</button>
      <button id="scheme-open-app" @click="openApp('scheme')">Scheme Url Open App</button>
    </div>
    <div class="download ">
      <img class="patpat-app" src="https://p-ssr-m.ppwebstatic.com/v2/assets/img/app-original-2.ba8aee5d.png" alt="Download PatPat App">
      <a href="https://itunes.apple.com/us/app/patpat-daily-deals-for-moms/id966740633?mt=8"> 在App Store上下載</a>
      <a href="https://play.google.com/store/apps/details?id=com.interfocusllc.patpat"> 在Google Play上獲取</a>
    </div>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component'
import HelloWorld from '@/components/HelloWorld.vue' // @ is an alias to /src

@Options({
  components: {
    HelloWorld
  },
  created () {
    window.onerror = function (message, source, lineno, colno, error) {
      console.log('捕获到异常：', { message, source, lineno, colno, error })
    }
  },
  mounted () {
    this.$nextTick(() => {
      try {
        const loadingRun = this.$route.query.loadingRun
        const openType = this.$route.query.openType
        if (loadingRun === 'unilink') {
          if (openType === 'blank') {
            window.open('https://uk-m.patpat.com/zh/product/Kid-Snowsuit-Windproof-Waterproof-Hooded-Quilted-Jacket-and-Adjustable-Snow-Bib-469150.html', '_blank')
          } else if (openType === 'click') {
            this.simulateClick('uni-open-app')
          } else {
            window.location.href = 'https://uk-m.patpat.com/zh/product/Kid-Snowsuit-Windproof-Waterproof-Hooded-Quilted-Jacket-and-Adjustable-Snow-Bib-469150.html'
          }
        } else if (loadingRun === 'scheme') {
          if (openType === 'click') {
            this.simulateClick('scheme-open-app')
          } else {
            window.location.href = 'patpat://?action=product_detail&event_id=1&product_id=469150'
          }
        }
      } catch (error) {
        const message = `无法 ${this.$route.query.loadingRun} link 启动APP`
        console.log(message, error.message)
        alert(message)
      }
    })
  },
  methods: {
    openApp (type: string) {
      console.log('openApp type', type)
      try {
        if (type === 'unilink') {
          window.location.href = 'https://uk-m.patpat.com/zh/product/Kid-Snowsuit-Windproof-Waterproof-Hooded-Quilted-Jacket-and-Adjustable-Snow-Bib-469150.html'
        } else if (type === 'scheme') {
          window.location.href = 'patpat://?action=product_detail&event_id=1&product_id=469150'
        }
      } catch (error) {
        const message = `无法 ${type} link 启动APP`
        console.log(message, error.message)
        alert(message)
      }
    },
    simulateClick (btnId: string) {
      console.log('simulateClick', btnId)
      const openAppBtn = document.getElementById(btnId)
      if (openAppBtn) {
        const event = new MouseEvent('click', {
          view: window,
          bubbles: true,
          cancelable: true,
          clientX: 12,
          clientY: 350
        })
        openAppBtn.dispatchEvent(event)
      }
    }
  }
})
export default class Home extends Vue {}
</script>

<style lang="less" scoped>
.brand-poster {
  width: 100%;
}
button {
  background-color: #ff2556;
  padding: 10px;
  border-radius: 6px;
  color: #fff;
}
.btn-box {
  text-align: left;
  position: relative;
  button {
    margin: 10px;
  }
}
.download {
  .patpat-app {
    width: 100%;
  }
  a {
    position: relative;
    display: inline-block;
    margin: 0 8px;
    padding: 10px;
    background: #414042;
    border-radius: 5px;
    color: #fff;
    line-height: 12px;
    font-size: 12px;
    .icon {
      position: absolute;
      width: 14px;
      left: 12px;
      top: 50%;
      transform: translateY(-50%);
    }
  }
}
</style>
