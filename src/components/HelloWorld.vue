<template>
  <nav class="navbar" role="naNPPvigation" aria-label="main navigation">
        <div class="navbar-brand">
            <a class="navbar-item" href="https://bulma.io">
                <img src="https://bulma.io/images/bulma-logo.png" width="112" height="28">
            </a>

            <a role="button" class="navbar-burger" aria-label="menu" aria-expanded="false"
                data-target="navbarBasicExample">
                <span aria-hidden="true"></span>
                <span aria-hidden="true"></span>
                <span aria-hidden="true"></span>
            </a>
        </div>

        <div id="navbarBasicExample" class="navbar-menu">
            <div class="navbar-start">
                <a class="navbar-item" href="/">
                    Home
                </a>

                <a class="navbar-item" href="/documentation">
                    Documentation
                </a>

                <div class="navbar-item has-dropdown is-hoverable">
                    <a class="navbar-link">
                        More
                    </a>

                    <div class="navbar-dropdown">
                        <a class="navbar-item" href="/about">
                            About
                        </a>                                            
                        <a class="navbar-item" href="/ui-module">
                            UI module
                        </a>                        
                    </div>
                </div>
            </div>

            <div class="navbar-end">
                <div class="navbar-item">
                    <div class="buttons">
                        <a class="button is-primary" @click="signUp">
                            <strong>Sign up</strong>
                        </a>
                        <a class="button is-light" id="login-btn" @click="login">
                            Log in
                        </a>
                    </div>
                </div>
            </div>
        </div>
    </nav>
</template>

<script>
import { MessageBus } from "@podium/browser";
const messageBus = new MessageBus();

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  methods:{
    login(){
      messageBus.publish('internalchannel', 'login', {message: 'open-login', from: 'vue header', tab: 0});
      this.$emit('login','open-login')
      console.log('emit event: open-login', 'login')
    },
    signUp(){
      messageBus.publish('internalchannel', 'login', {message: 'open-login', from: 'vue header', tab: 1});
      this.$emit('login','open-signUp')
      console.log('emit event: open-signUp', 'login')
    }
  }
}
</script>


