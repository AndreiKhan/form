<template>
  <div class="form center">
    <form @submit.prevent="submit" class="form_client">
      <div class="form_client__inputField">
        <label class="form_client__inputField__label" for="lastName">Фамилия</label>
        <input 
          id="lastName"
          type="text" 
          v-model.trim="lastName"
          class="form_client__inputField__input"
          :class="{error: $v.lastName.$dirty && !$v.lastName.required}"
        > 
        <small v-if="$v.lastName.$dirty && !$v.lastName.required" class="form_client__inputField__small">Это поле обязательно для заполнения</small>
      </div>

      <div class="form_client__inputField">
        <label class="form_client__inputField__label" for="firstName">Имя</label>
        <input 
          id="firstName"
          type="text" 
          v-model.trim="firstName"
          class="form_client__inputField__input"
          :class="{error: $v.firstName.$dirty && !$v.firstName.required}"
        > 
        <small v-if="$v.firstName.$dirty && !$v.firstName.required" class="form_client__inputField__small">Это поле обязательно для заполнения</small>
      </div>

      <div class="form_client__inputField">
        <label class="form_client__inputField__label" for="surname">Отчество</label>
        <input 
          id="surname"
          type="text" 
          v-model.trim="surname"
          class="form_client__inputField__input"
        >
      </div>

      <div class="form_client__inputField">
        <label class="form_client__inputField__label" for="birthDay">Дата рождения</label>
        <input 
          id="birthDay"
          type="date" 
          v-model.trim="birthDay"
          class="form_client__inputField__input inputDate"
          :class="{error: $v.birthDay.$dirty && !$v.birthDay.required}"
        >
        <small v-if="$v.birthDay.$dirty && !$v.birthDay.required" class="form_client__inputField__small">Это поле обязательно для заполнения</small>
      </div>

      <div class="form_client__inputField">
        <label class="form_client__inputField__label" for="phone">Номер телефона</label>
        <input 
          id="phone"
          type="text" 
          v-model.trim="phone"
          class="form_client__inputField__input"
          :class="{error: $v.phone.$dirty && (!$v.phone.required || 
                                              !$v.phone.numeric || 
                                              !$v.phone.isPhone || 
                                              !$v.phone.minLength || 
                                              !$v.phone.maxLength)}"
        >
        <small v-if="$v.phone.$dirty && !$v.phone.required" class="form_client__inputField__small">Это поле обязательно для заполнения</small>
        <small v-else-if="$v.phone.$dirty && (!$v.phone.minLength || !$v.phone.numeric || !$v.phone.maxLength)" 
          class="form_client__inputField__small">Введен некорректный номер телефона</small>
        <small v-else-if="!$v.phone.isPhone" class="form_client__inputField__small">Номер должен начинаться с 7</small>
      </div>

      <div class="form_client__inputField">
        <label class="form_client__inputField__label" for="sex">Пол</label>
        <input 
          id="sex"
          name="sex"
          type="text"
          v-model.trim="sex"
          class="form_client__inputField__input"
        >
      </div>

      <div class="form_client__inputField">
        <label class="form_client__inputField__label" for="group">Группа клиентов</label>
        <select
          multiple
          size="3"
          id="group"
          type="text" 
          v-model.trim="group"
          class="form_client__inputField__input selectMulti"
          :class="{error: $v.group.$dirty && !$v.group.required}"
        >
          <option class="form_client__inputField__input__option" value="vip">VIP</option>
          <option class="form_client__inputField__input__option" value="problem">Проблемные</option>
          <option class="form_client__inputField__input__option" value="mmc">ОМС</option>
        </select>
        <small v-if="$v.group.$dirty && !$v.group.required" class="form_client__inputField__small">Это поле обязательно для заполнения</small>
      </div>

      <div class="form_client__inputField">
        <label class="form_client__inputField__label" for="therapist">Лечащий врач</label>
        <select
          id="therapist"
          type="text" 
          v-model.trim="therapist"
          class="form_client__inputField__input select"
        >
          <option class="form_client__inputField__input__option" value="ivanov">Иванов</option>
          <option class="form_client__inputField__input__option" value="zakharov">Захаров</option>
          <option class="form_client__inputField__input__option" value="chernisheva">Чернышева</option>
        </select>
      </div>

      <div class="form_client__inputField sms">
        <label class="form_client__inputField__label" for="sms">Не отправлять СМС</label>
        <input
          id="sms"
          type="checkbox" 
          v-model.trim="sms"
          class="form_client__inputField__checkBox"
        >
      </div>

      <h2 class="form_client__header">Адрес:</h2>

      <div class="form_client__inputField">
        <label class="form_client__inputField__label" for="index">Индекс</label>
        <input
          id="index"
          type="text" 
          v-model.trim="index"
          class="form_client__inputField__input"
          :class="{error: !$v.index.numeric}"
        >
        <small v-if="!$v.index.numeric" class="form_client__inputField__small">Поле только для цифр</small>
      </div>

      <div class="form_client__inputField">
        <label class="form_client__inputField__label" for="country">Страна</label>
        <input
          id="country"
          type="text" 
          v-model.trim="country"
          class="form_client__inputField__input"
        >
      </div>

      <div class="form_client__inputField">
        <label class="form_client__inputField__label" for="region">Область</label>
        <input
          id="region"
          type="text"
          v-model.trim="region"
          class="form_client__inputField__input"
        >
      </div>

      <div class="form_client__inputField">
        <label class="form_client__inputField__label" for="city">Город</label>
        <input
          id="city"
          type="text" 
          v-model.trim="city"
          class="form_client__inputField__input"
          :class="{error: $v.city.$dirty && !$v.city.required}"
        >
        <small v-if="$v.city.$dirty && !$v.city.required" class="form_client__inputField__small">Это поле обязательно для заполнения</small>
      </div>

      <div class="form_client__inputField">
        <label class="form_client__inputField__label" for="street">Улица</label>
        <input
          id="street"
          type="text" 
          v-model.trim="street"
          class="form_client__inputField__input"
        >
      </div>

      <div class="form_client__inputField">
        <label class="form_client__inputField__label" for="house">Дом</label>
        <input
          id="house"
          type="text" 
          v-model.trim="house"
          class="form_client__inputField__input"
        >
      </div>

      <h2 class="form_client__header">Паспорт:</h2>

      <div class="form_client__inputField">
        <label class="form_client__inputField__label" for="document">Тип документа</label>
        <select
          id="document"
          type="text" 
          v-model.trim="document"
          class="form_client__inputField__input select"
          :class="{error: $v.document.$dirty && !$v.document.required}"
        >
          <option class="form_client__inputField__input__option" value="passport">Паспорт</option>
          <option class="form_client__inputField__input__option" value="birthCertificate">Свидетельство о рождении</option>
          <option class="form_client__inputField__input__option" value="driversLicense">Вод. удостоверение</option>
        </select>
        <small v-if="$v.document.$dirty && !$v.document.required" class="form_client__inputField__small">Это поле обязательно для заполнения</small>
      </div>

      <div class="form_client__inputField">
        <label class="form_client__inputField__label" for="series">Серия</label>
        <input
          id="series"
          type="text" 
          v-model.trim="series"
          class="form_client__inputField__input"
          :class="{error: !$v.series.numeric}"
        >
        <small v-if="!$v.series.numeric" class="form_client__inputField__small">Поле только для цифр</small>
      </div>

      <div class="form_client__inputField">
        <label class="form_client__inputField__label" for="number">Номер</label>
        <input
          id="number"
          type="text" 
          v-model.trim="number"
          class="form_client__inputField__input"
          :class="{error: !$v.number.numeric}"
        >
        <small v-if="!$v.number.numeric" class="form_client__inputField__small">Поле только для цифр</small>
      </div>

      <div class="form_client__inputField">
        <label class="form_client__inputField__label" for="issued">Кем выдан</label>
        <input
          id="issued"
          type="text" 
          v-model.trim="issued"
          class="form_client__inputField__input"
        >
      </div>

      <div class="form_client__inputField">
        <label class="form_client__inputField__label" for="issueDate">Дата выдачи</label>
        <input
          id="issueDate"
          type="date" 
          v-model.trim="issueDate"
          class="form_client__inputField__input"
          :class="{error: $v.issueDate.$dirty && !$v.issueDate.required}"
        >
        <small v-if="$v.issueDate.$dirty && !$v.issueDate.required" class="form_client__inputField__small">Это поле обязательно для заполнения</small>
      </div>

      <button class="form_client__submitButton" type="submit">
        Зарегистрироваться
      </button>
      <p v-if="success" class="form_client__inputField__small success">Форма успешно отправлена</p>
    </form>
  </div>
