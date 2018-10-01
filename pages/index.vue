<template>
    <div>
        <!-- 小圖示檔案 -->
        <link rel="stylesheet" href="https://cdn.bootcss.com/material-design-icons/3.0.1/iconfont/material-icons.css">

        <mu-appbar style="width: 100%;" color="primary">
          <mu-button icon slot="left" @click="drawerObject.open = !drawerObject.open">
            <mu-icon value="menu"></mu-icon>
          </mu-button>

          Muse UI 展示
          <no-ssr>
            <mu-menu placement="bottom-start">
                <mu-button color="primary">Open On Hover</mu-button>
                <mu-list slot="content">
                <mu-list-item button>
                    <mu-menu placement="bottom-start">
                        <mu-button color="primary">Open On Hover</mu-button>
                        <mu-list slot="content">
                        <mu-list-item button>
                            <mu-list-item-title>Refresh</mu-list-item-title>
                        </mu-list-item>
                        </mu-list>
                    </mu-menu>
                </mu-list-item>
                </mu-list>
            </mu-menu>
          </no-ssr>


          <mu-button flat slot="right">我是按鈕</mu-button>
        </mu-appbar>
        <mu-drawer :open.sync="drawerObject.open" :docked="true" :right="true">
          <mu-list>
            <mu-list-item button>
              <mu-list-item-title>Menu Item 1</mu-list-item-title>
            </mu-list-item>
            <mu-list-item button>
              <mu-list-item-title>Menu Item 2</mu-list-item-title>
            </mu-list-item>
            <mu-list-item  @click="drawerObject.open = false" button>
              <mu-list-item-title>Close</mu-list-item-title>
            </mu-list-item>
          </mu-list>
        </mu-drawer>

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
        },
        data() {
            return {
                drawerObject: {
                    open: false,
                    openMenu: false
                }
            };
        },
        mounted() {
            window.vm = this;
        }
    }
</script>