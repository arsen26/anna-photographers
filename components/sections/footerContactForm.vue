<template>
  <v-form ref="form">
    <v-text-field v-model="name" label="Name" dense outlined></v-text-field>
    <v-text-field v-model="email" label="Email" dense outlined></v-text-field>
    <v-text-field v-model="tel" label="Nr Tel" dense outlined></v-text-field>
    <v-text-field
      v-model="subject"
      label="Subject"
      dense
      outlined
    ></v-text-field>
    <v-textarea
      v-model="message"
      dense
      label="Your Message"
      auto-grow
      outlined
      rows="8"
      row-height="20"
    ></v-textarea>
    <v-btn outlined block color="primary" @click="sendEmail"
      >SEND MESSAGE</v-btn
    >
  </v-form>
</template>

<script>
import emailjs from 'emailjs-com'
export default {
  data() {
    return {
      name: '',
      tel: '',
      email: '',
      subject: '',
      message: '', // për modelin e mesazhit
    }
  },
  methods: {
    async sendEmail() {
      try {
        await emailjs.send(
          'service_u1ay0hb', // ID e shërbimit
          'template_09pnylp', // ID e templates
          {
            name: this.name,
            email: this.email,
            subject: this.subject,
            telephone: this.tel,
            message: this.message,
          },
          '2ydcucD9DD2LytKdw' // Çelësi publik
        )

        alert('EMAIL SENT SUCCESSFULLY') // Njofto përdoruesin për dërgimin e emailit
      } catch (err) {
        console.error('Error sending email:', err) // Printo gabimin në konsolë
        alert('Error sending email: ' + err.message) // Trego një mesazh gabimi përdoruesit
      }

      // Pastro fushat pas dërgimit
      this.name = ''
      this.email = ''
      this.tel = ''
      this.message = ''
      this.subject = ''
    },
  },
}
</script>

<style scoped></style>
