<template>
    <div>
        <div id="login">
            <h1>Login</h1>
            Login: <input type="text" name="username" v-model="input.username" placeholder="Username" />
            Password: <input type="password" name="password" v-model="input.password" placeholder="Password" />
            <div class="log-butt">
                <button type="button" v-on:click="login()">Login</button>
                <a href="#">Forgot password</a>
            </div>
        </div>
        <div class="hint">
          <h2>Hint</h2>
           <p>Login: nraboy</p>
           <p>Password: password</p>
        </div>
    </div>    
</template>

<script>
export default {
  name: "Login",
  data () {
    return {
      input: {
        username: "",
        password: ""
      }
    };
  },
  methods: {
    login () {
      if (this.input.username != "" && this.input.password != "") {
        if (
          this.input.username == this.$parent.mockAccount.username &&
          this.input.password == this.$parent.mockAccount.password
        ) {
          this.$emit("authenticated", true)
          this.$router.replace({ name: "secure" })
        } else {
          console.log("The username and / or password is incorrect")
        }
      } else {
        console.log("A username and password must be present")
      }
    }
  }
}
</script>