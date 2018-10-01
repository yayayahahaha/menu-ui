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
                                label-position="left">

                                <mu-container>
                                    <mu-row>
                                        <mu-col span="3">
                                            <mu-form-item prop="input" label="輸入輸入輸入輸入">
                                                <mu-text-field></mu-text-field>
                                            </mu-form-item>
                                        </mu-col>
                                        <mu-col span="4">
                                          <mu-date-input v-model="date_picker" label="横屏显示" label-float full-width landscape></mu-date-input>
                                        </mu-col>
                                        <mu-col span="4">
                                          <mu-date-input v-model="date_picker" label="隐藏日期展示" label-float full-width no-display></mu-date-input>
                                        </mu-col>
                                    </mu-row>
                                    <mu-row>
                                        <mu-col span="3">
                                            <mu-form-item prop="input" label="輸入輸入輸入輸入">
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
                                    <mu-row>
                                        <mu-col span="12">
                                           <mu-select label="Use Chips Filterable" filterable multiple chips v-model="filterable.value3" full-width>
                                             <mu-option v-for="city,index in computedFakeData" :key="city.key" :label="city.label" :value="city.value"></mu-option>
                                           </mu-select>
                                         </mu-col>
                                    </mu-row>
                                    <mu-row>
                                        <mu-col>
                                            <mu-form-item prop="radio" label="hello">
                                                <mu-radio
                                                    style="margin-right: 1rem;"
                                                    :label="'radio-1'"
                                                    value="radio-1"
                                                    v-model="radio"></mu-radio>
                                                <mu-radio
                                                    style="margin-right: 1rem;"
                                                    :label="'radio-2'"
                                                    value="radio-2"
                                                    v-model="radio"></mu-radio>
                                                <mu-radio
                                                    style="margin-right: 1rem;"
                                                    :label="'radio-3'"
                                                    value="radio-3"
                                                    v-model="radio"></mu-radio>
                                            </mu-form-item>
                                        </mu-col>
                                        <mu-col>
                                            <mu-form-item prop="input" label="Input">
                                                <mu-text-field v-model="form.color" suffix="hello" :action-icon="'shopping_cart '">
                                                    <div slot="prepend">prepend-prepend</div>
                                                    <div slot="append">append-append</div>
                                                </mu-text-field>
                                            </mu-form-item>
                                        </mu-col>
                                    </mu-row>
                                    <mu-divider solo full-width></mu-divider>
                                    <mu-row style="margin-top: 1rem;">
                                        <mu-col span="1" offset="11">
                                            <mu-button>hello</mu-button>
                                        </mu-col>
                                    </mu-row>
                                </mu-container>
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

    import { fake as fakeData } from '@/components/fake'

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
        computed: {
            computedFakeData() {
                return fakeData.map((item, index) => {
                    return {
                        key: `${index}_${item}`,
                        label: item,
                        value: item
                    };
                });
            }
        },
        data() {
            return {
                date_picker: '',
                drawerObject: {
                    open: false,
                    openMenu: false
                },
                form: {
                    input: '',
                    color: ''
                },
                filterable: {
                    value3: []
                },
                radio: 'radio-2',
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