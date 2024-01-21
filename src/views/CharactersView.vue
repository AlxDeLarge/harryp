<script setup lang="ts">
import characters from '../assets/data/characters.json'

export interface MyObj {
    [key: string]: any;
    id: string;
    name: string;
    alternate_names: string[];
    species: string;
    gender: string;
    house: string;
    dateOfBirth: string;
    yearOfBirth: number;
    wizard: boolean;
    ancestry: string;
    eyeColour: string;
    hairColour: string;
    wand: wand;
    patronus: string;
    hogwartsStudent: boolean;
    hogwartsStaff: boolean;
    actor: string;
    alternate_actors: string[];
    alive: boolean;
    image: string;
}

export interface wand {
    wood: string;
    core: string;
    length: number;
}

</script>
<script lang="ts">
    export default {
    data() {
      return {
          char: characters as MyObj[],
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
       this.char = this.char.map((item) => {
            return { ...item, show: false, isActive: false, };
       }) 
    }
  }
</script>
<template>
    <v-container class="py-3 fluid">
        <v-row class="fill-height overflow-y-auto">
            <v-col lg="4" md="5" sm="9" cols="12" v-for="item in char">
                <v-sheet min-height="250px" class="fill-height" color="transparent">
                    <v-lazy
                        v-model="item.isActive" :options="{
                        threshold: .5
                        }"
                        class="fill-height">
                        <v-card
                            :key="item.id"
                            class="hp-card"
                            >
                            <v-layout align-center>
                                <v-img
                                    class="d-block mx-auto rounded"
                                    :src="item.image"
                                    max-height="200px"
                                    max-width="270px"
                                    contain
                                    padding-bottom="1em"
                                    width="auto"
                                    height="auto"
                                    ></v-img>
                            </v-layout>
                            <v-card-title class="text-h5 custom-font">
                                {{item.name}}
                            </v-card-title>
                            <v-card-subtitle class="text-h6 custom-font">
                                {{item.house}}
                            </v-card-subtitle>
                            <v-card-actions>
                                <v-btn
                                    color="orange-lighten-2"
                                    variant="text"
                                    >
                                    Explore
                                </v-btn>
                                    <v-spacer></v-spacer>
                                    <v-btn
                                        :icon="item.show ? 'mdi-chevron-up' : 'mdi-chevron-down'"
                                        @click="item.show = !item.show"
                                        ></v-btn>
                            </v-card-actions>
                            <v-expand-transition>
                                <div v-show="item.show">
                                    <v-divider></v-divider>
                                    <v-container>
                                        <v-row no-gutters>
                                            <v-col>
                                                <v-sheet class="pa-2 ma-2 text-h6 custom-font hp-card">
                                                    Art 
                                                </v-sheet>
                                            </v-col>
                                            <v-col>
                                                <v-sheet class="pa-2 ma-2 text-h6 custom-font hp-card">
                                                    {{item.species}}
                                                </v-sheet>
                                            </v-col>
                                            <v-responsive width="100%"></v-responsive>
                                            <v-col>
                                                <v-sheet class="pa-2 ma-2 text-h6 custom-font hp-card">
                                                    Kön
                                                </v-sheet>
                                            </v-col>
                                            <v-col>
                                                <v-sheet class="pa-2 ma-2 text-h6 custom-font hp-card">
                                                    <v-icon v-if="item.gender === 'male'" icon="mdi-gender-male"></v-icon>
                                                    <v-icon v-if="item.gender === 'female'" icon="mdi-gender-female"></v-icon>
                                                </v-sheet>
                                            </v-col>
                                            <v-responsive width="100%"></v-responsive>
                                            <v-col>
                                                <v-sheet class="pa-2 ma-2 text-h6 custom-font hp-card">
                                                    Födelsedatum
                                                </v-sheet>
                                            </v-col>
                                            <v-col>
                                                <v-sheet class="pa-2 ma-2 text-h6 custom-font hp-card">
                                                    {{item.dateOfBirth}}
                                                </v-sheet>
                                            </v-col>
                                            <v-responsive width="100%"></v-responsive>
                                            <v-col>
                                                <v-sheet class="pa-2 ma-2 text-h6 custom-font hp-card">
                                                    Födelseår 
                                                </v-sheet>
                                            </v-col>
                                            <v-col>
                                                <v-sheet class="pa-2 ma-2 text-h6 custom-font hp-card">
                                                    {{item.yearOfBirth}}
                                                </v-sheet>
                                            </v-col>
                                            <v-responsive width="100%"></v-responsive>
                                            <v-col>
                                                <v-sheet class="pa-2 ma-2 text-h6 custom-font hp-card">
                                                    Härkomst 
                                                </v-sheet>
                                            </v-col>
                                            <v-col>
                                                <v-sheet class="pa-2 ma-2 text-h6 custom-font hp-card">
                                                    {{item.ancestry}}
                                                </v-sheet>
                                            </v-col>
                                            <v-responsive width="100%"></v-responsive>
                                            <v-col>
                                                <v-sheet class="pa-2 ma-2 text-h6 custom-font hp-card">
                                                    Ögonfärg 
                                                </v-sheet>
                                            </v-col>
                                            <v-col>
                                                <v-sheet class="pa-2 ma-2 text-h6 custom-font hp-card">
                                                    {{item.eyeColour}}
                                                </v-sheet>
                                            </v-col>
                                            <v-responsive width="100%"></v-responsive>
                                            <v-col>
                                                <v-sheet class="pa-2 ma-2 text-h6 custom-font hp-card">
                                                    Hårfärg 
                                                </v-sheet>
                                            </v-col>
                                            <v-col>
                                                <v-sheet class="pa-2 ma-2 text-h6 custom-font hp-card">
                                                    {{item.hairColour}}
                                                </v-sheet>
                                            </v-col>
                                            <v-responsive width="100%"></v-responsive>
                                            <v-col>
                                                <v-sheet class="pa-2 ma-2 text-h6 custom-font hp-card">
                                                    Trollstav 
                                                </v-sheet>
                                            </v-col>
                                            <v-col>
                                                <v-sheet class="pa-2 ma-2 text-h6 custom-font hp-card">
                                                    {{item.wand.core}}
                                                    {{item.wand.wood}}
                                                    {{item.wand.length}}
                                                </v-sheet>
                                            </v-col>
                                            <v-responsive width="100%"></v-responsive>
                                            <v-col>
                                                <v-sheet class="pa-2 ma-2 text-h6 custom-font hp-card">
                                                    Patronus 
                                                </v-sheet>
                                            </v-col>
                                            <v-col>
                                                <v-sheet class="pa-2 ma-2 text-h6 custom-font hp-card">
                                                    {{item.patronus}}
                                                </v-sheet>
                                            </v-col>
                                            <v-responsive width="100%"></v-responsive>
                                            <v-col>
                                                <v-sheet class="pa-2 ma-2 text-h6 custom-font hp-card">
                                                    Hogwarts student 
                                                </v-sheet>
                                            </v-col>
                                            <v-col>
                                                <v-sheet class="pa-2 ma-2 text-h6 custom-font hp-card">
                                                    <v-icon v-if="item.hogwartsStudent" icon="mdi-check"></v-icon> 
                                                    <v-icon v-else icon="mdi-close"></v-icon>
                                                </v-sheet>
                                            </v-col>
                                            <v-responsive width="100%"></v-responsive>
                                            <v-col>
                                                <v-sheet class="pa-2 ma-2 text-h6 custom-font hp-card">
                                                    Hogwarts anställd 
                                                </v-sheet>
                                            </v-col>
                                            <v-col>
                                                <v-sheet class="pa-2 ma-2 text-h6 custom-font hp-card">
                                                    <v-icon v-if="item.hogwartsStaff" icon="mdi-check"></v-icon> 
                                                    <v-icon v-else icon="mdi-close"></v-icon>
                                                </v-sheet>
                                            </v-col>
                                        </v-row>
                                    </v-container>
                                </div>
                            </v-expand-transition>
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
body { font-size: 1em; background: #221E4E; padding: 2em; font-family: 'BluuNextBoldItalic', serif;}
.card { border-radius: 8px; box-shadow: 0 4px 10px rgba(0,0,0,.15); -webkit-box-shadow: 0 4px 10px rgba(0,0,0,.15); -moz-box-shadow: 0 4px 10px rgba(0,0,0,.15); background-color: #F1E6BA;}
.card-topper { border-top-right-radius: 8px; border-top-left-radius: 8px; padding: 8px 16px; font-size: 2em; font-weight: 600; text-align: center; background-color: #312823; color: #ffffff;}
.pic { max-width: 270px; max-height: 200px; padding-bottom: 1em; width: auto; height: auto;}
.titles {font-family: serif;}
#test { border: 2px solid black;}
#test td { border: 1px solid black;}
.table-responsive { overflow-x: unset; }
</style>

