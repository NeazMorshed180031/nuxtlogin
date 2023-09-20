<template>
    <h1>Hello User,Welcome on Home Page</h1>
</template>
<script>
export default{
    
    async mounted(){
        let user=localStorage.getItem('userinfo')
        if(!user){
            this.$router.push('/login')
        }
    }
}

</script>