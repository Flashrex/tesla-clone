<script setup>
import { ref, onMounted } from 'vue';

import Section from './components/Section.vue';
import Header from './components/Header.vue';
import Content from './components/Content.vue';

const sections = ref([
  { bg_image: "Model3_Desktop.jpg", bg_image_mobile: "Model3_Mobile.jpg", headline: "Model 3", subText: "", bottomText: "" },
  { bg_image: "ModelY_Desktop.jpg", bg_image_mobile: "ModelY_Mobile.jpg", headline: "Model Y", subText: "", bottomText: "Euro NCAP 5-Star Safety Rating" },
  { bg_image: "ModelS_Desktop.jpg", bg_image_mobile: "ModelS_Mobile.jpg", headline: "Model S", subText: "", bottomText: "" },
  { bg_image: "ModelX_Desktop.jpg", bg_image_mobile: "ModelX_Mobile.jpg", headline: "Model X", subText: "", bottomText: "" },
  { bg_image: "Solar_Desktop.jpg", bg_image_mobile: "Solar_Mobile.jpg", headline: "Solar and Powerwall", subText: "Power Everything", bottomText: "" }
])

const sectionsContainer = ref(null);
const content = ref(null);
const useMobile = ref(false);

function handleScroll() {
  const x = sectionsContainer?.value;
  const sectionHeight = Math.abs(x.scrollHeight / sections.value.length);

  //check in which section we are
  let curSec = Math.abs(x.scrollTop / sectionHeight);

  //calculate opacity
  let opacity = 1.0;
  let y = curSec % 1;

  if (y < 0.5) {
    opacity = 1 - y * 2;
    curSec = Math.floor(curSec);
  } else {
    opacity = Math.abs(1 - y * 2);
    curSec = Math.ceil(curSec);
  }

  const data = {
    text: sections.value[curSec].headline,
    sText: sections.value[curSec].subText,
    bText: sections.value[curSec].bottomText,
    lSection: curSec == sections.value.length - 1,
    opacity: opacity
  }

  content.value.update(data);
}

onMounted(() => {
  const data = {
    text: sections.value[0].headline,
    sText: sections.value[0].subText,
    bText: sections.value[0].bottomText,
    lSection: false,
    opacity: 1.0
  }

  content.value.update(data);

  window.addEventListener('resize', onResize);
})

function onResize() {
  //console.log(window.innerWidth + " : " + useMobile.value);
  useMobile.value = window.innerWidth <= 768;
}




</script>

<template>
  <div class="main">
    <Header></Header>
    <div class="sections" ref="sectionsContainer" @scroll="handleScroll">
      <Section v-if="useMobile" v-for="(item, index) in sections" :key="index" :bg_image="item.bg_image_mobile"></Section>


      <Section v-else v-for="(item, index) in sections" :key="index + 1" :bg_image="item.bg_image">
      </Section>
    </div>

    <Content ref="content" :headline="sections[0].headline"></Content>
  </div>
</template>

<style scoped>
.sections {
  max-height: 100vh;
  overflow-y: scroll;
  scroll-behavior: smooth;
  scroll-snap-type: y mandatory;
}
</style>
