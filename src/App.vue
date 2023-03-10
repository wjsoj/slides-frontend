<script setup>
import { ref } from 'vue'
import { StyleProvider, Themes } from '@varlet/ui'

const active = ref(0)
const floating = ref(false)

let currentTheme = Themes.dark

function toggleTheme() {
  currentTheme = currentTheme ? null : Themes.dark
  StyleProvider(currentTheme)
}

function jump(url,isnew) {
  if(isnew){
    window.open(url,'_blank')
    console.log(isnew)
  }
  else{
    window.location.href=url
  }
}
</script>

<template>
  <div class="barbar">
    <var-app-bar round >
      My Slides
      <template #right>
        <var-button round text color="transparent" text-color="#fff" @click="toggleTheme">
          Switch Theme
        </var-button>
      </template>
    </var-app-bar>
  </div>

  <div class="cardlist">
    <div class="cardd">
      <var-card
        title="Slidev Template"
        subtitle="功能特性展示"
        description="Slidev 旨在为开发者提供灵活性和交互性，通过使用他们已经熟悉的工具和技术，使他们的演示文稿更加有趣、更具表现力和吸引力。当使用所见即所得的编辑器时，人们很容易被样式选项所干扰。Slidev 通过分离内容和视觉效果来弥补这一点。这使你能够一次专注于一件事，同时也能够重复使用社区中的主题。Slidev 并不寻求完全取代其他幻灯片制作工具。相反，它专注于迎合开发者社区的需求。"
        ripple
        src="https://s2.loli.net/2023/03/10/yRrVgcp51YXAH7z.png"
      >
        <template #extra>
          <var-button text type="warning" @click="jump('https://statuesque-mooncake-a37d40.netlify.app',0)">View Slide</var-button>
          <var-button text type="warning" @click="jump('https://github.com/wjsoj/slidev',1)">View Source</var-button>
        </template>
      </var-card>
    </div>
    <div class="cardd">
      <var-card
        title="本草纲目"
        subtitle="我表情悠哉 跳个大概"
        ripple
        src="https://varlet.gitee.io/varlet-ui/cat.jpg"
        v-model:floating="floating"
        @click="floating = true"
      >
        <template #extra>
          <var-button text type="warning" @click="window.open('https://statuesque-mooncake-a37d40.netlify.app','_self')">View Slide</var-button>
          <var-button text type="warning" @click="window.open('https://github.com/wjsoj/slidev','_blank')">View Source</var-button>
        </template>

        <template #floating-content>
          <var-divider dashed />
          
          <div class="card-example-text">
            如果华佗再世,崇洋都被医治,外邦来学汉字,激发我民族意识。马钱子、决明子、苍耳子，还有莲子；黄药子、苦豆子、川楝子，我要面子。用我的方式，改写一部历史。没什么别的事，跟着我念几个字。山药当归枸杞 GO，山药 当归 枸杞 GO，看我抓一把中药，服下一帖骄傲~
          </div>
        </template>
      </var-card>
    </div>
  </div>

</template>

<style>
.barbar {
  /* width: 100vw; */
  align-self: center;
  margin-top: -8px;
}

.card-example-text {
  padding: 14px;
  font-size: 14px;
  line-height: 28px;
}

.cardlist {
  display: grid;
  grid-template-columns: 1fr 1fr;
  margin-top: 20px;
  margin-left: 100px;
  margin-right: 100px;
}

.cardd {
  display: grid;
  padding: 20px;
}

@media (max-width: 767px) {
  .cardlist {
    margin-left: 10px;
    grid-template-columns: 1fr;
    margin-right: 10px;
  }
}
</style>
