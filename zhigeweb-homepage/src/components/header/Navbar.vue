<script setup>
import NavbarItem from './NavbarItem.vue';
</script>

<template>
        <div class="head_wrapper">
            <div class="head-item left-bar">
                <img alt="织个网" class="logo" src="../../assets/icons/logo.svg" />
            </div>
            <div class="head-item middle-bar">
                <NavbarItem class="item" text="首页" />
                <NavbarItem class="item" text="共建" />
                <NavbarItem class="item" text="帮助" />
            </div>
            <div class="head-item right-bar">
                <NavbarItem class="item" text="登录" />
                <span style="vertical-align: text-bottom; user-select: none;">/</span>
                <NavbarItem class="item" text="注册" />
            </div>
        </div>
</template>

<style scoped>
.head_wrapper {
    height: 100%;
    max-width: 960px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: 110px 1fr 110px;
    place-items: center;
}

.head-item {
    /* height: 100%; */
    /* display: inline-block; */
    vertical-align: middle;
}

.left-bar .logo {
    width: 110px;
    height: 100%;
    display: block;
}

.middle-bar .item {
    margin: 0 14px;
}

.right-bar .item {
    margin: 0 8px;
}
</style>
