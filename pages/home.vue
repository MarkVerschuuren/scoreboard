<template>
    <div>
        <div v-for="(team, teamNumber) in form.team" :key="teamNumber" style="width: 50%;">
            <div style="margin-bottom: 5px">
                {{ teamNumber }}
            </div>
            <div style="display: flex; align-items: flex-start; gap: 10px ">

                <el-input v-model=team.player1 style="margin-bottom: 10px;"  placeholder="Player 1" @input="updateTeam($event)"></el-input>
                <el-input v-model=team.player2 style="margin-bottom: 10px;"  placeholder="Player 2" @input="updateTeam($event)"></el-input>

                <el-button class="el-icon-minus" @click="numberOfTeams--" />
            </div>
        </div>
        <el-button @click="numberOfTeams++">+</el-button>
    </div>
 
</template>

<script setup lang="ts">
import { ref } from '@nuxtjs/composition-api'
import debounce from 'lodash/debounce';

const defaultForm = () =>  ({
    team: {'Team 1' : { player1: '', player2: '' }}
})

const numberOfTeams = ref(1)
const form = ref(defaultForm())

const updateTeam = debounce(function (event: string){
    console.log(event)

}, 500)



</script>
