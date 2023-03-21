<template>
  <div class="container d-flex">
      <br />
      <div v-if="contact" class="page">
          <h4>Thêm liên hệ</h4>
          <ContactForm :contact="contact"
           @submit:contact="createContact" />
          <p>{{ message }}</p>
      </div>
  </div>
</template>

<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/services/contact.service";
export default {
  components: {
      ContactForm,
  },
  props: {
      // id: { type: String, required: true },
  },
  data() {
      return {
          contact: {},
          message: "",
      };
  },
  methods: {
      async createContact(data) {
          try {
              await ContactService.create(data);
              // alert("Liên hệ đã được thêm thành công.");
              this.message = "Liên hệ được thêm thành công.";
              
          } catch (error) {
              console.log(error);
          }
      },
  },
};
</script>

<style>
  h4 {
    font-weight:700 ;
    text-align: center;
  }
</style>