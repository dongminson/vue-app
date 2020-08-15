<template>
  <div class="container">
    <div class="card">
      <md-field>
        <label>Password</label>
        <md-input id="password" v-model="password" type="password"></md-input>
        <md-button @click="copyToClipboard()" class="md-icon-button">
          <md-icon>description</md-icon>
        </md-button>
      </md-field>
      <md-field>
        <label>Length</label>
        <md-input v-model="length" type="number"></md-input>
      </md-field>
      <div>
        <md-checkbox v-model="letters">Letters</md-checkbox>
        <md-checkbox v-model="uppercase">Uppercase</md-checkbox>
        <md-checkbox v-model="numbers">Numbers</md-checkbox>
        <md-checkbox v-model="symbols">Symbols</md-checkbox>
      </div>
      <md-button :disabled="!(this.letters || this.symbols || this.numbers || this.uppercase)" @click="generatePassword()" class="md-primary">Generate</md-button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MainForm',
  data: function() {
    return {
      uppercase: false,
      numbers: false,
      letters: false,
      symbols: false,
      password: '',
      length: 6,
    }
  },
  methods: {
    generatePassword: function() {
      const numbers = '1234567890';
      const letters = 'abcdefghijklmnopqrstuvwyz';
      const uppercase = 'ABCDEFGHIJKLMNOPQRSTUVWYZ';
      const symbols = '!@#$%^&*()';

      let validChars = '';
      if (this.letters) {
        validChars += letters;
      }
      if (this.uppercase) {
        validChars += uppercase;
      }
      if (this.numbers) {
        validChars += numbers;
      }
      if (this.symbols) {
        validChars += symbols;
      }

      let generatedPassword = '';
      for (let i=0; i < this.length; i++) {
        const index = Math.floor(Math.random() * validChars.length);
        generatedPassword += validChars[index];
      }
      this.password = generatedPassword;
    },
    copyToClipboard: function() {
      let toCopy = document.querySelector('#password');
      toCopy.setAttribute('type', 'text');
      toCopy.select();
      try {
        document.execCommand('copy');
      } catch (err) {
        console.log(err);
      }
    }
  }
}
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.card {
  background-color: #fff;
  width: 700px;
  margin: 20px 20px;
  padding: 20px 20px;
}

.md-icon-button {
  margin: 0px 30px;
  padding: 0px 0px 10px;
}
</style>
