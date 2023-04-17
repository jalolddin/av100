<template>
  <div>
      <h2 class="title">Настройки</h2>
      <div class="settings">

        <!-- Call SIP -->
        <div class="settings__call">
              <div class="switch">  
                <h2>Звонок через SIP</h2>
                <switches v-model="call" theme="bootstrap" color="success" type-bold="true"></switches>
              </div>
              <p>Включите эту функцию чтобы Авито и другие площадки не блокировали ваш аккаунт. Будет выглядеть так, будто звонки совершаются с разных номеров.</p>
        </div>

        <!-- User Data -->
        <div class="settings__account">
            <h2>Учётная запись</h2>
            <div class="form">
                <div>
                    <label for="title">Компания</label>
                    <input v-model="companyName" type="text">
                </div>
                <div>
                    <label for="login">Логин</label>
                    <input v-model="login" type="text">
                </div>
                <div>
                    <label for="number">Номер <br> телефона</label>
                    <input v-model="phoneNumber" type="number">
                </div>
                <div>
                    <label for="name">Имя</label>
                    <input v-model="firstName" type="text">
                </div>
                <div>
                    <label for="name">Фамилия</label>
                    <div>
                        <input v-model="lastName" type="text">
                        <span>* Не обязательно</span>
                    </div>
                </div>
            </div>
        </div>

        <!-- Notification -->
        <div class="settings__notifications">
            <h2>Оповещения о новых <br> подборках</h2>
            <div class="settings__notifications__right">
                  <p>Выберите, куда будут приходить уведомления при появлении <br> автомобилей, которые подходят под критерии вашей подборки.</p>
                  <span>Уведомления</span>
                 <div class="settings__notifications__right__radio">
                  <!-- OFF -->
                   <div>
                        <div>
                          <input value="0" v-model="notification" type="radio">
                          <label for="value">Выкл</label>
                        </div>
                    </div>
                    <div class="line"></div>
                    <!-- PUSH -->
                    <div>
                      <div>
                        <input  value="1" v-model="notification" type="radio">
                        <label for="value">Push</label>
                      </div>
                      <div class="tooltip">
                        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <circle cx="12" cy="12" r="9" stroke="#686869" stroke-width="2"/>
                            <path d="M12.5 7.5C12.5 7.77614 12.2761 8 12 8C11.7239 8 11.5 7.77614 11.5 7.5C11.5 7.22386 11.7239 7 12 7C12.2761 7 12.5 7.22386 12.5 7.5Z" fill="#33363F" stroke="#33363F"/>
                            <path d="M12 17V10" stroke="#686869" stroke-width="2"/>
                        </svg>
                        <span class="tooltiptext">Можно установить только в приложении</span>
                      </div>
                    </div>
                    <div class="line"></div>
                    <!-- EMAIL -->
                    <div class="emailInput">
                        <div>
                          <input  value="2" v-model="notification" type="radio">
                          <label for="value">Email</label>
                        </div>
                        <!-- Unvisibleinputs -->
                        <input  v-model="email" v-if="emailVisible" type="text">
                        <input :readonly="true" :class="{removeApperance: true}" v-model="email" v-else>
                        <div v-if="!emailVisible" @click="emailVisible =! emailVisible">
                          <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                              <path d="M16.9393 7.23223L16.5858 7.58579L16.9393 7.23223L16.7678 7.06066L16.7445 7.03738C16.4311 6.72395 16.1611 6.45388 15.9157 6.2667C15.6528 6.0661 15.3604 5.91421 15 5.91421C14.6396 5.91421 14.3472 6.0661 14.0843 6.2667C13.8389 6.45388 13.5689 6.72395 13.2555 7.03739L13.2322 7.06066L6.03816 14.2547C6.02714 14.2658 6.01619 14.2767 6.00533 14.2875C5.84286 14.4496 5.69903 14.5932 5.59766 14.7722C5.4963 14.9512 5.44723 15.1484 5.39179 15.3711C5.38809 15.386 5.38435 15.401 5.38057 15.4162L4.71704 18.0703C4.71483 18.0791 4.7126 18.088 4.71036 18.097C4.67112 18.2537 4.62921 18.421 4.61546 18.5615C4.60032 18.7163 4.60385 18.9773 4.81326 19.1867C5.02267 19.3961 5.28373 19.3997 5.43846 19.3845C5.57899 19.3708 5.74633 19.3289 5.90301 19.2896C5.91195 19.2874 5.92085 19.2852 5.92971 19.283L5.92972 19.283L5.95149 19.2775L5.95151 19.2775L8.58384 18.6194C8.59896 18.6156 8.61396 18.6119 8.62885 18.6082C8.85159 18.5528 9.04877 18.5037 9.2278 18.4023C9.40683 18.301 9.55035 18.1571 9.71248 17.9947C9.72332 17.9838 9.73425 17.9729 9.74527 17.9618L16.9393 10.7678L16.9393 10.7678L16.9626 10.7445C17.2761 10.4311 17.5461 10.1611 17.7333 9.91573C17.9339 9.65281 18.0858 9.36038 18.0858 9C18.0858 8.63961 17.9339 8.34719 17.7333 8.08427C17.5461 7.83894 17.276 7.5689 16.9626 7.2555L16.9393 7.23223Z" stroke="#2DC574"/>
                              <path d="M12.5 7.5L15.5 5.5L18.5 8.5L16.5 11.5L12.5 7.5Z" fill="#2DC574"/>
                          </svg>
                        </div>
                    </div>
                    <div class="line"></div>
                    <!-- TELEGRAM -->
                    <div class="telegramInput">
                        <div>
                          <input value="3" v-model="notification" type="radio">
                          <label for="value">Telegram ID</label>
                        </div>
                        <!-- Unvisibleinputs -->
                        <input  v-model="telegram" v-if="telegramVisible" type="text">
                        <input :readonly="true" :class="{removeApperance: true}" v-model="telegram" v-else>
                        <div v-if="!telegramVisible" @click="telegramVisible =! telegramVisible">
                          <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                              <path d="M16.9393 7.23223L16.5858 7.58579L16.9393 7.23223L16.7678 7.06066L16.7445 7.03738C16.4311 6.72395 16.1611 6.45388 15.9157 6.2667C15.6528 6.0661 15.3604 5.91421 15 5.91421C14.6396 5.91421 14.3472 6.0661 14.0843 6.2667C13.8389 6.45388 13.5689 6.72395 13.2555 7.03739L13.2322 7.06066L6.03816 14.2547C6.02714 14.2658 6.01619 14.2767 6.00533 14.2875C5.84286 14.4496 5.69903 14.5932 5.59766 14.7722C5.4963 14.9512 5.44723 15.1484 5.39179 15.3711C5.38809 15.386 5.38435 15.401 5.38057 15.4162L4.71704 18.0703C4.71483 18.0791 4.7126 18.088 4.71036 18.097C4.67112 18.2537 4.62921 18.421 4.61546 18.5615C4.60032 18.7163 4.60385 18.9773 4.81326 19.1867C5.02267 19.3961 5.28373 19.3997 5.43846 19.3845C5.57899 19.3708 5.74633 19.3289 5.90301 19.2896C5.91195 19.2874 5.92085 19.2852 5.92971 19.283L5.92972 19.283L5.95149 19.2775L5.95151 19.2775L8.58384 18.6194C8.59896 18.6156 8.61396 18.6119 8.62885 18.6082C8.85159 18.5528 9.04877 18.5037 9.2278 18.4023C9.40683 18.301 9.55035 18.1571 9.71248 17.9947C9.72332 17.9838 9.73425 17.9729 9.74527 17.9618L16.9393 10.7678L16.9393 10.7678L16.9626 10.7445C17.2761 10.4311 17.5461 10.1611 17.7333 9.91573C17.9339 9.65281 18.0858 9.36038 18.0858 9C18.0858 8.63961 17.9339 8.34719 17.7333 8.08427C17.5461 7.83894 17.276 7.5689 16.9626 7.2555L16.9393 7.23223Z" stroke="#2DC574"/>
                              <path d="M12.5 7.5L15.5 5.5L18.5 8.5L16.5 11.5L12.5 7.5Z" fill="#2DC574"/>
                          </svg>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        
        <!-- About Card -->
        <div class="settings__card">
            <h2>Переход в карточку</h2>
            <div class="settings__card__right">
              <p>Выберите, каким образом будет открываться детальное <br> представление выбранного вами транспорта.</p>
                <div class="settings__card__right__radio">
                    <div>
                      <input v-model="redirect" value="0" type="radio">
                      <label for="value">В карточку в текущем окне</label>
                    </div>
                    <div class="line"></div>
                    <div>
                      <input v-model="redirect" value="1" type="radio">
                      <label for="value">В карточку в отдельном окне</label>
                    </div>
                    <div class="line"></div>
                    <div class="tooltip__content">
                        <div>
                          <input v-model="redirect" value="2" type="radio">
                          <label for="value">На источник </label>
                        </div>
                        <div class="tooltip">
                          <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                              <circle cx="12" cy="12" r="9" stroke="#686869" stroke-width="2"/>
                              <path d="M12.5 7.5C12.5 7.77614 12.2761 8 12 8C11.7239 8 11.5 7.77614 11.5 7.5C11.5 7.22386 11.7239 7 12 7C12.2761 7 12.5 7.22386 12.5 7.5Z" fill="#33363F" stroke="#33363F"/>
                              <path d="M12 17V10" stroke="#686869" stroke-width="2"/>
                          </svg>
                          <span class="tooltiptext">Прямой переход в объявление на источнике</span>
                        </div>
                    </div>
               </div>
            </div>
        </div>

        <!-- Another settings -->
        <div class="settings__another">
            <h2>Прочие настройки</h2>
            <div class="settings__another__right">
              <div class="settings__another__right__select">
                  <p>Часовой пояс</p>
                  <select v-model="timezone" name="" id="">
                    <option>{{ timezone }}</option>
                  </select>
              </div>
              <div class="settings__another__right__checkbox">
                <div>
                  <div>
                    <input v-model="automate" type="checkbox">
                    <label for="title">Автоматически переходить к новым <br> объявлениям</label>
                  </div>
                  <div class="tooltip">
                          <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                              <circle cx="12" cy="12" r="9" stroke="#686869" stroke-width="2"/>
                              <path d="M12.5 7.5C12.5 7.77614 12.2761 8 12 8C11.7239 8 11.5 7.77614 11.5 7.5C11.5 7.22386 11.7239 7 12 7C12.2761 7 12.5 7.22386 12.5 7.5Z" fill="#33363F" stroke="#33363F"/>
                              <path d="M12 17V10" stroke="#686869" stroke-width="2"/>
                          </svg>
                          <span class="tooltiptext">Лента будет автоматически обновляться 1 раз в 3 секунды</span>
                  </div>
                </div>
                <div>
                  <div>
                    <input v-model="colorMethod" type="checkbox">
                    <label for="title">Включить цвета в ленте</label>
                  </div>
                  <div class="tooltip">
                      <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                          <circle cx="12" cy="12" r="9" stroke="#686869" stroke-width="2"/>
                          <path d="M12.5 7.5C12.5 7.77614 12.2761 8 12 8C11.7239 8 11.5 7.77614 11.5 7.5C11.5 7.22386 11.7239 7 12 7C12.2761 7 12.5 7.22386 12.5 7.5Z" fill="#33363F" stroke="#33363F"/>
                          <path d="M12 17V10" stroke="#686869" stroke-width="2"/>
                      </svg>
                      <span class="tooltiptext">Включение зеленого/желтого цвета</span>
                  </div>
                </div>
              </div>
              <div class="line"></div>
              
              <notifications group="foo" position="top center" />
              <button  @click="updateData">Сохранить</button>
          </div>
        </div>
      </div>
  </div>
