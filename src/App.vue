<template>
    <div id="app">
        <div class="container" @mousemove='getCoordinates($event)'>
            <div class="layer8" v-bind:style="{ width: this.width + 'px', height: this.width + 'px', marginBottom: -this.width/2 + 'px', transform: translate3d(-20) }">
                <div class="stars"></div>
                <div class="twinkling"></div>
            </div>
            <div class="layer7" v-bind:style="{ transform: translate3d(-30) }">
                <div class="moon-container" >
                    <img class='moon' src="@/assets/moon.svg" alt="Moon">
                    <img class='second-moon' src="@/assets/moon.svg" alt="Moon">
                </div>
            </div>
            <div class="layer6" v-bind:style="{ transform: translate3d(-40) }">
                <img src="@/assets/layer6.png" alt="Mountain">
            </div>
            <div class="layer5" v-bind:style="{ transform: translate3d(-50) }">
                <img src="@/assets/layer5.png" alt="Rocks">
            </div>
            <div class="layer4" v-bind:style="{ transform: translate3d(-70) }">
                <img src="@/assets/layer4.png" alt="Trees">
            </div>
            <div class="layer3" v-bind:style="{ transform: translate3d(-90) }">
                <img src="@/assets/layer3.png" alt="Trees">
            </div>
            <div class="layer2" v-bind:style="{ transform: translate3d(-110) }">
                <img src="@/assets/layer2.png" alt="Tower">
            </div>
            <div class="layer1" v-bind:style="{ transform: translate3d(-130) }">
                <img src="@/assets/layer1.png" alt="Trees">
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
                let translate3d;

                if (this.x === null) {
                    translate3d = "translate3d(0, 0, 0px)"
                } else {
                    let width = window.innerWidth
                    let height = window.innerHeight
                    let translateX = ( this.x * depth / width - depth / 2 )
                    let translateY = ( this.y * depth / 2 / height - depth / 4 )
                    translate3d = "translate3d(" + translateX + "px, " + translateY + "px, 0px)"
                }

                return translate3d
            }
        },
        computed: {
            width(){
                return window.innerWidth * 1.3
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
        background-color: #000;
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
    }
    .layer1 {
        bottom: -100px;
    }
    .layer2 {
        bottom: -60px;
    }
    .layer3 {
        bottom: -100px;
    }
    .layer4 {
        bottom: -120px;
    }
    .layer5 {
        bottom: -90px;
    }
    .layer6 {
        bottom: -20px;
    }
    .layer7 {
        position: relative;
        height: 100vh;
        width: 100vw;
        display: flex;
        justify-content: center;
        overflow: hidden;
    }
    .layer8 {
        position: absolute;
        bottom: 0;
    }
    .stars, .twinkling {
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        display: block;
    }
    .stars {
        background: #000 url("./assets/stars.png") repeat top center;
        animation: rotation 1000s infinite linear;
    }
    .twinkling{
        background: transparent url("./assets/twinkling.png") repeat top center;
        animation: move-twink-back 200s linear infinite, rotation 1000s infinite linear;
    }
    .moon-container {
        position: absolute;
        bottom: -50%;
        height: 100%;
        width: 70%;
        animation: rotation 480s infinite linear;
    }
    .moon, .second-moon {
        width: 50px;
        height: 50px;
        position: absolute;
    }
    .moon {
        left: 0;
    }
    .second-moon {
        right: 0;
        bottom: 0;
    }
    @keyframes move-twink-back {
        from {
            background-position: 0 0;
        }
        to {
            background-position: -10000px 5000px;
        }
    }
    @keyframes rotation {
        from {
            transform: rotate(0deg);
        }
        to {
            transform: rotate(359deg);
        }
    }
</style>
