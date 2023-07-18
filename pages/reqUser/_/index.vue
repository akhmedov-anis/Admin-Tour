<template>
    <div id="user">
        <nuxt-link to="/">
            <button>
                Назад
            </button>
        </nuxt-link>
        <br>
        <br>
        <h1>
            ФИО
        </h1>
        <h3>
            {{ user.name }}
        </h3>
        <br>
        <h1>
            Email
        </h1>
        <h3>
            {{ user.email }}
        </h3>
        <br>
        <h1>
            Номер телефона
        </h1>
        <h3>
            {{ user.phone }}
        </h3>
        <br>
        <h1>
            Гражданин
        </h1>
        <h3>
            {{ user.rezident }}
        </h3>
        <br>
        <h1>
            На дату
        </h1>
        <h3>
            {{ user.date }}
        </h3>
        <br>
        <h1>
            Описание
        </h1>
        <h3>
            {{ user.disc }}
        </h3>
        <br>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    data() {
        return {
            user: Object
        }
    },
    mounted() {
        let link = window.location.href.split('/')[window.location.href.split('/').length - 1]
        axios.get('https://645d2fb3250a246ae319f640.mockapi.io/request/' + link)
            .then((res) => {
                console.log(res.data);
                this.user = res.data
            })
            .catch((err) => {
                console.log(err);
            })
    }
}
</script>

<style>
#user {
    padding: 50px;
}

#user button {
    padding: 15px 30px;
    border: none;
    margin-right: 10px;
    font-size: 20px;
    background-color: rgb(0, 132, 255);
    border-radius: 15px;
    font-weight: bold;
    color: white;
}

button:hover {
    cursor: pointer;
}
</style>