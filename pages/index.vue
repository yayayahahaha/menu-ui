<template>
    <div>
        <mu-container>
            <mu-expansion-panel>
                <div slot="header">Layout</div>
                <mu-card>
                    <mu-card-header title="這裡是卡片的頭" sub-title="卡片的小標">
                    </mu-card-header>
                    <mu-card-title title="卡片的身體" sub-title="卡片身體的小標"></mu-card-title>
                    <mu-card-text>
                        <p>卡片內文</p>
                    </mu-card-text>
                    <mu-card-actions>
                        <mu-flex align-items="center">
                            <mu-flex justify-content="center">
                                <mu-button color="red">f</mu-button>
                            </mu-flex>
                            <mu-flex justify-content="center">
                                <mu-button color="blue">l</mu-button>
                            </mu-flex>
                            <mu-flex justify-content="center">
                                <mu-button color="green">e</mu-button>
                            </mu-flex>
                            <mu-flex justify-content="center">
                                <mu-button color="yellow">x</mu-button>
                            </mu-flex>
                        </mu-flex>
                        <mu-row>
                            <mu-col span="1">
                                <mu-button color="black">g</mu-button>
                            </mu-col>
                            <mu-col span="1">
                                <mu-button color="gray">r</mu-button>
                            </mu-col>
                            <mu-col span="1">
                                <mu-button color="#ff0063">i</mu-button>
                            </mu-col>
                            <mu-col span="1">
                                <mu-button color="#123">d</mu-button>
                            </mu-col>
                        </mu-row>
                        <mu-row gutter>
                          <mu-col align-self="center">
                              <mu-button color="#123">gutter</mu-button>
                          </mu-col>
                          <mu-col align-self="center">
                              <mu-button color="#456">gutter</mu-button>
                          </mu-col>
                          <mu-col align-self="center">
                              <mu-button color="#789">gutter</mu-button>
                          </mu-col>
                          <mu-col align-self="center">
                              <mu-button color="#abc">gutter</mu-button>
                          </mu-col>
                          <mu-col align-self="center">
                              <mu-button color="#def">gutter</mu-button>
                          </mu-col>
                        </mu-row>
                    </mu-card-actions>
                </mu-card>
            </mu-expansion-panel>
        </mu-container>
    </div>
</template>

<style scoped>
</style>

<script>
    import Vue from 'vue';
    import MuseUI from 'muse-ui';
    import Message from 'muse-ui-message';
    import Toast from 'muse-ui-toast';

    import 'muse-ui-message/dist/muse-ui-message.css';
    import 'muse-ui/dist/muse-ui.css';

    Vue.use(Toast);
    Vue.use(Message);
    Vue.use(MuseUI);

    export default {
        asyncData(context) {
            return new Promise((resolve, reject) => {
                setTimeout(() => {
                    resolve({
                        msg: 'hello',
                        context: [1, 2, 3, 4, 5, 6, 7, 8, 9]
                    })
                }, 100);
            });
        },
        methods: {
            show() {
                this.$alert('Hello World', '提示', {
                  okLabel: '知道了'
                }).then(() => {
                  this.$toast.message('提示信息');
                });
            }
        },
        data() {
            return {
                msg: "Context Params"
            };
        }
    }
</script>