<script setup>
import { ref } from 'vue';

const content = ref(null);
const headline = ref("");
const subtext = ref("");
const bottomText = ref("");
const lastSection = ref(false);

defineExpose({ update })

function update(data) {

    //update text
    headline.value = data.text;
    subtext.value = data.sText;
    bottomText.value = data.bText;
    lastSection.value = data.lSection;

    content.value.style.opacity = data.opacity;
}

</script>

<template>
    <div ref="content" class="container">
        <h1 v-if="headline != ''">{{ headline }}</h1>
        <h3 v-if="subtext != ''">{{ subtext }}</h3>

        <div ref="btn_box" class="button_container">
            <span id="button_dark">Custom Order</span>
            <span>Learn More</span>
        </div>

        <p v-if="bottomText != ''">{{ bottomText }}</p>

        <footer v-if="lastSection">
            <a>Tesla © 2023</a>
            <a>Privacy & Legal</a>
            <a>Contact</a>
            <a>News</a>
            <a>Get Updates</a>
            <a>Locations</a>
        </footer>
    </div>
</template>

<style scoped>
.container {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
}

h1 {
    position: fixed;
    top: 6rem;
    color: rgb(15, 15, 15);
    font-weight: 600;
    font-size: 3em;
    text-align: center;
}

h3 {
    position: fixed;
    top: 10rem;
    color: rgb(23, 26, 32);
    font-weight: 400;
    line-height: 20px;
    text-align: center;
}

.button_container {
    bottom: 1rem;
    position: fixed;
    display: flex;
    justify-content: center;
    gap: 1rem;
}

span {
    color: rgb(15, 15, 15);
    font-weight: 500;
    background-color: rgb(232, 232, 232);
    padding: 0.5rem 5rem;
    border: none;
    border-radius: 5px;
    text-align: center;
    transition: opacity 0.5s;
    margin-bottom: 4rem;
}

span:hover {
    cursor: pointer;
}

#button_dark {
    background-color: rgb(23, 26, 32, 0.8);
    color: white;

}

.button_container {
    display: flex;
}

p {
    position: fixed;
    bottom: 1rem;
    color: rgb(15, 15, 15);
    font-size: 12px;
    font-weight: 400;
    line-height: 18px;
}

footer {
    position: fixed;
    bottom: 1.5rem;
    display: flex;
    gap: 1rem;
}

a {
    text-decoration: none;
    color: rgb(208, 209, 210);
    font-size: 12px;
    font-weight: 500;
    line-height: 20px;
}

a:hover {
    cursor: pointer;
}

@media (width < 768px) {

    h1 {
        margin-top: 0rem;
        line-height: 1;

    }

    h3 {
        margin-top: 2rem;
    }

    p {
        bottom: 0.3rem;
    }

    .button_container {
        gap: 0;
        bottom: 1.5rem;
        flex-direction: column;
    }

    span {
        margin-bottom: 0.5rem;
    }

    footer {
        margin: 0.2rem;
        position: static;
        width: 100%;
        text-align: center;
        background-color: rgba(0, 0, 0, 0.482);
        display: flex;
        flex-direction: column;
        gap: 0.1rem;
    }
}
</style>