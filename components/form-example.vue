<template>
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
                    <mu-col span="12"></mu-col>
                </mu-row>
            </mu-dialog>

    </mu-container>
</template>

<style>
    .red-color {
        color:#F00708;
    }
</style>

<script>
export default {
    data() {
        return {
            openAlert: false,
            openValidate: false,

            // form part
            options: [
                {
                    key: 'key 1',
                    label: 'option 1',
                    value: 1
                }, {
                    key: 'key 2',
                    label: 'option 2',
                    value: 2
                }, {
                    key: 'key 3',
                    label: 'option 3',
                    value: 3
                }, {
                    key: 'key 4',
                    label: 'option 4',
                    value: 4
                },
                {
                    key: 'key 5',
                    label: 'option 5',
                    value: 5
                }, {
                    key: 'key 6',
                    label: 'option 6',
                    value: 6
                }, {
                    key: 'key 7',
                    label: 'option 7',
                    value: 7
                }, {
                    key: 'key 8',
                    label: 'option 8',
                    value: 8
                },
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
            loading: false
        }
    },
    methods: {
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
            this.$toast.warning('使用者取消');
        },
        async submit() {
            this.loading = this.$loading();

            this.loading.close();

            var {result, value} = await this.$alert(JSON.stringify(this.form), 'alert title', {
                type: 'success'
            });
            this.$toast.info('修改成功!');

            this.closeAlertDialog();
        }
    },
    mounted() {
        window.form_vm = this;
    }
};
</script>
<style>
.mu-demo-form {
  width: 100%;
  max-width: 460px;
}
</style>