</template>

<script>
import axios from 'axios'
import Switches from 'vue-switches';
export default {
  name: 'Settings',
  components: {
    Switches
  },
  data(){
    return {
      emailVisible: false,
      telegramVisible: false,
      userToken: null,
      userId: null,
      call: true,
      companyName: null,
      login: null,
      phoneNumber: null,
      firstName: null,
      lastName: null,
      email: null,
      telegram: null,
      timezone: null,
      notification: null,
      redirect: null,
      colorMethod: null,
      automate: null,
      apiKey: '8bcfb6e1-4fa8-4fae-872c-a435bbdbe8d9',
      loginData: {
        "login": "9615746370",
        "password": "0522852607",
        "fromuser": 0
      },
      headerInfo: {
        headers:{
        'X-Api-Key': '8bcfb6e1-4fa8-4fae-872c-a435bbdbe8d9',
        'X-Device-OS': 'yes'
         }
      },
    }
  },
  // Method for updating user data
  methods:{
    updateData(){
      axios.put(`https://api.av100.ru/v3/user/${this.userId}`, 
        {
          "id": 0,
          "login": this.login,
          "email": this.email,
          "telegramChat": this.telegram,
          "clicks": 0,
          "expire": 0,
          "autoru": 0,
          "phone": this.phoneNumber,
          "sendMethod": 2,
          "lname": this.lastName,
          "fname": this.firstName,
          "timezone": this.timezone,
          "timezonestring": null,
          "notifytype": this.notification,
          "notifytypestring": null,
          "companyid": 0,
          "companyname": this.companyName,
          "calltype": null,
          "enableaudio": this.call,
          "locklentaupdate": true,
          "erased": 0,
          "os": null,
          "sipid": null,
          "updatePeriod": 0,
          "filterMaxCount": 0,
          "turbosip": null,
          "turbosip5accessto": null,
          "turbosip20accessto": null,
          "colorlenta": this.colorMethod,
          "ignoreavg": this.automate,
          "redirecttarget": this.redirect,
          "lentacolortype": 0
      },
      {
        headers: {
        'X-Api-Key': this.apiKey,
        'X-User-Token': this.userToken,
        'X-Device-OS': 'yes'
      }
      }).then((res) => {
        this.$notify({
        type: 'success',
        group: 'foo',
        title: 'Сохранено',
        text: 'Данные сохранены'
        });
      })
    }
  },
  // First hook for getting user data 
  created(){
  axios.post('https://api.av100.ru/v3/login', this.loginData, this.headerInfo).then((res) => {
    this.userToken = res.data.token
    this.userId = res.data.user.id
    axios.get(`https://api.av100.ru/v3/user`, {
      headers: {
        'userId': this.userId,
        'X-Api-Key': this.apiKey,
        'X-Device-OS': 'yes',
        'X-User-Token': this.userToken

      }
    }).then((res) => {
      console.log(res.data)
      this.companyName = res.data.companyname
      this.login = res.data.login
      this.phoneNumber = res.data.phone
      this.firstName = res.data.fname 
      this.lastName = res.data.lname
      this.timezone = res.data.timezonestring
      this.notification = res.data.notifytype 
      this.redirect = res.data.redirecttarget
      this.colorMethod = res.data.colorlenta
      this.automate = res.data.ignoreavg
      this.email = res.data.email
      this.telegram = res.data.telegramChat
      this.call = res.data.enableaudio
      }).catch(error => console.log(error))
  }).catch(error => console.log(error))
  }
}
</script>

