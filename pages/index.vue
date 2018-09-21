<template>
    <div>
        <layout-example></layout-example>
        <transition-example></transition-example>
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

    //

    import LayoutExample from '~/components/layout-example'
    import TransitionExample from '~/components/transition-example'

    export default {
        components: {
            LayoutExample,
            TransitionExample
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
        }
    }
</script>