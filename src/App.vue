<template>
  <div class="container">
    <form class="form">
      <h1>Регистрация</h1>

      <div class="form-content">
        <div class="form-section">
          <div class="form-param">
            <label for="">Фамилия*</label>
            <span v-if="v$.form.secondName.$error">
              {{ v$.form.secondName.$errors[0].$message }}
            </span>
            <input
              class="input"
              v-model.trim="form.secondName"
              placeholder="Введите фамилию"
            />
          </div>

          <div class="form-param">
            <label for="">Имя*</label>
            <span v-if="v$.form.name.$error">
              {{ v$.form.name.$errors[0].$message }}
            </span>
            <input
              class="input"
              v-model.trim="form.name"
              placeholder="Введите имя"
            />
          </div>

          <div class="form-param">
            <label for="">Отчество</label>
            <input
              class="input"
              v-model.trim="form.patronymic"
              placeholder="Введите отчество"
            />
          </div>

          <div class="form-param">
            <!-- Переделать -->
            <label for="">Дата рождения*</label>
            <input class="input" v-model="form.birthday" type="date" />
            <span v-if="v$.form.birthday.$error">
              {{ v$.form.birthday.$errors[0].$message }}
            </span>
          </div>

          <div class="form-param">
            <label for="">Номер телефона*</label>
            <span v-if="v$.form.phone.$error">
              {{ v$.form.phone.$errors[0].$message }}
            </span>
            <input class="input" type="number" v-model.trim="form.phone" />
          </div>

          <div class="form-param">
            <label>Пол</label>
            <div class="form-check">
              <input
                class="radio"
                value="male"
                type="radio"
                id="male"
                v-model="form.gendere"
              />
              <label>Мужчина</label>
            </div>
            <div class="form-check">
              <input
                class="radio"
                value="female"
                type="radio"
                id="female"
                v-model="form.gendere"
              />
              <label>Женщина</label>
            </div>
          </div>

          <div class="form-param">
            <label>Группа клиентов*</label>
            <span v-if="v$.form.clientGroup.$error">
              {{ v$.form.clientGroup.$errors[0].$message }}
            </span>
            <select multiple v-model="form.clientGroup">
              <option
                v-for="group in form.clientGroups"
                :key="group.id"
                :value="group.name"
              >
                {{ group.name }}
              </option>
            </select>
          </div>

          <div class="form-param">
            <label>Врач</label>
            <select v-model="form.doctor">
              <option
                v-for="doctor in form.doctors"
                :key="doctor.id"
                :value="doctor.name"
              >
                {{ doctor.name }}
              </option>
            </select>
          </div>

          <div class="form-param">
            <div class="checkbox">
              <label>Не отправлять смс</label>
              <input class="input" type="checkbox" v-model="form.sendMessage" />
            </div>
          </div>
        </div>

        <div class="form-section">
          <div class="form-param">
            <label for="">Индекс</label>
            <input
              class="input"
              type="number"
              placeholder="Введите индекс"
              v-model.trim="form.index"
            />
          </div>

          <div class="form-param">
            <label for="">Страна</label>
            <input
              class="input"
              placeholder="Введите страну"
              v-model.trim="form.country"
            />
          </div>

          <div class="form-param">
            <label for="">Область</label>
            <input
              class="input"
              placeholder="Введите регион"
              v-model.trim="form.region"
            />
          </div>

          <div class="form-param">
            <label for="">Город*</label>
            <span v-if="v$.form.city.$error">
              {{ v$.form.city.$errors[0].$message }}
            </span>
            <input
              class="input"
              placeholder="Введите город"
              v-model.trim="form.city"
            />
          </div>

          <div class="form-param">
            <label for="">Улица</label>
            <input
              class="input"
              placeholder="Введите улицу"
              v-model.trim="form.street"
            />
          </div>

          <div class="form-param">
            <label for="">Дом</label>
            <input
              class="input"
              placeholder="Введите номер дома"
              v-model.trim="form.house"
            />
          </div>
        </div>

        <div class="form-section">
          <div class="form-param">
            <label>Тип документа*</label>
            <span v-if="v$.form.document.$error">
              {{ v$.form.document.$errors[0].$message }}
            </span>
            <select v-model="form.document">
              <option
                v-for="document in form.documents"
                :key="document.name"
                :value="document.name"
              >
                {{ document.name }}
              </option>
            </select>
          </div>

          <div class="form-param">
            <label for="">Серия</label>
            <input
              class="input"
              type="number"
              v-model.trim="form.series"
              placeholder="Введите серию паспорта"
            />
          </div>

          <div class="form-param">
            <label for="">Номер</label>
            <input
              class="input"
              type="number"
              v-model.trim="form.number"
              placeholder="Введите номер паспорта"
            />
          </div>

          <div class="form-param">
            <label for="">Кем выдан</label>
            <input
              class="input"
              v-model.trim="form.whoIssue"
              placeholder="Кем выдан"
            />
          </div>

          <div class="form-param">
            <label for="">Дата выдачи*</label>
            <span v-if="v$.form.dateIssue.$error">
              {{ v$.form.dateIssue.$errors[0].$message }}
            </span>
            <input
              class="input"
              type="date"
              v-model="form.dateIssue"
              placeholder="Дата выдачи"
            />
          </div>

          <button @click="register" type="button">Зарегестрироваться</button>
        </div>
      </div>

      <!-- <div>
        <label class="typo__label">Simple select / dropdown</label>
        <multiselect
          v-model="value"
          :options="options"
          :multiple="true"
          :close-on-select="false"
          :clear-on-select="false"
          :preserve-search="true"
          placeholder="Pick some"
          label="name"
          track-by="name"
          :preselect-first="true"
        >
          <template slot="selection" slot-scope="{ values, isOpen }"
            ><span
              class="multiselect__single"
              v-if="values.length &amp;&amp; !isOpen"
              >{{ values.length }} options selected</span
            ></template
          >
        </multiselect>
        <pre class="language-json"><code>{{ value  }}</code></pre>
      </div> -->
    </form>
  </div>