</template>

<script>
import {required, minLength, maxLength, numeric} from 'vuelidate/lib/validators'

const isPhone = (value) => value[0] == 7

export default {
  name: 'FormComp',
  data() {
    return {
        lastName: '',
        firstName: '',
        surname: '',
        birthDay: '',
        phone: '',
        sex: '',
        group: [],
        therapist: '',
        sms: '',
        index: '',
        country: '',
        region: '',
        city: '',
        street: '',
        house: '',
        document: '',
        series: '',
        number: '',
        issued: '',
        issueDate: '',
        success: false,
    };
  },

  validations: {
    lastName: {required},
    firstName: {required},
    birthDay: {required},
    phone: {required, minLength: minLength(11), maxLength: maxLength(11), numeric, isPhone},
    group: {required},
    index: {numeric},
    city: {required},
    document: {required},
    series: {numeric},
    number: {numeric},
    issueDate: {required},
  },

  methods: {
    submit() {
      if (this.$v.$invalid) {
        this.$v.$touch()
        return
      }

      this.success = true
      const formData = {
        lastName: this.lastName,
        firstName: this.firstName,
        surname: this.surname,
        birthDay: this.birthDay,
        phone: this.phone,
        sex: this.sex,
        group: this.group,
        therapist: this.therapist,
        sms: this.sms,
        index: this.index,
        country: this.country,
        region: this.region,
        city: this.city,
        street: this.street,
        house: this.house,
        document: this.document,
        series: this.series,
        number: this.number,
        issued: this.issued,
        issueDate: this.issueDate,
      }
      
      console.log(formData)
    },
  }
};
</script>

