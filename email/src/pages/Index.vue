<template>
   <q-img :src='background_img' :ratio="18/9" >
  <q-page class="flex flex-center">
    <q-card bordered>
    <img
      alt="LoopClub"
      :src="img_url"
    >
    <div class="text-center text-black-8" style="font-size:25px; font-family: 'Arial';">
    <q-label>
      Subscribe To Our Newsletter
    </q-label>
    </div>
    <div class="text-grey-8 text-center text-caption q-pb-md q-pt-sm">
    <q-label>
      Join our subscribers list to get the latest news, updates and special offers delivered directly
    </q-label>
    </div>
     <q-input class="q-mx-xl q-mb-xl" @keyup.enter="saveEmail()" outlined label="Enter your email" v-model="email" type="email">
        <template v-slot:prepend>
          <q-icon name="mail"/>
        </template>
        <template v-slot:append>
          <q-btn icon="send" @click="saveEmail()" color="accent" size="md"/>
        </template>
      </q-input>
      <q-btn ripple label="SUBSCRIBE" color="accent" @click="saveEmail()" style="margin-left:40%; margin-top:-10%"/>
    </q-card>
    <!-- success dialog -->
    <q-dialog v-model="success_dialog">
      <q-card>
        <q-card-section class="row items-center">
          <q-img :src="success_img" />
          <span class="q-ml-sm text-grey-8" style="font-size:20px">Successfully subscribed</span>
        </q-card-section>

        <q-card-actions align="right">
          <q-btn flat label="Ok" color="primary" v-close-popup />
        </q-card-actions>
      </q-card>
    </q-dialog>
    <!-- fail dialog -->
    <q-dialog v-model="fail_dialog">
      <q-card>
        <q-card-section class="row items-center">
           <q-img :src="fail_img" />
          <span class="q-ml-sm text-grey-8" style="font-size:20px">Subscription failed, please try again</span>
        </q-card-section>

        <q-card-actions align="right">
          <q-btn flat label="Ok" color="primary" v-close-popup />
        </q-card-actions>
      </q-card>
    </q-dialog>
  </q-page>
  </q-img>

</template>

<script>
export default {
  name: 'PageIndex',
  data () {
    return {
      background_img: 'https://cdn.nohat.cc/image_by_url.php?url=https://image.freepik.com/free-vector/abstract-waves-colorful-vector-background_23-2147640767.jpg',
      email: '',
      img_url: 'https://image.freepik.com/free-vector/woman-receiving-mail-reading-letter_74855-5964.jpg',
      success_dialog: false,
      fail_dialog: false,
      success_img: 'https://www.med-bay.com/images/2019/check.gif',
      fail_img: 'https://lh3.googleusercontent.com/proxy/5mHNkCXrKYgBh3j3Cs0p24mb3bPqV-XAFKyq5TmsjdmV2UJ4527pPo-nMoLQ5yw8HOKbGeAGsn0DC7Qh2InLBEOPkrvzqSc'
    }
  },
  methods: {
    saveEmail () {
      var params = new URLSearchParams()
      params.append('email', this.email)
      this.$axios.post('http://127.0.0.1:8000/', params)
        .then(response => {
          console.log('Email saved')
          this.email = ''
          this.success_dialog = true
        })
        .catch(error => {
          console.log(error + ' Email not saved')
          this.fail_dialog = true
        })
    }
  }
}
</script>
