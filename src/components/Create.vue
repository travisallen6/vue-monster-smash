<template>
    <div >
        <form class="form-container" @submit.prevent="submitMonster">
            <label>Name:</label>
            <input type="text" v-model="nameInput">
            <label>Health:</label>
            <input type="text" v-model="healthInput">
            <label>Attack:</label>
            <input type="text" v-model="attackInput">
            <button type="submit">Create</button>

        </form>
    </div>
</template>

<script>
    export default {
        data() {
            return{
                nameInput: '',
                healthInput: '',
                attackInput: ''
            }
        },
        methods: {
            submitMonster(){
                let monster = {
                    name: this.nameInput,
                    health: this.healthInput,
                    attack: this.attackInput
                }

                this.gimme(monster)
                this.nameInput = '';
                this.healthInput = '';
                this.attackInput = ''; 
            }


        },
        props: ['gimme']
        
    }
</script>

<style scoped>
    .form-container {
        display:flex;
        flex-direction: column;
        width: 25vw;
    }

    .form-container > label, .form-container > button {
        margin-top: 10px;
    }

</style>