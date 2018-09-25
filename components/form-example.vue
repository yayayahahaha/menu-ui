<template>
    <mu-container>
        <mu-expansion-panel>
            <div slot="header">基本表單</div>
            <mu-container>
                <!-- 一般的表單 -->
                <mu-button class="red-color" color="#0C0A3C" @click="openAlertDialog">一般的表單</mu-button>
                <mu-dialog
                    title=""
                    width="600"
                    max-width="80%"
                    :esc-press-close="false"
                    :overlay-close="false"
                    :open.sync="openAlert"
                    scrollable>
                    <mu-row>
                        <mu-col>
                            <mu-container>
                                <mu-flex align-items="center" style="padding-bottom: 8px;">
                                    <span style="margin-right: 16px;">Label Position:</span>
                                    <mu-radio v-model="labelPosition" style="margin-right: 16px;" value="top" label="Top"></mu-radio>
                                    <mu-radio v-model="labelPosition" style="margin-right: 16px;" value="left" label="Left"></mu-radio>
                                    <mu-radio v-model="labelPosition" style="margin-right: 16px;" value="right" label="Right"></mu-radio>
                                </mu-flex>

                              <mu-form :model="form" class="mu-demo-form" :label-position="labelPosition" label-width="100">
                                <mu-form-item prop="input" label="Input">
                                    <mu-text-field v-model="form.input"></mu-text-field>
                                </mu-form-item>
                                <mu-form-item prop="select" label="Select">
                                    <mu-select v-model="form.select">
                                        <mu-option v-for="option,index in options" :key="option.key" :label="option.label" :value="option.value"></mu-option>
                                    </mu-select>
                                </mu-form-item>
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
                    <mu-button slot="actions" flat color="primary" @click="closeAlertDialog">Disagree</mu-button>
                    <mu-button slot="actions" flat color="primary" @click="submit">Agree</mu-button>
                </mu-dialog>

                <!-- 有驗證的表單 -->
                <mu-button color="#F00708" @click="openValidateDialog">表單驗證</mu-button>
                <mu-dialog
                    title=""
                    width="600"
                    max-width="80%"
                    :esc-press-close="true"
                    :overlay-close="true"
                    :open.sync="openValidate"
                    scrollable>
                        <mu-row>
                            <mu-col span="12">
                                <mu-container>
                                  <mu-form ref="validate-form" :model="validateForm" class="mu-demo-form">
                                    <mu-form-item label="用户名" help-text="帮助文字" prop="username" :rules="usernameRules">
                                      <mu-text-field v-model="validateForm.username" prop="username" @keyup.enter="validateSubmit"></mu-text-field>
                                    </mu-form-item>
                                    <mu-form-item label="密码" prop="password" :rules="passwordRules">
                                        <mu-text-field type="password" v-model="validateForm.password" prop="password" @keyup.enter="validateSubmit"></mu-text-field>
                                    </mu-form-item>
                                    <mu-form-item prop="isAgree" :rules="argeeRules">
                                      <mu-checkbox label="同意用户协议" v-model="validateForm.isAgree"></mu-checkbox>
                                    </mu-form-item>
                                    <mu-form-item prop="date" label="Date Time" :rules="dateRules">
                                        <mu-date-input v-model="validateForm.date" type="dateTime" actions></mu-date-input>
                                    </mu-form-item>
                                    <mu-form-item>
                                      <mu-button color="primary" @click="validateSubmit">提交</mu-button>
                                      <mu-button @click="clearValidateForm">重置</mu-button>
                                    </mu-form-item>
                                  </mu-form>
                                </mu-container>
                            </mu-col>
                        </mu-row>
                    </mu-dialog>

                <!-- 自動補齊 -->
                <mu-button color="#0C0A3C" @click="openAutoDialog">自動補齊</mu-button>
                <mu-dialog
                    :open.sync="openAuto">
                        <mu-container>
                            <mu-row>
                                <mu-col>
                                    <mu-auto-complete :data="nameList" label="自動補齊測試" v-model="autoName"></mu-auto-complete>
                                </mu-col>
                            </mu-row>
                        </mu-container>
                    </mu-dialog>
            </mu-container>
        </mu-expansion-panel>
    </mu-container>
</template>

<style>
    .red-color {
        color:#F00708;
    }
</style>

<script>
import { fake as fakeData } from '@/components/fake'

export default {
    data() {
        return {
            openAlert: false,
            openValidate: false,
            openAuto: false,

            // form part
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
            labelPosition: 'top',
            form: {
                input: '',
                select: '',
                date: '',
                radio: '',
                checkbox: [],
                switch: false,
                slider: 30,
                textarea: ''
            },
            loading: false,

            validateForm: {
                username: '',
                password: '',
                date: '',
                isAgree: false
            },
            usernameRules: [{
                validate(value, validateForm) {
                    return value === 'hello'
                },
                message: '請輸入 hello'
            }],
            dateRules: [{
                validate(value) {
                    return !!value;
                },
                message: '時間什麼的'
            }],
            passwordRules: [{
                validate(value, validateForm) {
                    return value !== validateForm.username;
                },
                message: '密碼不可和帳號相同'
            }],
            argeeRules: [{
                validate(value, validateForm) {
                    return value;
                },
                message: '這是一定要點的吧'
            }],

            nameList: [],
            autoName: ''
        }
    },
    methods: {
        openAutoDialog() {
            this.openAuto = true;
        },
        closeAutoDialog() {
            this.openAuto = false;
        },
        openValidateDialog() {
            this.openValidate = true;
        },
        closeValidateDialog() {
            this.openValidate = false;
        },
        openAlertDialog() {
            this.openAlert = true;
        },
        closeAlertDialog() {
            this.openAlert = false;
        },
        async submit() {
            this.loading = this.$loading();
            this.loading.close();

            var {result, value} = await this.$alert(JSON.stringify(this.form), 'alert title', {
                type: 'success'
            });
            this.$toast.info('修改成功!');

            this.closeAlertDialog();
        },

        async validateSubmit() {
            var pass = await this.$refs['validate-form'].validate().then((pass) => {
                return pass;
            });
            if (pass) {
                this.$alert('pass!').then(() => {
                    this.openValidate = false;
                });
            }
        },
        clearValidateForm() {
            this.$refs['validate-form'].clear();
            this.validateForm.username = '';
            this.validateForm.password = '';
            this.validateForm.isAgree = false;
            this.validateForm.date = '';
        },

        async getFakeData() {
            var [data, error] = await (() => {
                return new Promise((resolve) => {
                    setTimeout(() => {
                        resolve([fakeData, null]);
                    }, 300);
                });
            })();
            if (error) {
                return;
            }
            this.nameList = data;
        }
    },
    mounted() {
        window.form_vm = this;
        this.getFakeData();
    }
};
</script>
<style>
.mu-demo-form {
  width: 100%;
  max-width: 460px;
}
</style>