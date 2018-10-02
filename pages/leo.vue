<template>
    <div>
        <!-- 小圖示檔案 -->
        <link rel="stylesheet" href="https://cdn.bootcss.com/material-design-icons/3.0.1/iconfont/material-icons.css">

        <mu-container>
            <mu-appbar style="width: 100%;" color="primary">
                <mu-icon value="pan_tool"></mu-icon>
                Title

                <mu-button slot="right">點我</mu-button>
                <mu-button flat slot="right" @click="filter_show = !filter_show">
                    <mu-icon value="trending_down"></mu-icon>
                </mu-button>
            </mu-appbar>
            <mu-expand-transition>
                <mu-card v-show="filter_show">
                    <mu-card-text>
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
                                    </mu-container>
                                  </mu-form>
                                </mu-container>
                            </mu-col>
                        </mu-row>
                    </mu-card-text>
                    <mu-card-actions>
                        <mu-row>
                            <mu-col span="1" offset="11">
                                <mu-button color="blue">click!</mu-button>
                            </mu-col>
                        </mu-row>
                    </mu-card-actions>
                </mu-card>
            </mu-expand-transition>


            <mu-appbar style="width: 100%;" color="primary">
                <mu-icon value="pan_tool"></mu-icon>
                Title
                <mu-button flat slot="right" @click="result_show = !result_show">
                    <mu-icon value="trending_down"></mu-icon>
                </mu-button>
            </mu-appbar>
            <mu-expand-transition>
                <mu-card v-show="result_show">
                    <mu-card-header>
                        <mu-container>
                            <mu-row>
                                <mu-col span="1">
                                    <mu-button>Left</mu-button>
                                </mu-col>
                                <mu-col span="2" offset="9">
                                    <mu-row>
                                        <mu-col>
                                            <mu-button>Right</mu-button>
                                            <mu-button>Right</mu-button>
                                        </mu-col>
                                    </mu-row>
                                </mu-col>
                            </mu-row>
                        </mu-container>
                    </mu-card-header>

                    <mu-card-text>
                        <mu-container>
                          <mu-paper :z-depth="1">
                            <mu-data-table
                                border
                                :columns="columns"
                                :data="list">
                              <template slot-scope="scope">
                                <td>{{scope.row.name}}</td>
                                <td class="is-right">{{scope.row.calories}}</td>
                                <td class="is-right">{{scope.row.fat}}</td>
                                <td class="is-right">{{scope.row.carbs}}</td>
                                <td class="is-right">{{scope.row.protein}}</td>
                                <td class="is-right">{{scope.row.iron}}%</td>
                              </template>
                            </mu-data-table>
                          </mu-paper>
                        </mu-container>
                    </mu-card-text>

                    <mu-card-actions>
                    </mu-card-actions>
                </mu-card>
            </mu-expand-transition>
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

    import { fake as fakeData } from '@/components/fake'

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
                filter_show: false,
                result_show: true,
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
                options: [{
                    key: 'key 9',
                    label: 'option 9',
                    value: 9
                }, {
                    key: 'key 10',
                    label: 'option 10',
                    value: 10
                }],

                columns: [{
                    title: 'Dessert (100g serving)',
                    width: 200,
                    name: 'name'
                }, {
                    title: 'Calories',
                    name: 'calories',
                    align: 'center',
                    sortable: true
                }, {
                    title: 'Fat (g)',
                    name: 'fat',
                    align: 'center',
                    sortable: true
                }, {
                    title: 'Carbs (g)',
                    name: 'carbs',
                    align: 'center',
                    sortable: true
                }, {
                    title: 'Protein (g)',
                    name: 'protein',
                    align: 'center',
                    sortable: true
                }, {
                    title: 'Iron (%)',
                    name: 'iron',
                    align: 'center',
                    sortable: true
                }],
                list: [{
                    name: 'Frozen Yogurt',
                    calories: 159,
                    fat: 6.0,
                    carbs: 24,
                    protein: 4.0,
                    iron: 1
                }, {
                    name: 'Ice cream sandwich',
                    calories: 237,
                    fat: 9.0,
                    carbs: 37,
                    protein: 4.3,
                    iron: 1
                }, {
                    name: 'Eclair',
                    calories: 262,
                    fat: 16.0,
                    carbs: 23,
                    protein: 6.0,
                    iron: 7
                }, {
                    name: 'Cupcake',
                    calories: 305,
                    fat: 3.7,
                    carbs: 67,
                    protein: 4.3,
                    iron: 8
                }, {
                    name: 'Gingerbread',
                    calories: 356,
                    fat: 16.0,
                    carbs: 49,
                    protein: 3.9,
                    iron: 16
                }, {
                    name: 'Jelly bean',
                    calories: 375,
                    fat: 0.0,
                    carbs: 94,
                    protein: 0.0,
                    iron: 0
                }, {
                    name: 'Lollipop',
                    calories: 392,
                    fat: 0.2,
                    carbs: 98,
                    protein: 0,
                    iron: 2
                }, {
                    name: 'Honeycomb',
                    calories: 408,
                    fat: 3.2,
                    carbs: 87,
                    protein: 6.5,
                    iron: 45
                }, {
                    name: 'Donut',
                    calories: 452,
                    fat: 25.0,
                    carbs: 51,
                    protein: 4.9,
                    iron: 22
                }, {
                    name: 'KitKat',
                    calories: 518,
                    fat: 26.0,
                    carbs: 65,
                    protein: 7,
                    iron: 6
                }]
            };
        },
        mounted() {
            window.vm = this;
        }
    }
</script>