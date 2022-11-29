<script setup>
import { ref, nextTick } from 'vue'

const typeList = ['内容网络', '知识图谱', '1234']
const typer = ref(typeList[0])

async function typeWriter() {
    const spanTime = 3000; // 打完字之后 下一次打字开始前等待时间
    const typeTime = 400; // 每打完一个字停顿多久
    const deleteTime = 120; // 每删除一个字停顿多久

    async function sleep(interval) {
        await new Promise((resolve) => {
            // setTimeout(resolve, interval)
            let now = Date.now()
            nextTick(() => {
                let realInteval = interval - (Date.now() - now)
                if (realInteval < 1) resolve()
                setTimeout(resolve, realInteval)
            })
        })
    }

    async function typeWord(word) {
        await new Promise((resolve) => {
            for (let i = 0; i < word.length; i++) {
                setTimeout(() => {
                    // typer.value = word.substring(0, i + 1)
                    typer.value = word.substring(0, typer.value.length + 1)
                    if (i + 1 == word.length) resolve()
                }, typeTime * i);
            }
        })

        // let oldNow = Date.now(), newNow;
        // for (let i = 0; i < word.length; i++) {
        //     let j = i + 1
        //     typer.value = word.substring(0, j)
        //     console.log("typer.value", typer.value)
        //     oldNow = newNow
        //     await sleep(typeTime)
        //     newNow = Date.now()
        //     console.log("typeWord", newNow - oldNow, "参考值", typeTime)
        // }
    }

    async function deleteWord(word) {
        await new Promise((resolve) => {
            for (let i = 0; i < word.length; i++) {
                setTimeout(() => {
                    // typer.value = word.substring(0, word.length - (i + 1))
                    typer.value = word.substring(0, typer.value.length - 1)
                    if (i + 1 == word.length) resolve()
                }, deleteTime * i);
            }
        })

        // let oldNow = Date.now(), newNow;
        // for (let i = 0; i < word.length; i++) {
        //     let j = word.length - i - 1
        //     typer.value = word.substring(0, j)
        //     console.log("typer.value", typer.value)
        //     oldNow = newNow
        //     await sleep(deleteTime)
        //     newNow = Date.now()
        //     console.log("deleteWord", newNow - oldNow, "参考值", deleteTime)
        // }
    }

    let currentIndex = 0; // 当前在打数组中的第几个元素
    while (true) {
        // 停顿
        await sleep(spanTime)
        // console.log("停顿", "→", "删除文字")
        // 删除文字
        await deleteWord(typeList[currentIndex])
        // console.log("删除文字", "→", "")
        currentIndex = ++currentIndex % typeList.length
        // 停顿
        await sleep(200)
        // console.log(currentString, "→", "打字")
        // 打字
        await typeWord(typeList[currentIndex])
        // console.log("打字", "→", "停顿")
    }
}

// Windows下 Edge 浏览器
typeWriter()

// 测试 setTimeout 是否正常代码
// let inv = 50
// let temp = Date.now()
// function test() {
//     setTimeout(() => {
//         console.log("delta:", Date.now() - temp, "wish:", inv)
//         temp = Date.now()
//         test()
//     }, inv)
// }
// test()
</script>

<template>
    <h1 style="font-size: 90px; letter-spacing: 4px;" id="title">
        构建你的<span class="colorful">{{ typer }}</span>
    </h1>
    <h2 style="font-size: 20px; letter-spacing: 6px; color: grey; opacity: 0.7;">
        无限节点 · 无尽可能
    </h2>
</template>

<style scoped>
.colorful {
    --gradient: -webkit-linear-gradient(0deg, #ba32bf 5%, #3434ff);
    background-image: var(--gradient);
    background-clip: text;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;

    transition: background-position .4s, transform .15s;
    background-size: 160%;
    animation: animate 5s infinite linear;
}

#title::after {
    content: '|';
    font-family: initial;
    animation: blink 1000ms infinite;
    transition: none;
}

/* 模拟光标效果 */
@keyframes blink {

    0%,
    51%,
    100% {
        opacity: 0;
    }

    1%,
    50% {
        opacity: 1;
    }
}

/* 背景 */
@keyframes animate {

    0%,
    100% {
        background-position: left;
    }

    50% {
        background-position: right;
    }
}
</style>
