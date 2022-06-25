<template>
  <div class="w-[400px] mx-auto">
    <form @submit="submit">
      <FormInput
        v-for="input in form"
        :key="input.name"
        v-model="input.value"
        :name="input.name"
        :visible="input.visible"
        @input="changed"
      />
    </form>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',

  data() {
    return {
      form: [
        {
          name: 'firstname',
          value: '',
          visible: true,
          shouldBeVisible: (input) => {
            console.log('Calling on', input.name)
            return true
          },
        },
        {
          name: 'lastname',
          value: '',
          visible: true,
          shouldBeVisible: (input) => {
            console.log('Calling on', input.name)
            return true
          },
        },
        {
          name: 'email',
          value: '',
          visible: true,
          shouldBeVisible: (input) => {
            const firstname = this.form.find(
              (input) => input.name === 'firstname'
            )
            return firstname.value !== 'Luis'
          },
        },
      ],
    }
  },

  // watch: {
  //   form: {
  //     deep: true,
  //     handler(newValue, oldValue) {
  // this.form.forEach((input) => {
  //   const email = this.form.find((input) => input.name === 'email')
  //   email.visible = input.name === 'firstname' && input.value === 'Luis'
  // })
  //       console.log(this.form)
  //     },
  //   },
  // },

  methods: {
    submit() {
      console.log(this.form)
    },

    changed() {
      console.log('Changing')
      this.form.forEach((input) => {
        input.visible = input.shouldBeVisible(input)
      })
    },
  },
}
</script>
