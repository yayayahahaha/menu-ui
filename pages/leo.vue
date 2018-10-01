<template>
    <div>
        <!-- 小圖示檔案 -->
        <link rel="stylesheet" href="https://cdn.bootcss.com/material-design-icons/3.0.1/iconfont/material-icons.css">

        <mu-container>
            <mu-expansion-panel :expand="true">
                <div slot="header">
                    <h1><mu-icon value="menu"></mu-icon>hello</h1>
                </div>

                <mu-container>
                    <mu-row>
                        <mu-col>
                            <mu-container>
                              <mu-form
                                :model="form"
                                class="mu-demo-form"
                                label-position="left"
                                style="outline: 1px solid red;">

                                <mu-container>
                                    <mu-row>
                                        <mu-col span="3">
                                            <mu-form-item prop="checkbox" label="輸入輸入輸入輸入">
                                                <mu-text-field></mu-text-field>
                                            </mu-form-item>
                                        </mu-col>
                                        <mu-col span="3">
                                            <mu-form-item prop="input" label="輸入輸入輸入輸入">
                                                <mu-text-field v-model="form.input"></mu-text-field>
                                            </mu-form-item>
                                        </mu-col>
                                        <mu-col span="3">
                                            <mu-form-item prop="input" label="輸入輸入輸入輸入">
                                                <mu-text-field v-model="form.input"></mu-text-field>
                                            </mu-form-item>
                                        </mu-col>
                                        <mu-col span="3">
                                            <mu-form-item prop="input" label="輸入輸入輸入輸入">
                                                <mu-text-field v-model="form.input"></mu-text-field>
                                            </mu-form-item>
                                        </mu-col>
                                    </mu-row>
                                    <mu-row>
                                        <mu-col span="3">
                                            <mu-form-item prop="select" label="Select">
                                                <mu-select v-model="form.select">
                                                    <mu-option v-for="option,index in options" :key="option.key" :label="option.label" :value="option.value"></mu-option>
                                                </mu-select>
                                            </mu-form-item>
                                        </mu-col>
                                        <mu-col span="3">
                                            <mu-form-item prop="input" label="">
                                                <mu-text-field v-model="form.input"></mu-text-field>
                                            </mu-form-item>
                                        </mu-col>
                                    </mu-row>
                                </mu-container>

                                <mu-form-item prop="date" label="Date Time">
                                    <mu-date-input v-model="form.date" type="dateTime" actions></mu-date-input>
                                </mu-form-item>
                                <mu-form-item prop="radio" label="Radio">
                                    <mu-radio v-model="form.radio" value="male" label="Male"></mu-radio>
                                    <mu-radio v-model="form.radio" value="female" label="Female"></mu-radio>
                                </mu-form-item>
                                <mu-form-item prop="checkbox" label="Checkbox">
                                    <mu-checkbox v-model="form.checkbox" value="eat" label="Eat"></mu-checkbox>
                                    <mu-checkbox v-model="form.checkbox" value="sleep" label="Sleep"></mu-checkbox>
                                    <mu-checkbox v-model="form.checkbox" value="run" label="Run"></mu-checkbox>
                                    <mu-checkbox v-model="form.checkbox" value="movie" label="Movie"></mu-checkbox>
                                </mu-form-item>
                                <mu-form-item prop="switch" label="Switch">
                                    <mu-switch v-model="form.switch"></mu-switch>
                                </mu-form-item>
                                <mu-form-item prop="slider" label="Slider">
                                    <mu-slider v-model="form.slider"></mu-slider>
                                </mu-form-item>
                                <mu-form-item prop="textarea" label="Textarea">
                                    <mu-text-field multi-line :rows="3" :rows-max="6" v-model="form.textarea"></mu-text-field>
                                </mu-form-item>
                              </mu-form>
                            </mu-container>
                        </mu-col>
                    </mu-row>
                </mu-container>



            </mu-expansion-panel>
            <mu-expansion-panel :expand="true">
                <div slot="header">牛刀小試</div>
            </mu-expansion-panel>
        </mu-container>

    </div>
</template>

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
                },
                form: {},
                options: [
                    {
                        key: 'key 9',
                        label: 'option 9',
                        value: 9
                    }, {
                        key: 'key 10',
                        label: 'option 10',
                        value: 10
                    }
                ],
            };
        },
        mounted() {
            window.vm = this;
        }
    }
</script>