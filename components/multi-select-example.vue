<template>
    <mu-container>
      <mu-row gutter>
        <mu-col span="12" lg="4" sm="6">
          <mu-select label="Filerable Select" filterable v-model="filterable.value1" full-width>
            <mu-option v-for="city,index in nameList" :key="city" :label="city" :value="city"></mu-option>
          </mu-select>
        </mu-col>
        <mu-col span="12" lg="4" sm="6">
          <mu-select label="Multi Filerable Select" filterable multiple v-model="filterable.value2" full-width>
            <mu-option v-for="city,index in nameList" :key="city" :label="city" :value="city"></mu-option>
          </mu-select>
        </mu-col>
        <mu-col span="12" lg="4" sm="6">
          <mu-select label="Use Chips Filterable" filterable multiple chips v-model="filterable.value3" full-width>
            <mu-option v-for="city,index in nameList" :key="city" :label="city" :value="city"></mu-option>
          </mu-select>
        </mu-col>
      </mu-row>
    </mu-container>
</template>

<script>
    import { fake as fakeData } from '@/components/fake'

    export default {
        data() {
            return {
                nameList: [],
                city: '',
                filterable: {
                    value1: '',
                    value2: [],
                    value3: []
                }
            };
        },
        methods: {
            async getFake() {
                var [data, error] = await (() => {
                    return new Promise((resolve, reject) => {
                        setTimeout(() => {
                            resolve([fakeData, null])
                        }, 300);
                    });
                })();

                if (error) {
                    return;
                }
                this.nameList = fakeData;
            }
        },
        mounted() {
            window.multi = this;
            this.getFake();
        }
    };
</script>