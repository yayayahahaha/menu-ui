<template>
    <div>
        <h1 v-text="msg"></h1>
        <p v-for="item in context" v-text='item'></p>
    </div>
</template>

<style scoped>
    /* some scoped css */
</style>

<script>
    import axios from "axios";
    import MuseUI from 'muse-ui';
    import 'muse-ui/dist/muse-ui.css';

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
        data() {
            return {
                msg: "Context Params"
            };
        }
    }
</script>