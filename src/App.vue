<template>
    <div id="app">
        <div class="container" @mousemove='getCoordinates($event)'>
            <div class="layer6" v-bind:style="{ transform: translate3d(-40) }">
                <img src="@/assets/layer6.png" alt="">
            </div>
            <div class="layer5" v-bind:style="{ transform: translate3d(-50) }">
                <img src="@/assets/layer5.png" alt="">
            </div>
            <div class="layer4" v-bind:style="{ transform: translate3d(-70) }">
                <img src="@/assets/layer4.png" alt="">
            </div>
            <div class="layer3" v-bind:style="{ transform: translate3d(-90) }">
                <img src="@/assets/layer3.png" alt="">
            </div>
            <div class="layer2" v-bind:style="{ transform: translate3d(-110) }">
                <img src="@/assets/layer2.png" alt="">
            </div>
            <div class="layer1" v-bind:style="{ transform: translate3d(-130) }">
                    <img src="@/assets/layer1.png" alt="">
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data(){
            return {
                x: null,
                y: null
            }
        },
        methods: {
            getCoordinates(event){
                this.x = event.clientX
                this.y = event.clientY
            },
            translate3d(depth) {
                let translateX = (this.x * depth / 1920 - depth / 2 ) + 'px'
                let translateY = (this.y * depth / 2 / 880 - depth / 4) + 'px'
                let translate3d = "translate3d(" + translateX + ", " + translateY + ", 0px)"

                return translate3d
            }
        }
    }
</script>

<style>
    *, *:after, *:before {
        margin: 0;
        padding: 0;
        -webkit-box-sizing: border-box;
        box-sizing: border-box;
    }
    body {
        background-color: #0f1317;
        color: white;
    }
    img {
        transform: scale(0.7);
    }
    .container {
        position: relative;
        height: 100vh;
        width: 100vw;
        display: flex;
        justify-content: center;
        overflow: hidden;
    }
    .layer6, .layer5, .layer4, .layer3, .layer2, .layer1 {
        position: absolute;
        bottom: -80px;
    }
    .layer1 {
        bottom: -80px;
    },
    .layer2 {

    }
    .layer3 {

    }
    .layer4 {
        bottom: -100px;
    }
    .layer5 {
        bottom: -80px;
    }
    .layer6 {
        bottom: -20px;
    }
</style>
