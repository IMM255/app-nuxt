<template>
  <div class="container">
    <section class="form">
        <div class="field">
          <label class="label">Name :</label>
          <div class="control">
            <input
            v-model="form.name"
            class="input"
            type="text"
            placeholder="Isi Lengkap beserta  gelar"
            >
          </div>
          <label class="label">Message</label>
          <div class="control">
            <textarea
            v-model="form.message"
            class="textarea"
            >
            </textarea>
          </div>
          <label class="label">
            Select Inquiry
          </label>
          <div class="control">
            <select v-model="form.inquiry_type" >
              <option disabled value="">Nothing selected</option>
              <option v-for="option in options.inquiry" :key="option" >{{option.text}}</option>
            </select>
          </div>
          <label class="label">Select Multiple</label>
          <div class="control">
            <select multiple v-model="form.usecases">
              <option>Debugging Code</option>
              <option>Fixing Error</option>
              <option>User Support</option>
            </select>
          </div>
          <label class="checkbox">
            <input type="checkbox" v-model="form.terms">
            I agree to the <a href="#">terms and condition</a>
          </label>
        </div>
    </section>
    <section class="content">
      <br>
      <ul>
        <li v-for="(item, k) in form" :key="k">
          <strong>{{ k }}:</strong> {{ item }}
        </li>
      </ul>
    </section>
  </div>
</template>

<script>
export default {
    layout (context){
      return 'Custom'
    },
        data() {
          return{
            form: {
                name:'',
                message:'',
                inquiry_type: '',
                usecase: [],
                terms: false,

            },
            options: {
            inquiry: [
              {value: 'feature', text: "feature Request"},
              {value: 'bug', text: "Bug report"},
              {value: 'support', text: " "},
            ]
          }
        }
      },
      methods: {
        handleSubmit(){
          console.log(this.form)
        }
      }
    }
</script>

