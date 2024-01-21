<script setup lang="ts">
import { ref } from 'vue'
import characters from '../assets/data/characters.json'

export interface MyObj {
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

let obj: MyObj[] = characters as MyObj[];

//const show = ref(false)
</script>
<script lang="ts">
export default {
    data() {
      return {
          char: characters as MyObj[],
          show: "" as String,
      }
    },
    methods: {
      showHide(id: string) {
        this.show === id ? this.show = "" : this.show = id;
      }
    }
  }
</script>
<template>
    <v-card
        v-for="item in char" :key="item.id"
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
        :icon="show === item.id ? 'mdi-chevron-up' : 'mdi-chevron-down'"
        @click="showHide(item.id)"
      ></v-btn>
    </v-card-actions>

    <v-expand-transition>
      <div v-show="show === item.id">
        <v-divider></v-divider>

        <v-card-text>
          I'm a thing. But, like most politicians, he promised more than he could deliver. You won't have time for sleeping, soldier, not with all the bed making you'll be doing. Then we'll go with that data file! Hey, you add a one and two zeros to that or we walk! You're going to do his laundry? I've got to find a way to escape.
        </v-card-text>
      </div>
    </v-expand-transition>
  </v-card>
        <div class="container-fluid">
            <div class="row">
                <div v-for="item in obj" class="col-sm-6 col-lg-4 col-xl-4 mb-5" style="max-width: 400px;">
                    <div class="card">
                        <div class="card-topper card-img-top">{{item.name}}</div>
                        <div class="card-body">
                            <img class="rounded mx-auto d-block pic" v-bind:src="item.image">
                            <div class="table-responsive">
                                <table id="test" class="table table-bordered table-hover">
                                    <tbody>
                                        <tr>
                                            <td class="titles">Species</td>
                                            <td class="text-center">{{item.species}}</td>
                                        </tr>
                                        <tr>
                                            <td class="titles">Gender</td>
                                            <td class="gender text-center">{{item.gender}}</td>
                                        </tr>
                                        <tr>
                                            <td class="titles">House</td>
                                            <td class="house text-center">{{item.house === "" ? '-' : item.house}}</td>
                                        </tr>
                                        <tr>
                                            <td class="titles">Date of Birth</td>
                                            <td class="text-center" id="dateOfBirth">{{item.dateOfBirth === null ? '-' : item.dateOfBirth}}</td>
                                        </tr>
                                        <tr>
                                            <td class="titles">Year of Birth</td>
                                            <td class="text-center">{{item.yearOfBirth === null ? '-' : item.yearOfBirth}}</td>
                                        </tr>
                                        <tr style="visibility: {{{item.wizard === true ? 'visible':'collapse'}}">
                                            <td class="titles text-center" colspan="2">Wizard</td>
                                        </tr>
                                        <tr>
                                            <td class="titles">Ancestry</td>
                                            <td class="text-center">{{item.ancestry}}</td>
                                        </tr>
                                        <tr>
                                            <td class="titles">Eye colour</td>
                                            <td class="eyeColor text-center">{{item.eyeColour}}</td>
                                        </tr>
                                        <tr>
                                            <td class="titles">Hair colour</td>
                                            <td class="hairColor text-center">{{item.hairColour}}</td>
                                        </tr>
                                        <tr style="display: {{item.wand.wood !== '' ? '' : 'none'}}">
                                            <td class="titles" style="padding-top: 2em; padding-bottom: 2em;">Wand</td>
                                            <td class="text-center">
                                                <span>{{item.wand.wood}}</span>
                                                <br>
                                                <span>{{item.wand.core}}</span>
                                                <br>
                                                <span>{{item.wand.length}}</span>
                                            </td>
                                        </tr>
                                        <tr style="display: {{item.patronus !== '' ? '' : 'none'}}">
                                            <td class="titles">Patronus</td>
                                            <td class="text-center">{{item.patronus}}</td>
                                        </tr>
                                        <tr>
                                            <td class="titles">Hogwarts Student</td>
                                            <td class="isStudent text-center">{{item.hogwartsStudent}}</td>
                                        </tr>
                                        <tr>
                                            <td class="titles">Hogwarts Staff</td>
                                            <td class="isStaff text-center">{{item.hogwartsStaff}}</td>
                                        </tr>
                                        <tr>
                                            <td class="titles">Actor</td>
                                            <td class="text-center">{{item.actor}}</td>
                                        </tr>
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                </div>
                </div>
                </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
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