</template>

<script>
import useVuelidate from "@vuelidate/core";
import { required, minLength, maxLength, helpers } from "@vuelidate/validators";
import Multiselect from "vue-multiselect";

export default {
  components: {
    Multiselect,
  },
  data() {
    return {
      v$: useVuelidate(),
      form: {


      //   value: [],
      //   options: [
      //   { name: 'Vue.js', language: 'JavaScript' },
      //   { name: 'Adonis', language: 'JavaScript' },
      //   { name: 'Rails', language: 'Ruby' },
      //   { name: 'Sinatra', language: 'Ruby' },
      //   { name: 'Laravel', language: 'PHP' },
      //   { name: 'Phoenix', language: 'Elixir' }
      // ],


        secondName: "",
        name: "",
        patronymic: "",
        birthday: "",
        phone: "",
        gendere: "",
        clientGroup: [],
        clientGroups: [
          { name: "VIP", id: "1" },
          { name: "Проблемные", id: "2" },
          { name: "ОМС", id: "3" },
        ],
        doctor: "",
        doctors: [
          { name: "Иванов", id: "1" },
          { name: "Захаров", id: "2" },
          { name: "Чернышев", id: "3" },
        ],
        sendMessage: false,
        index: "",
        country: "",
        region: "",
        city: "",
        street: "",
        house: "",
        document: "",
        documents: [
          { name: "Паспорт" },
          { name: "Свидетельство о рождении" },
          { name: "Вод. удостоверение" },
        ],
        series: "",
        number: "",
        whoIssue: "",
        dateIssue: "",
      },
    };
  },
  validations() {
    return {
      form: {
        secondName: {
          //required: helpers.withMessage('Это обязательное поле', required)
        },
        name: {
          //required: helpers.withMessage('Это обязательное поле', required)
        },
        birthday: {
          // required: helpers.withMessage('Это обязательное поле', required),
          // correctDate: helpers.withMessage('Некорректная дата',
          //   (birthday) => {
          //   let bDate = new Date(birthday);
          //   let currentDate = new Date()
          //   if (bDate > currentDate) {
          //     return false
          //   }
          //   else {
          //     return true
          //   }
          // }
          // )
        },
        phone: {
          // required: helpers.withMessage('Это обязательное поле', required),
          // minLength: helpers.withMessage('Номер должен содержать 11 цифр', minLength(11)),
          // maxLength: helpers.withMessage('Номер должен содержать 11 цифр', maxLength(11)),
          // fchar: helpers.withMessage('Номер должен начинаться с 7',
          //   (value) => {
          //   value = value[0];
          //   if (value == '7') {
          //     return true
          //   }
          //   else return false
          // }
          // )
        },
        clientGroup: {
          //required: helpers.withMessage('Это обязательное поле', required)
        },
        city: {
          //required: helpers.withMessage('Это обязательное поле', required)
        },
        document: {
          //required: helpers.withMessage('Это обязательное поле', required)
        },
        dateIssue: {
          // required: helpers.withMessage('Это обязательное поле', required),
          // correctDate: helpers.withMessage('Некорректная дата',
          //   (birthday) => {
          //   let bDate = new Date(birthday);
          //   let currentDate = new Date()
          //   if (bDate > currentDate) {
          //     return false
          //   }
          //   else {
          //     return true
          //   }
          // }
          // )
        },
      },
    };
  },
  methods: {
    register() {
      console.log(this.v$.$error);
      this.v$.$validate();
      if (!this.v$.$error) {
        alert("Successful");
      } else {
        alert("Error");
      }
    },
  },
};
</script>

<style>
body {
  background-color: #363740;
}
@import url("https://fonts.googleapis.com/css2?family=Mulish:wght@400;700&display=swap");
* {
  font-family: "Mulish", sans-serif;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.container {
  margin: 0 auto;
  max-width: 1360px;
  padding: 15px;
}
h1 {
  text-align: center;
  margin-bottom: 40px;
}
label {
  /* margin-top: 10px; */
  margin-bottom: 5px;
  align-items: left;
}
.form {
  padding: 15px 15px;
  max-width: 1360px;
  width: 100%;
  border: 1px solid #dfe0eb;
  box-sizing: border-box;
  border-radius: 8px;
  background: #ffffff;
}
.form-content {
  display: flex;
  /* flex-direction: column; */
  /* align-items: center; */
  align-items: start;
  justify-content: space-around;
  flex-wrap: wrap;

  /* height: 90vh; */
}
.form-section {
  padding: 0 10px;
  display: flex;
  justify-content: center;
  /* align-items: center; */
  flex-direction: column;
}
.form-param {
  position: relative;
  display: flex;
  flex-direction: column;
  padding: 5px;
}
input,
select {
  width: 300px;
  margin-bottom: 10px;
  padding: 10px 20px 10px;
  border-radius: 8px;
  border: 1px solid #dfe0eb;
}
.input {
}
option {
}
button {
  margin-top: 14px;
  border: none;
  border-radius: 8px;
  max-width: 160px;
  width: 100%;
  height: 48px;
  background-color: #212121;
  color: #fff;
}
.radio {
  width: 30px;
}
.checkbox {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.checkbox label {
  margin: 0;
}
.checkbox input {
  width: 40px;
  margin: 0px;
}
span {
  color: red;
  font-size: 12px;
  position: absolute;
  bottom: 0;
}
@media (max-width: 400px) {
  input,
  select {
    width: 240px;
    padding: 10px 5px;
  }
}
</style>