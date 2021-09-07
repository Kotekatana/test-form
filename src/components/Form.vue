<template>
    <div class="container">
            <div class="card marked" v-if="success">
                новый клиент успешно создан
            </div>
            <form  @submit.prevent="submitHandler">
                <div class="card">
                    <div class="form-control" :class="{invalid: ($v.surname.$dirty && !$v.surname.required) }" >
                        <label for="surname">Фамилия <span class="required">*</span></label>
                        <input type="text" id="surname" v-model="surname">
                        <small v-if="$v.surname.$dirty && !$v.surname.required">Поле не должно быть пустым</small>
                    </div>

                    <div class="form-control" :class="{invalid: ($v.name.$dirty && !$v.name.required) }" >
                        <label for="name">Имя <span class="required">*</span></label>
                        <input type="text" id="name" v-model="name">
                        <small v-if="$v.name.$dirty && !$v.name.required">Поле не должно быть пустым</small>
                        <small></small>
                    </div>

                    <div class="form-control" >
                        <label for="patronymic">Отчество</label>
                        <input type="text" id="patronymic" >
                        <small ></small>
                        <small></small>
                    </div>
                    <div class="form-control" :class="{invalid: ($v.dateOfBirth.$dirty && !$v.dateOfBirth.required) }">
                        <label for="dateOfBirth">Дата рождения <span class="required">*</span></label>
                        <input type="date" id="dateOfBirth" v-model="dateOfBirth">
                        <small v-if="$v.dateOfBirth.$dirty && !$v.dateOfBirth.required">Поле не должно быть пустым</small>

                    </div>
                    <div class="form-control" :class="{invalid: ($v.phoneNumber.$dirty && !$v.phoneNumber.required) || ($v.phoneNumber.$dirty && !$v.phoneNumber.minLength) ||($v.phoneNumber.$dirty && !$v.phoneNumber.maxLength) }">
                        <label for="phoneNumber">Номер телефона <span class="required">*</span></label>
                        <input type="tel" id="phoneNumber" v-model="phoneNumber" placeholder="7(987)654-32-10">
                        <small v-if="$v.phoneNumber.$dirty && !$v.phoneNumber.required">Поле не должно быть пустым</small>
                        <small v-if="($v.phoneNumber.$dirty && !$v.phoneNumber.minLength) || ($v.phoneNumber.$dirty && !$v.phoneNumber.maxLength)">Номер введен некорректно</small>
                    </div>
                    <div class="form-control" >
                        <label for="sex">Пол</label>
                        <input type="tel" id="sex">
                        <small ></small>
                        <small></small>
                    </div>
                    <div class="form-control" :class="{invalid: $v.clientGroup.$dirty && !$v.clientGroup.required }">
                        <label for="clientGroup">Группа клиентов <span class="required">*</span></label>
                        <select name="clientGroup" id="clientGroup" multiple v-model="clientGroup">
                            <option value="VIP">VIP</option>
                            <option value="Проблемные">Проблемные</option>
                            <option value="ОМС">ОМС</option>
                        </select>
                        <small v-if="$v.clientGroup.$dirty && !$v.clientGroup.required">Поле не должно быть пустым</small>
                        <small></small>
                    </div>
                    <div class="form-control" >
                        <label for="doctor">Лечащий врач</label>
                        <select name="doctor" id="doctor" >
                            <option value="">Иванов</option>
                            <option value="">Захаров</option>
                            <option value="">Чернышева</option>
                        </select>
                        <small ></small>
                        <small></small>
                    </div>
                    <div class="form-checkbox">
                        <label for="sendSMS">Не отправлять смс</label>
                        <input  class="checkbox" type="checkbox" id="sendSMS">
                    </div>

                </div>
                <div class="card">
                    <div class="form-control" >
                        <label for="index">Индекс</label>
                        <input type="text" id="index">
                        <small ></small>
                        <small></small>
                    </div>

                    <div class="form-control" >
                        <label for="sex">Страна</label>
                        <input type="text" id="sex">
                        <small ></small>
                        <small></small>
                    </div>

                    <div class="form-control" >
                        <label for="region">Область</label>
                        <input type="text" id="region">
                        <small ></small>
                        <small></small>
                    </div>

                    <div class="form-control" :class="{invalid: ($v.dateOfBirth.$dirty && !$v.dateOfBirth.required) }">
                        <label for="city">Город <span class="required">*</span></label>
                        <input type="text" id="city" v-model="city">
                        <small v-if="$v.dateOfBirth.$dirty && !$v.dateOfBirth.required">Поле не должно быть пустым</small>

                    </div>

                    <div class="form-control" >
                        <label for="street">Улица</label>
                        <input type="text" id="street">
                        <small ></small>
                        <small></small>
                    </div>

                    <div class="form-control" >
                        <label for="home">Дом</label>
                        <input type="text" id="home">
                        <small ></small>
                        <small></small>
                    </div>

                </div>

                <div class="card">
                    <div class="form-control" >
                        <label for="document">Тип документа <span class="required">*</span></label>
                        <select name="document" id="document" >
                            <option value="Паспорт">Паспорт</option>
                            <option value="Свидетельство о рождении">Свидетельство о рождении</option>
                            <option value="Вод. удостоверение">Вод. удостоверение</option>
                        </select>
                        <small ></small>
                        <small></small>
                    </div>

                    <div class="form-control" >
                        <label for="home">Серия</label>
                        <input type="number" id="home">
                        <small ></small>
                        <small></small>
                    </div>

                    <div class="form-control" >
                        <label for="home">Номер</label>
                        <input type="number" id="home">
                        <small ></small>
                        <small></small>
                    </div>

                    <div class="form-control" >
                        <label for="organization">Кем выдан</label>
                        <input type="text" id="organization">
                        <small ></small>
                        <small></small>
                    </div>

                    <div class="form-control" :class="{invalid: ($v.issueDate.$dirty && !$v.issueDate.required) }">
                        <label for="issueDate">Дата выдачи <span class="required">*</span></label>
                        <input type="date" id="issueDate"  v-model="issueDate">
                        <small v-if="$v.issueDate.$dirty && !$v.issueDate.required">Поле не должно быть пустым</small>
                        <small></small>
                    </div>
                </div>

                <div class="card">
                    <button class="btn primary" type="submit">Отправить</button>
                </div>

            </form>

        </div>

