<template>
  <div class="bg-gray-300" style="font-family: Roboto">
    <div class="w-full h-screen flex items-center justify-center">
      <form
        @submit.prevent="formRegister"
        class="w-full md:w-1/3 bg-white rounded-lg"
      >
        <div class="flex font-bold justify-center mt-6">
          <img
            class="h-20 w-20"
            src="https://raw.githubusercontent.com/sefyudem/Responsive-Login-Form/master/img/avatar.svg"
          />
        </div>
        <h2 class="text-3xl text-center text-gray-700 mb-4">Register Form</h2>
        <div class="px-12 pb-10">
          <div class="w-full mb-2">
            <div class="flex items-center">
              <i
                class="ml-3 fill-current text-gray-400 text-xs z-10 fa fa-user"
              ></i>
              <input
                v-model="email"
                type="email"
                placeholder="input your email here.."
                class="
                  -mx-6
                  px-8
                  w-full
                  border
                  rounded
                  px-3
                  py-2
                  text-gray-700
                  focus:outline-none
                "
              />
            </div>
          </div>
          <div class="w-full mb-2">
            <div class="flex items-center">
              <i
                class="ml-3 fill-current text-gray-400 text-xs z-10 fa fa-lock"
              ></i>
              <input
                v-model="password"
                type="password"
                placeholder="input your password here.."
                class="
                  -mx-6
                  px-8
                  w-full
                  border
                  rounded
                  px-3
                  py-2
                  text-gray-700
                  focus:outline-none
                "
              />
            </div>
          </div>
          <button
            type="submit"
            class="
              w-full
              py-2
              rounded-full
              bg-green-600
              text-gray-100
              focus:outline-none
            "
          >
            Register
          </button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "Register",
  data() {
    return {
      email: "",
      password: "",
    };
  },
  computed: {
    flagRegister() {
      return this.$store.state.flagRegister;
    },
  },

  methods: {
    async formRegister() {
      await this.$store.dispatch("register", {
        email: this.email,
        password: this.password,
      });
      if (this.flagRegister) {
        this.$router.push({ name: "Login" });
      }
    },
    loginPage() {
      this.$router.push({ name: "Login" });
    },
  },
};
</script>

<style>
</style>