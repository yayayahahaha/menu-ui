<template>
    <mu-container>
        <mu-expansion-panel>
            <div slot="header">提示訊息相關</div>

            <!-- toast -->
            <mu-flex>
                <mu-button class="demo-button" @click="$toast.message('Message Toast')" color="primary">
                    message toast
                </mu-button>
                <mu-button class="demo-button" @click="$toast.success('Success Toast')" color="success">
                    success toast
                </mu-button>
                <mu-button class="demo-button" @click="$toast.warning('Warning Toast')" color="warning">
                    warning toast
                </mu-button>
                <mu-button class="demo-button" @click="$toast.info('Info Toast')" color="info">
                    info toast
                </mu-button>
                <mu-button class="demo-button" @click="$toast.error('Error Toast')" color="error">
                    error toast
                </mu-button>
            </mu-flex>

            <!-- alert -->
            <mu-flex>
                <mu-button class="demo-button" color="brown" @click="alert()">Alert</mu-button>
                <mu-button class="demo-button" color="secondary" @click="confirm()">Confirm</mu-button>
                <mu-button class="demo-button" color="teal" @click="prompt()">Prompt</mu-button>
            </mu-flex>

        </mu-expansion-panel>
    </mu-container>
</template>

<script>
    export default {
        data() {
            return {
            }
        },
        methods: {
            async alert() {
                var {result, value} = await this.$alert('alert content', 'alert title', {
                    type: 'success'
                });
                this.$toast.info('result: ' + result);
            },
            async confirm() {
                var {result, value} = await this.$confirm('confirm content', 'confirm title', {
                    type: 'success'
                });
                this.$toast.info('result: ' + result);
            },
            async prompt() {
                var { result, value } = await this.$prompt('prompt', 'prompt title', {
                    transition: 'slide-left',
                    validator(value) {
                        var result = (() => {
                            return value === 'hello';
                        })();
                        return {
                            valid: result,
                            message: '請輸入 hello '
                        }
                    }
                });
                this.$toast.info('result: ' + result + ' value: ' + value);
            }
        }
    }
</script>