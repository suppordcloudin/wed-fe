<template>
    <div>
        <input v-model="uname" type="text">
        <input v-model="pass" type="password">
        <button @click="login()">asdasdasd</button>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                uname: '',
                pass: ''
            }
        },
        methods: {
            login(){
                if(this.uname=="admin" && this.pass=="asd"){
                    console.log('logged in');
                    localStorage.setItem('auth', 'masuk');
                    this.$router.push({name: "Attendance"})

                    // let val = localStorage.getItem('auth');
                }
            }
        }
    }     
</script>