<template>
  <div class="container">
    <form class="form">
      <label for="">Фамилия*</label>
      <input v-model.trim="form.secondName" placeholder="Введите фамилию" />
      <span v-if="v$.form.secondName.$error">
        {{v$.form.secondName.$errors[0].$message}}
      </span>

      <label for="">Имя*</label>
      <input v-model.trim="form.name" placeholder="Введите имя" />
      <span v-if="v$.form.name.$error">
        {{v$.form.name.$errors[0].$message}}
      </span>

      <label for="">Отчество</label>
      <input v-model.trim="form.patronymic" placeholder="Введите имя" />

      <label for="">Дата рождения*</label>
      <input
        v-model="form.birthday"
        type="date"
        timezone=""
        placeholder="Введите имя"
      />
      <span v-if="v$.form.birthday.$error">
        {{v$.form.birthday.$errors[0].$message}}
      </span>

      <label for="">Номер телефона*</label>
      <input
        type="number"
        v-model.trim="form.phone"
      />
      <span v-if="v$.form.phone.$error">
        {{v$.form.phone.$errors[0].$message}}
      </span>


      <label>Пол</label>
      <input v-model.trim="form.sex" type="text" />

      <label>Группа клиентов*</label>
      <select multiple v-model="form.clientGroup">
        <option
          v-for="group in form.clientGroups"
          :key="group.id"
          :value="group.name"
        >
          {{ group.name }}
        </option>
      </select>
      <span v-if="v$.form.clientGroup.$error">
        {{v$.form.clientGroup.$errors[0].$message}}
      </span>

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

      <label>Не отправлять смс</label>
      <input type="checkbox" v-model="form.sendMessage" />

      <label for="">Индекс</label>
      <input type="number" placeholder="Введите индекс" v-model.trim="form.index" />

      <label for="">Страна</label>
      <input placeholder="Введите страну" v-model.trim="form.country" />

      <label for="">Область</label>
      <input placeholder="Введите регион" v-model.trim="form.region" />

      <label for="">Город*</label>
      <input placeholder="Введите город" v-model.trim="form.city" />
      <span v-if="v$.form.city.$error">
        {{v$.form.city.$errors[0].$message}}
      </span>

      <label for="">Улица</label>
      <input placeholder="Введите улицу" v-model.trim="form.street" />

      <label for="">Дом</label>
      <input placeholder="Введите номер дома" v-model.trim="form.house" />

      <label>Тип документа*</label>
      <select v-model="form.document">
        <option
          v-for="document in form.documents"
          :key="document.name"
          :value="document.name"
        >
          {{ document.name }}
        </option>
      </select>
      <span v-if="v$.form.document.$error">
        {{v$.form.document.$errors[0].$message}}
      </span>

      <label for="">Серия</label>
      <input
        type="number"
        v-model.trim="form.series"
        placeholder="Введите серию паспорта"
      />

      <label for="">Номер</label>
      <input
        type="number"
        v-model.trim="form.number"
        placeholder="Введите номер паспорта"
      />

      <label for="">Кем выдан</label>
      <input v-model.trim="form.whoIssue" placeholder="Кем выдан" />

      <label for="">Дата выдачи*</label>
      <input type="date" v-model="form.dateIssue" placeholder="Дата выдачи" />
      <span v-if="v$.form.dateIssue.$error">
        {{v$.form.dateIssue.$errors[0].$message}}
      </span>

      <button @click="register" type="button">Зарегестрироваться</button>
    </form>
  </div>
</template>

<script>
import useVuelidate from "@vuelidate/core";
import { required, minLength, maxLength, helpers } from "@vuelidate/validators";

export default {
  data() {
    return {
      v$: useVuelidate(),
      form: {
        secondName: "",
        name: "",
        patronymic: "",
        birthday: "",
        phone: "",
        sex: "",
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
        }
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
.container {
  margin: 0 auto;
  max-width: 1200px;
  padding: 0 15px;
}
label {
  margin-top: 10px;
}
.form {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
</style>