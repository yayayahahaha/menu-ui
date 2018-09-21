<template>
    <mu-container>
        <mu-expansion-panel>
            <div slot="header">過度動畫</div>
            <mu-container>

                <!-- fade -->
                <mu-button @click="fade_show = !fade_show" color="#ff0063">Fade</mu-button>
                <mu-flex>
                    <mu-fade-transition>
                        <mu-card v-show="fade_show">
                            <mu-card-title title="card-title" sub-title="card-sub-title"></mu-card-title>
                            <mu-card-header title="card-header-title" sub-title="card-header-sub-title"></mu-card-header>
                        </mu-card>
                    </mu-fade-transition>
                </mu-flex>

                <!-- slide -->
                <mu-button @click="slide_show = !slide_show" color="#ff0063">Slide Left</mu-button>
                <mu-flex>
                    <mu-slide-top-transition>
                        <mu-card v-show="slide_show">
                            <mu-card-title title="card-slide-title"></mu-card-title>
                        </mu-card>
                    </mu-slide-top-transition>
                    <mu-slide-right-transition>
                        <mu-card v-show="slide_show">
                            <mu-card-title title="card-slide-title"></mu-card-title>
                        </mu-card>
                    </mu-slide-right-transition>
                </mu-flex>
                <mu-flex>
                    <mu-slide-left-transition>
                        <mu-card v-show="slide_show">
                            <mu-card-title title="card-slide-title"></mu-card-title>
                        </mu-card>
                    </mu-slide-left-transition>
                    <mu-slide-bottom-transition>
                        <mu-card v-show="slide_show">
                            <mu-card-title title="card-slide-title"></mu-card-title>
                        </mu-card>
                    </mu-slide-bottom-transition>
                </mu-flex>

                <!-- expand -->
                <mu-button @click="expand_show = !expand_show" color="#6300ff">Expand</mu-button>
                <mu-flex>
                    <mu-expand-transition>
                        <mu-card v-show="expand_show">
                            <mu-card-title title="card-expand-title"></mu-card-title>
                        </mu-card>
                    </mu-expand-transition>
                </mu-flex>

                <!-- scale -->
                <mu-button @click="scale_show = !scale_show" color="#00ff63">Scale</mu-button>
                <mu-flex>
                    <mu-scale-transition>
                        <mu-card v-show="scale_show">
                            <mu-card-title title="card-scale-title"></mu-card-title>
                        </mu-card>
                    </mu-scale-transition>
                </mu-flex>
            </mu-container>
        </mu-expansion-panel>
    </mu-container>
</template>

<script>
    export default {
        data() {
            return {
                fade_show: false,
                slide_show: false,
                expand_show: false,
                scale_show: false
            }
        },
        methods: {
        },
        mounted() {}
    }
</script>