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
    <v-container>
        <v-row class="fill-height overflow-y-auto">
            <v-col lg="3" md="5" sm="7" cols="12" min-width="340" max-width="344" v-for="item in char">
                <v-sheet min-height="250" class="fill-height" color="transparent">
                    <v-lazy
                        v-model="item.isActive" :options="{
                        threshold: .5
                        }"
                        min-width="340"
                        class="fill-height">

                <v-card
                    :key="item.id"
                    class="mx-auto"
                    max-width="344"
                    width="340"
                    >
                    <v-img
                        :src="item.image"
                        max-height="200px"
                        contain
                        max-width="270px"
                        padding-bottom="1em"
                        width="auto"
                        height="auto"
                        ></v-img>
                    <v-card-title>
                        {{item.name}}
                    </v-card-title>
                    <v-card-subtitle>
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
                            <v-card-text>
                                I'm a thing. But, like most politicians, he promised more than he could deliver. You won't have time for sleeping, soldier, not with all the bed making you'll be doing. Then we'll go with that data file! Hey, you add a one and two zeros to that or we walk! You're going to do his laundry? I've got to find a way to escape.
                            </v-card-text>
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
body { font-size: 1em; background: #221E4E; padding: 2em; font-family: 'BluuNextBoldItalic', serif;}
.card { border-radius: 8px; box-shadow: 0 4px 10px rgba(0,0,0,.15); -webkit-box-shadow: 0 4px 10px rgba(0,0,0,.15); -moz-box-shadow: 0 4px 10px rgba(0,0,0,.15); background-color: #F1E6BA;}
.card-topper { border-top-right-radius: 8px; border-top-left-radius: 8px; padding: 8px 16px; font-size: 2em; font-weight: 600; text-align: center; background-color: #312823; color: #ffffff;}
.pic { max-width: 270px; max-height: 200px; padding-bottom: 1em; width: auto; height: auto;}
.titles {font-family: serif;}
#test { border: 2px solid black;}
#test td { border: 1px solid black;}
.table-responsive { overflow-x: unset; }
</style>

