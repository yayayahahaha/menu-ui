<template>
    <div>
        <!-- 小圖示檔案 -->
        <link rel="stylesheet" href="https://cdn.bootcss.com/material-design-icons/3.0.1/iconfont/material-icons.css">

        <layout-example></layout-example>
        <transition-example></transition-example>
        <message-example></message-example>
        <loading-example></loading-example>
        <form-example></form-example>
        <multi-select-example></multi-select-example>
    </div>
</template>

<style scoped>
</style>

<script>
    import Vue from 'vue';
    import MuseUI from 'muse-ui';
    import Message from 'muse-ui-message';
    import Toast from 'muse-ui-toast';
    import Loading from 'muse-ui-loading';

    import 'muse-ui-loading/dist/muse-ui-loading.css'; // load css
    import 'muse-ui-message/dist/muse-ui-message.css'; // message css
    import 'muse-ui/dist/muse-ui.css';

    Vue.use(Toast);
    Vue.use(Message);
    Vue.use(MuseUI);
    Vue.use(Loading);

    //

    import LayoutExample from '~/components/layout-example'
    import TransitionExample from '~/components/transition-example'
    import MessageExample from '~/components/message-example'
    import LoadingExample from '~/components/loading-example'

    import FormExample from '~/components/form-example'

    import multiSelectExample from '~/components/multi-select-example'

    export default {
        components: {
            LayoutExample,
            TransitionExample,
            MessageExample,
            LoadingExample,
            FormExample,
            multiSelectExample
        },
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
        },
        mounted() {
            window.vm = this;
        }
    }
</script>