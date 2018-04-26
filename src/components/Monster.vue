<template>
    <div class="monster-card">
        <div v-if='!editing'>
            <p>Name: {{monster.name}}</p>
            <p>Health: {{monster.health}}</p>
            <p>Attack: {{monster.attack}}</p>
            <button @click='pickMonster'>Select</button>
            <button @click='editingMonster(true)'>Edit</button>
        </div>
        <div v-else >
            <form @submit.prevent='submitEdits'>
                <input type="text" v-model="nameInput">
                <input type="text" v-model="healthInput">
                <input type="text" v-model="attackInput">
                <button type="submit">Submit</button>

            </form>
        </div>
    </div>
</template>

<script>
    export default {
        data(){
            return {
                nameInput: this.monster.name,
                healthInput: this.monster.health,
                attackInput: this.monster.attack,
                editing: false
            }
        },

        props: ['monster', 'select', 'editMonster', 'monsterid' ],

        methods: {
            pickMonster(){
                this.select(this.monster)
            },

            editingMonster(bool){
                this.editing = bool
            },

            submitEdits(){
                let newMonster = {
                    name: this.nameInput,
                    health: this.healthInput,
                    attack: this.attackInput
                }

                this.editMonster(this.monsterid, newMonster)
                this.editing = false
            }

            // submitEdit

        }
        
    }
</script>

<style scoped>
    .monster-card {
        background: #111;
        color: white;
        padding: 15px;
    }

</style>