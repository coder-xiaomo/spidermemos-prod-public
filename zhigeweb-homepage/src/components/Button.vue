<script>
export default {
    // refer: https://cn.vuejs.org/guide/components/props.html#prop-validation
    props: {
        // dark / light / black
        type: { type: String, default: 'light' },
        // 是否渐变 (浅色按钮边框不支持渐变 / 黑色按钮不支持渐变)
        gradient: { type: Boolean, default: false },
        text: { type: String, default: '按钮' },
        // width: { type: Number, default: 110 },
        // height: { type: Number, default: 38 },
    },

    computed: {
        buttonStyle() {
            return {
                // width: `${this.width}px`,
                // height: `${this.height}px`,
            };
        }
    }
}
</script>

<template>
    <div class="btn" :class="[type, { gradient: gradient }]" :style="buttonStyle">
        <span class="btn-text">{{ text }}</span>
    </div>
</template>

<style scoped>
.btn {
    --light-color: #FFFFFF;
    --theme-color: #000000;
    --dark-color: #8A4AFF;
    --dark-color: #7e0cff;
    /* 深 偏亮 */
    --dark-color: #7735f0;
    --dark-color: #6801F9;
    --dark-color-button-background-hover: #9537ff;
    /* --dark-color-button-background-hover: #7e0cff; */
    --dark-color-button-text-hover: #a557ff;

    --border-radius: 6px;

    font-size: 20px;
    letter-spacing: 1px;
    padding: 3.8px 21px 2.5px;
    border-radius: var(--border-radius);

    display: inline-grid;
    place-items: center;

    cursor: pointer;
    user-select: none;
    transition: background-color .4s, color .3s, border-color .3s, transform .15s;
    transform: none;
}

/* 按钮点击动效 */
.btn:active {
    transform: scale(1.03) skew(-1deg, -1deg);
}

/* 浅色纯色按钮 */
.btn.light {
    border-style: solid;
    border-width: 1px;

    background-color: var(--light-color);
    border-color: var(--dark-color);
    color: var(--dark-color);
}

.btn.light:hover {
    color: var(--dark-color-button-text-hover);
    border-color: var(--dark-color-button-text-hover);
}

/* 深色纯色按钮 */
.btn.dark {
    /* 深色按钮没有边框 padding整体加上border宽度 */
    border: none;
    padding: 4.8px 22px 3.5px;

    background-color: var(--dark-color);
    border-color: var(--dark-color);
    color: var(--light-color);
}

.btn.dark:hover {
    background-color: var(--dark-color-button-background-hover);
}

/* 浅色渐变色按钮 */
.btn.gradient.light .btn-text {
    background-image: var(--gradient);
    background-clip: text;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;

    transition: all .4s;
    background-size: 200%;
    background-position: 50% 50%;
}

.btn.gradient.light:hover .btn-text {
    background-position: 0 0;
}

/* 深色渐变色按钮 */
.btn.gradient.dark {
    background-image: var(--gradient);

    /* refer: https://www.76339.cn/css/2990.html */
    transition: background-position .4s, transform .15s;
    background-size: 200%;
    background-position: 50% 50%;
}

.btn.gradient.dark:hover {
    background-position: 0 0;
}
</style>