</template>

<script>
import {email, required ,minLength, maxLength} from 'vuelidate/lib/validators'
export default {
    data(){
        return{
            success:false,
            email:'',
            password:'',
            surname:'',
            name:'',
            dateOfBirth: '',
            phoneNumber:'',
            clientGroup:[],
            city:'',
            issueDate:''

        }
    },
    validations:{
        surname:{required},
        name:{required},
        dateOfBirth:{required},
        phoneNumber:{required,minLength:minLength(11),maxLength:maxLength(11)},
        clientGroup:{required},
        city:{required},
        issueDate:{required}

    },
    methods:{
        submitHandler(){
            if(this.$v.$invalid){
                this.$v.$touch()
                return
            }else{
                console.log(this.$v.$invalid)

                this.success= true
                document.documentElement.scrollTop = 0
            }
        },
    },

}
</script>


<style lang="sass">
.required
    color: red

@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&display=swap');

*
    box-sizing: border-box

body
    font-family: Inter, Roboto, Oxygen, Fira Sans, Helvetica Neue, sans-serif

    font-size: 16px
    color: #2c3e50
    background: #2c3e50

.btn
    color: #42b983
    position: relative
    place-content: center
    place-items: center
    width: fit-content
    border-radius: 99px
    letter-spacing: 0.05em
    border: 1px solid #42b983
    text-decoration: none
    text-transform: uppercase
    margin-right: 10px
    padding: 0.5rem 1.5rem
    white-space: nowrap
    font-weight: 700
    outline: none
    background: #fff
    transition: all 0.22s
    &:hover
        cursor: pointer
        opacity: 0.8
    &:active
        box-shadow: inset 1px 1px 1px rgba(0, 0, 0, 0.3)
    &.primary
        background: #42b983
        color: #fff

.container
    margin: 0 auto
    max-width: 1000px
    position: relative

.form-control
    position: relative
    margin-bottom: 0.5rem
    input,select,textarea
        font-family: Inter, Roboto, Oxygen, Fira Sans, Helvetica Neue, sans-serif
        margin: 0
        outline: none
        border: 2px solid #ccc
        display: block
        width: 100%
        color: #2c3e50
        padding: 0.5rem 1.5rem
        border-radius: 3px
        font-size: 1rem
        resize: none
    small
        color: #e53935
    &.invalid input
        border-color: #e53935
    &.invalid select
        border-color: #e53935
    label
        display: block
        margin: 0 0 0.3rem 0.3rem
        font-weight: 500
    input:active, input:focus
        transition: border 0.22s
        border: 2px solid #42b983

.form-checkbox
    margin-bottom: 1rem
    &.label
        display: block
        margin: 0 0 0.3rem 0.3rem
        font-weight: 500
    &.checkbox input
        margin-right: 1rem

.card
    overflow: hidden
    padding: 1rem
    margin-bottom: 1rem
    border-radius: 10px
    box-shadow: 2px 3px 10px rgba(0, 0, 0, 0.2)
    background: #fff
    &.center
        display: flex
        flex-direction: column
        align-items: center
    &-title
        display: flex
        justify-content: space-between
        align-items: center
    &.marked
        border: 4px solid #42b983

</style>