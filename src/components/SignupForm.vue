<template>
    <form @submit.prevent="handleSubmit">
        <label>Email:</label>
        <input type="email" required v-model="email">

        <label>Password:</label>
        <input type="password" required v-model="password">
        <div v-if="passwordError" class="error">{{ passwordError }}</div>

        <label>Name:</label>
        <input type="names" required v-model="names">

        <label>Age：</label>
        <select v-model="age">
            <option value="under20">under 20</option>
            <option value="20to29">20 to 29</option>
            <option value="31to39">31 to 39</option>
            <option value="over40">above 40</option>
        </select>

        <div class="terms">
            <input type = "checkbox" v-model="terms" required>
            <label>Accept terms and conditions</label>
        </div>
        <div v-if="termsError" class="error">{{ termsError }}</div>

        <div class="submit">
            <button>Create an Account</button>
        </div>

    </form>
</template>

<script>
export default {
  data () {
    return {
      email: '',
      password: '',
      names: '',
      age: '',
      terms: false,
      passwordError: '',
      termsError: ''
    }
  },
  methods: {
    handleSubmit () {
      // validate password
      this.passwordError = this.password.length > 7 ? '' : 'Password must be at least 8 chars long'
      // validate terms
      this.termsError = (this.terms === true) ? '' : 'Must accepted terms to create an account'

      if (!this.termsError && !this.passwordError) {
        console.log('submit succeed!')
      }
    }
  }
}
</script>
<style>
    form {
        max-width: 420px;
        margin: 30px auto;
        background: white;
        text-align: left;
        padding: 40px;
        border-radius: 10px;
    }
    label {
        color: #aaa;
        display: inline-block;
        margin: 25px 0 15px;
        font-size: 0.6em;
        text-transform: uppercase;
        letter-spacing: 1px;
        font-weight: bold;
    }
    input, select {
        display: block;
        padding: 10px 6px;
        width: 100%;
        box-sizing: border-box;
        border: none;
        border-bottom: 1px solid #ddd;
        color: #555;
    }
    input[type="checkbox"] {
        display: inline-block;
        width: 16px;
        margin: 0 10px 0 0;
        position: relative;
        top: 2px;
    }
    button {
        background: #0b6dff;
        border: 0;
        padding: 10px 20px;
        margin-top: 20px;
        color: white;
        border-radius: 20px;
    }
    .submit {
        text-align: center;
    }
    .error {
        color: #ff0062;
        margin-top: 10px;
        font-size: 0.8em;
        font-weight: bold;
    }
</style>