<style lang="sass" scoped>
.form
  width: 100%
  max-width: 500px
  min-width: 270px
  margin: 40px
  font-family: sans-serif

  &_client
    border-radius: 20px
    box-shadow: 0px 0px 43px 3px rgba(0, 0, 0, 0.31)
    display: flex
    flex-direction: column
    gap: 20px
    padding: 20px

    &__header
      padding-top: 10px

    &__submitButton
      margin-top: 10px
      height: 45px
      border: none
      border-radius: 10px
      background-color: blue
      font-size: 22px
      color: white
      transition: transform 0.3s

      &:hover
        cursor: pointer
        transform: scale(1.02)

      &:active
        filter: brightness(0.8)

    &__inputField
      display: flex
      flex-direction: column
      align-items: flex-start

      &__checkBox
        width: 20px
        height: 20px

        &:hover
          cursor: pointer

      &__input
        box-sizing: border-box
        margin-top: 5px
        padding: 10px
        width: 100%
        border: none
        border-radius: 10px
        box-shadow: 0px 0px 8px 2px rgba(0, 0, 0, 0.31)
        outline: none
        transition: transform 0.3s

        &:hover
          transform: scale(1.03)
      
      &__small
        padding-top: 5px 
        color: red

.error
  box-shadow: 0px 0px 8px 2px rgba(255, 0, 0, 0.31)

.sms
  flex-direction: row
  gap: 15px
  align-items: center

.success
  color: blue
</style>