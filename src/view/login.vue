<template>
    <div>
        用户名:<input type="text" v-model="loginForm.username" placeholder="请输入用户名"/>
        <br><br>
        密码： <input type="password" v-model="loginForm.password" placeholder="请输入密码"/>
        <br><br>
        <button v-on:click="login">登录</button>
    </div>
</template>

<script>
    import axios from 'axios'

    export default {
        name: 'login',
        data () {
            return {
                loginForm: {
                    username: '',
                    password: ''
                },
                responseResult: []
            }
        },
        methods: {
            login () {
                axios.post('/api/sysUser/getSomething', {
                        userName: this.loginForm.username,
                        userPassword: this.loginForm.password
                    })
                    .then(response => {
                        if (response.data.code === 200) {
                            this.$router.push({path: '/success'})
                        }
                        else if (response.data.code === 400){
                            this.$router.push({path: '/error'})
                        }
                    })
                    // .catch(failResponse => {
                    // })
            }
        }
    }
</script>

