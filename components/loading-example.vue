<template>
    <mu-container>
        <mu-expansion-panel>
            <div slot="header">載入動畫</div>
            <mu-container data-mu-loading-color="secondary" data-mu-loading-overlay-color="rgba(0, 0, 0, .7)" v-loading="loading2" class="demo-loading-wrap">
              <mu-button color="primary" @click="loading()">区域加载</mu-button>
              <mu-button color="secondary" v-loading="loading1" data-mu-loading-size="24" @click="loading1 = !loading1">按钮加载</mu-button>
              <mu-button color="teal" @click="fullscreen()">全屏加载</mu-button>
            </mu-container>
        </mu-expansion-panel>
    </mu-container>
</template>

<style>
    .demo-loading-wrap {
        outline: 1px solid red;
        height: 300px;
        position: relative;
    }
    .demo-loading-wrap .mu-button {
        margin: 6px 8px;
    }
</style>

<script>
    export default {
        data() {
            return {
                loading1: false,
                loading2: false
            };
        },
        methods: {
            loading() {
                this.loading2 = true;
                setTimeout(() => {
                    this.loading2 = false;
                }, 2000)
            },
            fullscreen() {
                const loading = this.$loading();
                setTimeout(() => {
                    loading.close();
                }, 2000)
            }
        }
    };
</script>