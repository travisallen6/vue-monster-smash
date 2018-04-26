<template>
    <div>

    <div class="arena-container">
        <div class="monster-divider">
            <h2>Monster1</h2>
                {{monster1}}
        </div >
        <div class="monster-divider">
            <h2>Monster2</h2>
            {{monster2}}
        </div>
    </div>
        <div class="btn">
            <button @click='battle'>Battle</button>
        </div>
    <div class="monster-pad">

    
        <monster
            v-for='(monster, i) in monsters' :key='i'
                :monster='monster'
                :select='selectMonster'
                :monsterid='i'
                :editMonster='receiveEdits'
            >
        </monster>
    </div>
        
    </div>
</template>

<script>
    import Monster from './Monster'

    export default {
        data(){
            return {
                monster1: '',
                monster2: ''
            }
        },

        methods: {
            selectMonster(monster){
                if(this.monster1 === ''){
                    this.monster1 = monster.name;

                } else if(this.monster2 === ''){
                    this.monster2 = monster.name
                }
            },

            battle(){
                let winner = Math.floor(Math.random() * 2)
                console.log(winner)
                if(this.monster1 !== '' || this.monster2 !== ''){

                    if(winner === 0){
                        alert("Winner: " + this.monster1 )
                    } else if (winner === 1){
                        alert("Winner: " + this.monster2)
                    }
                    this.monster1 = '';
                    this.monster2 = '';
                }
            },

            receiveEdits(i, newMonster){
                this.repeatReceiveEdits(i, newMonster)
            }

        },

        components: {
            monster: Monster
        },

        props: ['monsters', 'repeatReceiveEdits']
        
    }
</script>

<style scoped>
    .arena-container {
        display: grid;
        grid-template-columns: 1fr 1fr;
        background-color: #00f486;
        color:grey;
        padding: 20px;
    }
    .monster-pad {
        display:grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 15px;
        padding: 15px;
        color:grey;
    }

    .btn {
        display:flex;
        justify-content: center;
        grid-template-columns:1/2;
        background-color: #00f486;
        padding: 20px;
    }

</style>