<script setup>
import { ref, onMounted } from 'vue';

import Section from './components/Section.vue';
import Header from './components/Header.vue';
import Content from './components/Content.vue';

const sections = ref([
  { bg_image: "Model3_Desktop.jpg", headline: "Model 3", subText: "", bottomText: "" },
  { bg_image: "ModelY_Desktop.jpg", headline: "Model Y", subText: "", bottomText: "Euro NCAP 5-Star Safety Rating" },
  { bg_image: "ModelS_Desktop.jpg", headline: "Model S", subText: "", bottomText: "" },
  { bg_image: "ModelX_Desktop.jpg", headline: "Model X", subText: "", bottomText: "" },
  { bg_image: "Solar_Desktop.jpg", headline: "Solar and Powerwall", subText: "Power Everything", bottomText: "" }
])

const sectionsContainer = ref(null);
const content = ref(null);

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
  content.value.update(sections.value[curSec].headline, sections.value[curSec].subText, opacity, sections.value[curSec].bottomText, curSec == sections.value.length - 1);
}

onMounted(() => {
  content.value.update(sections.value[0].headline, sections.value[0].subText, 1.0, sections.value[0].bottomText, false);
})


</script>

<template>
  <div class="main">
    <Header></Header>
    <Content ref="content" :headline="sections[0].headline"></Content>
    <div class="sections" ref="sectionsContainer" @scroll="handleScroll">
      <Section v-for="(item, index) in sections" :key="index" :bg_image="item.bg_image">
      </Section>
    </div>


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
