<template>
    <div className="inner">
        <h1 className="form__title">Регистрация</h1>
        <input className="form__input" type="text" v-model="userName" placeholder="Name">
        <input className="form__input" type="password" v-model="userPwd" placeholder="Password">
        <input className="form__input" type="email" v-model="userEmail" placeholder="Email">
        <button className="form__btn" @click="sendData()" type="text">Send</button>
        <p className="form__error" v-if="flag == 1" > {{ error }}</p> <!--допущена ошибка -->

         <div className="form__message" v-if="(userData.length == 0) && (flag == 0)"> <!--массив пуст и нет ошибок -->
            К сожалению, сейчас нет активных пользователей
        </div>
        <div className="form__message" v-else-if="userData.length != 0"> <!--массив непуст и нет ошибок -->
            Активных пользователей сейчас: {{ userData.length }}
        </div>
        <div className="users" v-for="(el,index) in userData" :key="index"> <!--проход по массиву с ключом index -->
            <h3 className="users__name"> {{ el.name }}</h3>
            <p className="user__info"> {{  el.email }} - {{ el.pass }}</p>
        </div>
    </div>
</template>

<style scoped>
    *,
    *::after,
    *::before{
        box-sizing: border-box;
        font-family: "Open Sans", sans-serif;
    }
    .inner{
        text-align: center;
        width: 300px;
        margin: auto;
    }
    .form__title{
        border-bottom: 3px solid #81bd72;
        width: 300px;
        text-align: center;
        padding-bottom: 5px;
    }
    .form__input{
        width: 300px;
        display: block;
        margin-bottom: 15px;
        border-radius: 15px;
        padding: 15px;
        background-color: transparent;
        border: 3px solid #81bd72;
        font-size: 16px;
        font-weight: 800;
    }
    .form__input::placeholder{
        color: black;
        font-size: 15px;
        font-weight: 800;
    }
    .form__btn{
        background-color: #81bd72;
        border: 3px solid black;
        padding: 15px;
        border-radius: 15px;
        width: 300px;
        font-size: 15px;
        font-weight: 800;
        cursor: pointer;
        transition: all ease .4s;
        margin-bottom: 30px;
    }
    .form__btn:hover{
        background-color: black;
        border: 3px solid #81bd72;
        color: #81bd72;
    }
    .form__btn:active{
        transform: translateY(10px);
    }
    .form__error{
        background-color: rgb(195, 98, 98);
        padding: 15px;
        border-radius: 15px;
    }
    .form__message{
        background-color: gray;
        padding: 15px;
        border-radius: 15px;
        margin-bottom: 15px;
    }
    .users{
        background-color: #81bd72;
        padding: 3px;
        border-radius: 15px;
        margin-bottom: 15px;

    }

</style>

<script>

export default {
    data() {
        return {
            flag: 0,
            userData: [],
            error: '',
            userName: '',
            userPwd: '',
            userEmail: '',
        }
    },
    methods: {
        sendData() {
            if(this.userName == '') {
                this.flag = 1
                this.error = 'Имя не введено'
                return
            }else if(this.userPwd == '') {
                this.flag = 1
                this.error = 'Пароль не введен'
                return
            }else if(this.userEmail == '') {
                this.flag = 1
                this.error = 'Email не введен'
                return
            }
            this.error = ''
            this.flag = 0
            this.userData.push({
                name: this.userName,
                pass: this.userPwd,
                email: this.userEmail
            })
        }
    }
}
</script>



