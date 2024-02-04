<script setup lang="ts">
import spells from '../assets/data/spells.json'

export interface MyObj {
    [key: string]: any;
    "id": string,
    "name": string,
    "description": string,
}
</script>
<script lang="ts">
    export default {
    data() {
      return {
          spell: spells as MyObj[],
          numberOfColumns: 3,
      }
    },
    computed: {
        gridStyle() {
            return {
                gridTemplateColumns: `repeat(auto-fill, minmax(340px, 1fr)`
            }
        }
    },
    created() {
       this.spell = this.spell.map((item) => {
            return { ...item, isActive: false, };
       }) 
    }
  }
</script>
<template>
    <v-container class="py-3 fluid">
        <v-row class="fill-height overflow-y-auto">
            <v-col lg="4" md="5" sm="9" cols="12" v-for="item in spell">
                <v-sheet min-height="50px" class="fill-height" color="transparent">
                    <v-lazy
                        v-model="item.isActive" :options="{
                        threshold: .5
                        }"
                        class="fill-height">
                        <v-card
                            :key="item.id"
                            class="mx-auto my-8 hp-card"
                            >
                            <v-card-title class="text-h5 custom-font">
                                {{item.name}}
                            </v-card-title>
                            <v-card-text class="text-h6 custom-font">
                                {{item.description}}
                            </v-card-text>
                        </v-card>
                    </v-lazy>
                </v-sheet>
            </v-col>
        </v-row>
    </v-container>
</template>

<style>
.custom-font {
   font-family: 'BluuNextBoldItalic', serif;
   color: #e8e6e3;
}
.hp-card {
    background: #191b1c
}
.card { border-radius: 8px; box-shadow: 0 4px 10px rgba(0,0,0,.15); -webkit-box-shadow: 0 4px 10px rgba(0,0,0,.15); -moz-box-shadow: 0 4px 10px rgba(0,0,0,.15); background-color: #F1E6BA;}
.card-topper { border-top-right-radius: 8px; border-top-left-radius: 8px; padding: 8px 16px; font-size: 2em; font-weight: 600; text-align: center; background-color: #312823; color: #ffffff;}
.pic { max-width: 270px; max-height: 200px; padding-bottom: 1em; width: auto; height: auto;}
.titles {font-family: serif;}
#test { border: 2px solid black;}
#test td { border: 1px solid black;}
.table-responsive { overflow-x: unset; }
</style>

