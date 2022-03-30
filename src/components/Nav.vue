<template>
     <nav class="navbar">
      <div class="nav-wrapper">
        <router-link to="/" class="brand-logo">Employe Manager</router-link>
      </div>
    </nav>
</template>

<script>
    export default{
        name: 'Navb',
        data(){
            return{
                
            }
        }
    }
</script>

<style scoped>
    .navbar{
        width: 40%;
        margin: auto;
    }
    .brand-logo{
        padding: 5px;
    }
</style>