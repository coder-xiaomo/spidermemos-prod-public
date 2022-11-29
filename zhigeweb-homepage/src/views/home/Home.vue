<script setup>
import { ref, nextTick } from 'vue'

import WelcomeItem from '../../components/WelcomeItem.vue'
import FullScreenItem from '../../components/FullScreenItem.vue';
import BackgroundImage from '../../components/BackgroundImage.vue';
import Button from '../../components/Button.vue';
import FirstScreenTitle from './FirstScreenTitle.vue';
</script>

<template>
    <FullScreenItem>
        <BackgroundImage class="grid" src="./images/first-screen-background.svg">
            <div class="content">
                <FirstScreenTitle />
                <div>
                    <Button class="content-btn" type="dark" text="免费使用" />
                    <Button class="content-btn" type="light" text="共建社区" />
                    <Button class="content-btn" type="dark" :gradient="true" text="免费使用" />
                    <Button class="content-btn" type="light" :gradient="true" text="共建社区" />
                    <Button class="content-btn" type="black" text="免费使用" />
                    <Button class="content-btn" type="white" text="共建社区" />
                </div>
            </div>
        </BackgroundImage>
    </FullScreenItem>
    <WelcomeItem>
        <template #heading>Documentation</template>

        Vue’s
        <a href="https://vuejs.org/" target="_blank" rel="noopener">official documentation</a>
        provides you with all information you need to get started.
    </WelcomeItem>
</template>

<style scoped>
.grid {
    display: grid;
    height: 100%;
    place-items: center;
    text-align: center;
}

.content {
    height: 430px;
    height: 46vh;
}

.content .content-btn {
    /* top left-right bottom */
    margin: 25px 8px 0;
}
</style>
