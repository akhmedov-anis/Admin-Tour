<template>
  <div id="app">
    <div class="header">
      <h1>
        Нажмите чтобы <br> открыть форму
      </h1>
      <div class="btns">
        <button @click="showWh(1)" :class="isShow == 1 ? 'active' : ''" :disabled="isShow == 1 ? true : false">
          Связаться с клиентом
        </button>
        <button @click="showWh(2)" :class="isShow == 2 ? 'active' : ''" :disabled="isShow == 2 ? true : false">
          Запросы на тур
        </button>
        <!-- <button @click="showWh(3)" :class="isShow == 3 ? 'active' : ''" :disabled="isShow == 3 ? true : false">
          Создать тур
        </button>
        <button @click="showWh(4)" :class="isShow == 4 ? 'active' : ''" :disabled="isShow == 4 ? true : false">
          Просмотреть туры
        </button> -->
      </div>
    </div>

    <div class="main">
      <div class="contacts" v-if="isShow == 1">
        <h1>Таблица запросов на клиентов</h1>
        <br>
        <table>
          <thead>
            <tr>
              <th>№</th>
              <th>Имя фамилия</th>
              <th>Адрес электронной почты</th>
              <th>Номер телефона</th>
              <th>Описание</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="item of arr" :key="item">
              <td>{{ item.id }}</td>
              <td>{{ item.name }}</td>
              <td>{{ item.email }}</td>
              <td>{{ item.phone }}</td>
              <td><nuxt-link :to="'user/' + item.id">Посмотреть описание</nuxt-link></td>

            </tr>
          </tbody>
        </table>
      </div>
      <div class="request" v-else-if="isShow == 2">
        <h1>Таблица запросов на тур</h1>
        <br>
        <table>
          <thead>
            <tr>
              <th>№</th>
              <th>Имя фамилия</th>
              <th>Адрес электронной почты</th>
              <th>Номер телефона</th>
              <th>Гражданин</th>
              <th>На дату</th>
              <th>Описание</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="item of arrTours" :key="item">
              <td>{{ item.id }}</td>
              <td>{{ item.name }}</td>
              <td>{{ item.email }}</td>
              <td>{{ item.phone }}</td>
              <td>{{ item.rezident }}</td>
              <td>{{ item.date }}</td>
              <td><nuxt-link :to="'reqUser/' + item.id">Посмотреть описание</nuxt-link></td>

            </tr>
          </tbody>
        </table>
      </div>
      <!-- <div class="tour" v-else-if="isShow == 3">
        <h1>Создать тур</h1>
        <form @submit.prevent="" action="">
          <label for="" class="nameTour">
            <h3>Название тура</h3>
            <input require placeholder="ru" name="ru" type="text">
            <input require placeholder="uz" name="uz" type="text">
            <input require placeholder="en" name="en" type="text">
          </label>
          <label for="" class="valuePeople">
            <h3>Кол-во дней</h3>
            <input require placeholder="Кол-во дней" name="days" type="number">
          </label>npm run dev
          <label for="" class="route">
            <h3>Маршрут Uz</h3>
            <input v-for="item of num" :key="item" require placeholder="путь" name="ru" type="text">
            <h3>Маршрут Ru</h3>
            <input v-for="item of num" :key="item" require placeholder="путь" name="uz" type="text">
            <h3>Маршрут En</h3>
            <input v-for="item of num" :key="item" require placeholder="путь" name="en" type="text">
            <button @click="num++" >Добавить маршрут</button>
          </label>
          <label for="" class="duration">
            <h3>Длительность</h3>
            <input require placeholder="Дней" name="ru" type="number">
            <input require placeholder="Ночей" name="uz" type="number">
          </label>
          <label for="" class="listDays">
            <h3>Распись по дням</h3>
            <div class="day" v-for="item of numDay" :key="item">

              <input require placeholder="Название дня" name="ru" type="text">
              <input require placeholder="Описания дня" name="ru" type="text">
            </div>
            <h3>Распись по дням</h3>
            <div class="day" v-for="item of numDay" :key="item">

              <input require placeholder="Название дня UZ" name="uz" type="text">
              <input require placeholder="Описания дня UZ" name="uz" type="text">
            </div>
            <h3>Распись по дням</h3>
            <div class="day" v-for="item of numDay" :key="item">

              <input require placeholder="Название дня EN" name="en" type="text">
              <input require placeholder="Описания дня EN" name="en" type="text">
            </div>
            <button @click="numDay++" >Добавить маршрут</button>
          </label>
          <label for="" class="photo">
            <h3>Фото для расписи дней</h3>
            <input v-for="item of numDay" :key="item" placeholder="Фото для дня (только ссылка)" name="ru" type="text">
          </label>
          <label for="" class="valuePeoplePrice">
            <h3>Кол-во людей</h3>
            <div v-for="item of numPeople" :key="item" class="peopleValue">
              <input placeholder="Кол-во людей" name="ru" type="number">
              <input placeholder="Цены за кол-во людей" name="ru" type="number">
            </div>
            <button @click="numPeople++" >Добавить людей кол-во</button>
          </label>
          <label for="" class="hotels">
            <h3>Название города отлея</h3>
            <div v-for="item of numHotels" :key="item" class="peopleValue">
              <input placeholder="Название города RU" name="ru" type="text">
              <input placeholder="Название города UZ" name="uz" type="text">
              <input placeholder="Название города En" name="en" type="text">
            </div>
            <h3>Название отеля</h3>
            <div v-for="item of numHotels" :key="item" class="peopleValue">
              <input placeholder="Название отеля RU" name="ru" type="text">
              <input placeholder="Название отеля UZ" name="uz" type="text">
              <input placeholder="Название отеля EN" name="en" type="text">
            </div>
            <h3>Название кол-во людей в отель</h3>
            <div v-for="item of numHotels" :key="item" class="peopleValue">
              <input placeholder="На какое кол-во людей" name="ru" type="text">
            </div>
            <button @click="numHotels++" >Добавить отель</button>
          </label>
          <label for="" class="include">
            <h3>Что входит в цену</h3>
            <div v-for="item of include" :key="item" class="peopleValue">
              <input placeholder="Что входит RU" name="ru" type="text">
              <input placeholder="Что входит UZ" name="uz" type="text">
              <input placeholder="Что входит En" name="en" type="text">
            </div>
            <button @click="include++" >Добавить отель</button>
          </label>
          <label for="" class="unInclude">
            <h3>Что не входит в цену</h3>
            <div v-for="item of unInclude" :key="item" class="peopleValue">
              <input placeholder="Что не входит RU" name="ru" type="text">
              <input placeholder="Что не входит UZ" name="uz" type="text">
              <input placeholder="Что не входит En" name="en" type="text">
            </div>
            <button @click="unInclude++" >Добавить отель</button>
          </label>
        </form>
        <button @click="useForm()" >Добавить отель</button>
      </div> -->
      <!-- <div class="request" v-else-if="isShow == 3">
        <h1>Таблица туров</h1>
      </div> -->
      <div class="error" v-else></div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'IndexPage',
  data() {
    return {
      isShow: 1 ,
      arr: [],
      arrTours: [],
      showDropDown: false,
      num: 1,
      numDay: 1,
      numPeople: 1,
      numHotels: 1,
      include: 1,
      unInclude: 1,
    }
  },
  methods: {
    useForm(){
      let fm = event.target.parentNode.children[1].children
      let obj = {}
      // let nameTour = fm.getElementsByClassName('nameTour')
      // let valuePeople = fm.getElementsByClassName('valuePeople')
      // let route = fm.getElementsByClassName('route')
      // let duration = fm.getElementsByClassName('duration')
      // let listDays = fm.getElementsByClassName('listDays')
      // let photo = fm.getElementsByClassName('photo')
      // let valuePeoplePrice = fm.getElementsByClassName('valuePeoplePrice')
      // let hotels = fm.getElementsByClassName('hotels')
      // let include = fm.getElementsByClassName('include')
      // let unInclude = fm.getElementsByClassName('unInclude')

      console.log(fm[0].children)
      //for(let item of fm){
        //console.log(item.children[0]);
      //}

      // console.log(nameTour, `\n`, valuePeople, `\n`, route, `\n`, duration, `\n`, listDays, `\n`, photo, `\n`, photo, `\n`, valuePeoplePrice, `\n`, hotels, `\n`, include, `\n`, unInclude);
    },
    showWh(param) {
      this.isShow = param
    },
    show(param) {
      param.isShow
    },
    getUsers(param) {
      axios.get(param)
        .then((res) => {
          console.log(res.data);
          this.arr = res.data.reverse()
          for (let item of this.arr) {
            item.showDropDown = false
            if (item.isShow == 0) {
              item.isShow = 'Не просмотрено'
              item.isShow = 0
            } else if (item.isShow == 1) {
              item.isShow = 'Просмотрено'
              item.isShow = 1
            } else if (item.isShow == 2) {
              item.isShow = 'В процессе'
              item.isShowNum = 2
            } else {
              item.isShow = 'Error'
            }
          }
        })
        .catch((err) => {
          console.log(err);
        })
    },
    getReqTours(param) {
      axios.get(param)
        .then((res) => {
          console.log(res);
          this.arrTours = res.data.reverse()
        })
        .catch((err) => {
          console.log(err);
        })
    }
  },
  async mounted() {
    await this.getUsers('https://64b11fe5062767bc4825ba51.mockapi.io/contacts')
    await this.getReqTours('https://645d2fb3250a246ae319f640.mockapi.io/request')

    setInterval(() => {
      console.log('Получили доп запросы');
      this.getUsers('https://64b11fe5062767bc4825ba51.mockapi.io/contacts')
      this.getReqTours('https://645d2fb3250a246ae319f640.mockapi.io/request')
    }, 60000)
  }
}
</script>
