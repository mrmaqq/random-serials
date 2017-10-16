<template>
  <div>
    <div class="container-fluid navbar-inverse bg-inverse">
      <div class="row">
        <div class="col">
          <nav class="navbar">
            <form class="form-inline d-flex justify-content-end">
             <div v-if="!signComplete">
               <router-link to="/sign-in">
                <button class="btn btn-outline-success mr-3" type="button" @click="switchSign('sign-in')">Войти</button>
               </router-link>
               <router-link to="/sign-up">
                <button class="btn btn-outline-success" type="button" @click="switchSign('sign-up')">Регистрация</button>
               </router-link>
              </div>
              <div v-else>
                <router-link to="/serials">
                <button class="btn btn-outline-success" type="button">Список сериалов</button>
                </router-link>
                <span class="ml-4">{{ email }}</span>
              </div>
            </form>
          </nav>
        </div>
      </div>
    </div>
    <div class="container">
      <div class="row">
        <div class="col">
          <router-view @addUser="email = $event.email, signComplete = $event.signComplete, userUid = $event.uid" :uid="userUid"></router-view>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import SignIn from './components/SignIn.vue'
import SignUp from './components/SignUp.vue'
import MainPage from './components/MainPage.vue'
export default {
  name: 'app',
  data() {
    return {
      signComplete: false,
      email: '',
      uid: ''
    }
  },
  components: {
    SignIn,
    SignUp,
    MainPage
  },
  methods: {
    switchSign(currentSign) {
      this.sign = currentSign;
    }
  }
}
</script>

<style lang="scss" scoped>
span {
  color: #fff;
}
</style>
