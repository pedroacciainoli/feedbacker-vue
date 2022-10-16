<template>
  <custom-header @create-account="handleAccountCreate" @login="handleLogin" />
  <contact />
  <div class="flex justify-center py-10 bg-brand-gray">
    <p class="font-medium text-center text-gray-800">
      feedbacker &copy; {{ year }}
    </p>
  </div>
</template>

<script>
import { onMounted } from "vue";
import { useRouter } from "vue-router";
import CustomHeader from "./CustomHeader.vue";
import Contact from "./Contact.vue";

export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Home",
  components: {
    CustomHeader,
    Contact,
  },
  data (){
    return{
       year : new Date().getFullYear();
    }
  },
  setup() {
    const router = useRouter();
    onMounted(() => {
      const token = window.localStorage.getItem("token");
      if (token) {
        router.push({ name: "Feedbacks" });
      }
    });

    function handleLogin() {}

    function handleAccountCreate() {}

    return handleLogin, handleAccountCreate;
  },
};
</script>
<style></style>
