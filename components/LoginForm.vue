<template>
  <form >
    <v-text-field v-model="name" :error-messages="nameErrors" :counter="10" label="Name"
      required @input="$v.name.$touch()" @blur="$v.name.$touch()" >
    </v-text-field>
    <v-text-field v-model="password" :error-messages="passwordErrors" :append-icon="show ? 'visibility' : 'visibility_off'"
      :type="show ? 'text' : 'password'" label="Password" required :counter="10" @click:append="show = !show" >
    </v-text-field>
    <v-btn class="mr-4" @click="submit" nuxt >submit</v-btn>
    <v-btn @click="clear">clear</v-btn>
  </form>
</template>

<script>
  import { validationMixin } from 'vuelidate'
  import { required, maxLength } from 'vuelidate/lib/validators'
  const Cookie = process.client ? require('js-cookie') : undefined

  export default {
    mixins: [validationMixin],

    validations: {
      name: { required, maxLength: maxLength(10) },
      password: { required, maxLength: maxLength(10) }
    },

    data: () => ({
      name: '',
      password: '',
      rules: {
        required: value => !!value || 'Required.',
        min: v => v.length >= 8 || 'Min 8 characters'
      },
      show: false
    }),

    computed: {
      nameErrors () {
        const errors = []
        if (!this.$v.name.$dirty) return errors
        !this.$v.name.maxLength && errors.push('Name must be at most 10 characters long')
        !this.$v.name.required && errors.push('Name is required.')
        return errors
      },
      passwordErrors () {
        const errors = []
        if (!this.$v.password.$dirty) return errors
        !this.$v.password.maxLength && errors.push('Name must be at most 10 characters long')
        !this.$v.password.required && errors.push('Password is required')
        return errors
      },
    },

    methods: {
      submit () {
        console.log('submit')
        this.$v.$touch()
        if (!this.$v.$invalid) {
          if(this.name == 'Admin' && this.password == 'Password'){
            const auth = {
              accessToken: 'someStringGotFromApiServiceWithAjax'
            }
            Cookie.set('auth', auth)
            this.$store.commit('setAuth', auth)
          }
          this.$router.push('/person/HelloWorld')
        }
      },
      clear () {
        this.$v.$reset()
        this.name = ''
        this.email = ''
        this.select = null
        this.checkbox = false
      },
      logout () {
        Cookie.remove('auth')
        this.$store.commit('setAuth', null)
      }
    }
  }
</script>