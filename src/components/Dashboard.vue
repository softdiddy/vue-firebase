<template>
    <div class="dashboard">
        <ul class="collection" v-for="employe in employee" v-bind:key="employe.id">
            <li class="collection-item avatar">
            <img src="images/users.png" alt="" class="circle">
            <span class="title">{{employe.job_title}}</span>
            <p><b> {{employe.employee_name}} </b></p>
                <p>{{employe.department}}</p>
                <p class="chip">{{employe.gender}}</p>
                <a href="#!" class="secondary-content"><i class="material-icons left">Edit</i></a>
            </li>
        </ul>
        <div class="fixed-action-btn">
	<router-link to="" class="btn-floating btn-large red">
		<i class="fa-solid fa-plus"></i>
	</router-link>
</div>
    </div>
</template>

<script>
    import db from './firebaseinit'
    import { getDocs, collection } from 'firebase/firestore'

    export default{
        name: 'Dashboard',
        data(){
            return{
                employee : [],
            };
        },

        methods:{
           async fetchGames(){
                const gamesColRef= collection(db, "employees")
                let gamesSnapShot = await getDocs(gamesColRef)
                let games = []
                gamesSnapShot.forEach(game => {
                    const d = {
                        'id': game.id,
                        'employee_name': game.data().employee_name,
                        'department': game.data().department,
                        'gender': game.data().gender,
                        'job_title': game.data().job_title,
                    }

                    this.employee.push(d)
                })
            },
        },

        created () {
           this.fetchGames()
        }
    }
</script>

<style scoped>
    .dashboard{
        width: 40%;
        margin: auto;
    }
</style>
