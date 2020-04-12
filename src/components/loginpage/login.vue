<template>
    <div id="form" class="mx-auto container ">
        <input class="form-control" v-model="nick" placeholder="Enter your Nick" type="text" id="nickname" required/>
        <input class="form-control mt-4" v-model="password" placeholder="Make sure to remember your password, because we don't !" type="password" id="password" required/>
    <button class="btn mt-4 btn-outline-primary" @click="signup()" > Get Set Go</button>
    </div>
</template>

<script>
export default {
    data : function(){
        return {
            nick:"",
            password:"",
        }
    },
    methods:{
        signup(){
          
            axios.post('http://localhost:8000/auth/users/create/', this.$data, (data) => 
            {
                alert("Your account has been created. You will be signed in automatically")
               
                })
                .fail((response) => {
                alert(response.responseText)
            })

        }
    }
}
</script>

<style lang="scss" scoped>


#form {
     font-family: 'Comic Neue', cursive;
}

input {
    background:none;
    border:none;
    border-bottom: 2px solid black;
}
input:focus {
    border:none;
    background:none;
}
</style>