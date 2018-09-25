<template>
    <mu-container>
        <mu-button class="red-color" color="#0C0A3C" @click="openAlertDialog">Open Dialog</mu-button>
        <mu-dialog title="Use Google's location service?" width="600" max-width="80%" :esc-press-close="false" :overlay-close="false" :open.sync="openAlert">
        Let Google help apps determine location. This means sending anonymous location data to Google, even when no apps are running.
            <mu-button slot="actions" flat color="primary" @click="closeAlertDialog">Disagree</mu-button>
            <mu-button slot="actions" flat color="primary" @click="closeAlertDialog">Agree</mu-button>
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

            // form part
            options: [
                'Option 1', 'Option 2', 'Option 3', 'Option 4',
                'Option 5', 'Option 6', 'Option 7', 'Option 8',
                'Option 9', 'Option 10'
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
            }
        }
    },
    methods: {
        openAlertDialog() {
            this.openAlert = true;
        },
        closeAlertDialog() {
            this.openAlert = false;
        }
    }
};
</script>
<style>
.mu-demo-form {
  width: 100%;
  max-width: 460px;
}
</style>