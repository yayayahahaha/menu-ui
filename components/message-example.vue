<template>
    <mu-container>
        <mu-expansion-panel>
            <div slot="header">提示訊息相關</div>

            <mu-button class="demo-button" @click="$toast.message('Message')" color="primary">
                message
            </mu-button>
            <mu-button class="demo-button" @click="$toast.success('Success')" color="success">
                success
            </mu-button>
            <mu-button class="demo-button" @click="$toast.warning('Warning')" color="warning">
                warning
            </mu-button>
            <mu-button class="demo-button" @click="$toast.info('Info')" color="info">
                info
            </mu-button>
            <mu-button class="demo-button" @click="$toast.error('Error')" color="error">
                error
            </mu-button>

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
            alter() {
                console.log('alter');
            },
            toast() {
                console.log('toast');
            }
        },
        mounted() {
        }
    }
</script>