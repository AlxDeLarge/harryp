<script setup lang="ts">

import characters from '../assets/data/characters.json'

interface MyObj {
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

interface wand {
    wood: string;
    core: string;
    length: number;
}

let obj: MyObj[] = characters as MyObj[];

//let students = document.querySelectorAll<HTMLTableCellElement>('.isStudent');
//for(let i = 0; i < students.length; i++)
//{
//    if (students[i].innerHTML === 'true')
//        {
//            students[i].innerHTML = '&#10004';
//            students[i].style.color = 'green';
//        }
//        else
//            {
//                students[i].innerHTML = '&#10006';
//                students[i].style.color = 'red';
//            }
//}
//let staff = document.querySelectorAll<HTMLTableCellElement>('.isStaff');
//for(let i = 0; i < staff.length; i++)
//{
//    if (staff[i].innerHTML === 'true')
//        {
//            staff[i].innerHTML = '&#10004';
//            staff[i].style.color = 'green';
//        }
//        else
//            {
//                staff[i].innerHTML = '&#10006';
//                staff[i].style.color = 'red';
//            }
//}
//let alive = document.querySelectorAll<HTMLTableCellElement>('.isAlive');
//for(let i = 0; i < alive.length; i++)
//{
//    if (alive[i].innerHTML === 'true')
//        {
//            alive[i].innerHTML = '&#10004';
//            alive[i].style.color = 'green';
//        }
//        else
//            {
//                alive[i].innerHTML = '&#10006';
//                alive[i].style.color = 'red';
//            }
//}
//let gender = document.querySelectorAll<HTMLTableCellElement>('.gender');
//for (let i = 0; i < gender.length; i++) {
//    if (gender[i].innerHTML === 'male')
//        {
//            gender[i].innerHTML = '&#x2642';
//            gender[i].style.color = '#0000ff';
//            gender[i].style.fontSize = '1.2em';
//        }
//        else
//            {
//                gender[i].innerHTML = '&#9792';
//                gender[i].style.color = '#ff3399';
//                gender[i].style.fontSize = '1.2em';
//            }
//}
//let houses = document.querySelectorAll<HTMLTableCellElement>('.house');
//for(var i = 0; i < houses.length; i++)
//{
//    if (houses[i].innerHTML == "Gryffindor")
//        {
//            houses[i].style.backgroundColor = '#7F0909';
//            houses[i].style.color = '#FFC500';
//        }
//        else if (houses[i].innerHTML == "Ravenclaw")
//            {
//                houses[i].style.backgroundColor = '#946B2D';
//                houses[i].style.color = '#000A90';
//            }
//            else if (houses[i].innerHTML == "Hufflepuff")
//                {
//                    houses[i].style.backgroundColor = '#000000';
//                    houses[i].style.color = '#EEE117';
//                }
//                else if (houses[i].innerHTML == "Slytherin")
//                    {
//                        houses[i].style.backgroundColor = '#AAAAAA';
//                        houses[i].style.color = '#0D6217';
//                    }
//}
//
//let eyes = document.querySelectorAll<HTMLTableCellElement>('.eyeColor');
//for(var i = 0; i < eyes.length; i++)
//{
//    if (eyes[i].innerHTML == "green")
//        {
//            eyes[i].style.color = 'green';
//        }
//        else if (eyes[i].innerHTML == "brown")
//            {
//                eyes[i].style.color = 'brown';
//            }
//            else if (eyes[i].innerHTML == "blue")
//                {
//                    eyes[i].style.color = 'blue';
//                }
//                else if (eyes[i].innerHTML == "grey")
//                    {
//                        eyes[i].style.color = 'grey';
//                    }
//                    else if (eyes[i].innerHTML == "red")
//                        {
//                            eyes[i].style.color = 'red';
//                        }
//                        else if (eyes[i].innerHTML == "yellow")
//                            {
//                                eyes[i].style.color = '#b3b300';
//                            }
//                            else
//                                {
//                                    eyes[i].style.color = 'black';
//                                }
//}
//
//
//let hair = document.querySelectorAll<HTMLTableCellElement>('.hairColor');
//for(var i = 0; i < hair.length; i++)
//{
//    if (hair[i].innerHTML == "green")
//        {
//            hair[i].style.color = 'green';
//        }
//        else if (hair[i].innerHTML == "brown")
//            {
//                hair[i].style.color = 'brown';
//            }
//            else if (hair[i].innerHTML == "blue")
//                {
//                    hair[i].style.color = 'blue';
//                }
//                else if (hair[i].innerHTML == "grey")
//                    {
//                        hair[i].style.color = 'grey';
//                    }
//                    else if (hair[i].innerHTML == "red")
//                        {
//                            hair[i].style.color = '#e68a00';
//                        }
//                        else if (hair[i].innerHTML == "blonde")
//                            {
//                                hair[i].style.color = '#b3b300';
//                            }
//                            else
//                                {
//                                    hair[i].style.color = 'black';
//                                }
//}
</script>

<template>
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
                                        <tr style="visibility: ${{item.wizard === true ? 'visible':'collapse'}}">
                                            <td class="titles text-center" colspan="2">Wizard</td>
                                        </tr>
                                        <tr>
                                            <td class="titles">Ancestry</td>
                                            <td class="text-center">${item.ancestry}</td>
                                        </tr>
                                        <tr>
                                            <td class="titles">Eye colour</td>
                                            <td class="eyeColor text-center">${item.eyeColour}</td>
                                        </tr>
                                        <tr>
                                            <td class="titles">Hair colour</td>
                                            <td class="hairColor text-center">${item.hairColour}</td>
                                        </tr>
                                        <tr style="display: ${item.wand.wood !== '' ? '' : 'none'}">
                                            <td class="titles" style="padding-top: 2em; padding-bottom: 2em;">Wand</td>
                                            <td class="text-center">
                                                <span>${item.wand.wood}</span>
                                                <br>
                                                <span>${item.wand.core}</span>
                                                <br>
                                                <span>${item.wand.length}</span>
                                            </td>
                                        </tr>
                                        <tr style="display: ${item.patronus !== '' ? '' : 'none'}">
                                            <td class="titles">Patronus</td>
                                            <td class="text-center">${item.patronus}</td>
                                        </tr>
                                        <tr>
                                            <td class="titles">Hogwarts Student</td>
                                            <td class="isStudent text-center">${item.hogwartsStudent}</td>
                                        </tr>
                                        <tr>
                                            <td class="titles">Hogwarts Staff</td>
                                            <td class="isStaff text-center">${item.hogwartsStaff}</td>
                                        </tr>
                                        <tr>
                                            <td class="titles">Actor</td>
                                            <td class="text-center">${item.actor}</td>
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
</style>

