<template>
  <b-container>
    <section class="contact">
      <h2 class="section_title">Contact me</h2>
      <b-form
        @submit="handleFormSubmit"
        class="gform"
        action="https://script.google.com/macros/s/AKfycbyn46ncUzOIkgxU5YYbSU8PCZh9v4klQklzcX9Q/exec"
        method="post"
      >
        <b-form-group id="nameInput" label="Your Name:" label-for="name">
          <b-form-input
            id="name"
            v-model="name"
            name="name"
            required
            placeholder="Enter name"
          ></b-form-input>
        </b-form-group>

        <b-form-group
          id="mailInput"
          label="Email Address:"
          label-for="mail"
          description="I'll never share your email with anyone else."
        >
          <b-form-input
            id="mail"
            v-model="mail"
            name="email"
            type="email"
            required
            placeholder="Enter email"
          ></b-form-input>
        </b-form-group>
        <b-form-group
          id="messageInput"
          label="Your Message:"
          label-for="textarea"
        >
          <b-form-textarea
            id="textarea"
            v-model="message"
            name="message"
            required
            placeholder="Enter something..."
            rows="3"
            max-rows="6"
          ></b-form-textarea>
        </b-form-group>
        <b-button :disabled="formSended" class="submitBtn" type="submit"
          >Submit</b-button
        >
      </b-form>
      <div class="thankyou_message" style="display:none;">
        <h2>
          <em>Thanks</em> for contacting us! We will get back to you soon!
        </h2>
      </div>
    </section>
  </b-container>
</template>

<script>
export default {
  data() {
    return {
      message: '',
      name: '',
      mail: '',
      formSended: false,
    };
  },

  methods: {
    // get all data in form and return object
    getFormData(form) {
      const elements = form.elements;
      let honeypot;

      const fields = Object.keys(elements)
        .filter(function(k) {
          if (elements[k].name === 'honeypot') {
            honeypot = elements[k].value;
            return false;
          }
          return true;
        })
        .map(function(k) {
          if (elements[k].name !== undefined) {
            return elements[k].name;
            // special case for Edge's html collection
          } else if (elements[k].length > 0) {
            return elements[k].item(0).name;
          }
        })
        .filter(function(item, pos, self) {
          return self.indexOf(item) === pos && item;
        });

      const formData = {};
      fields.forEach(function(name) {
        const element = elements[name];

        // singular form elements just have one value
        formData[name] = element.value;

        // when our element has multiple items, get their values
        if (element.length) {
          const data = [];
          for (let i = 0; i < element.length; i++) {
            const item = element.item(i);
            if (item.checked || item.selected) {
              data.push(item.value);
            }
          }
          formData[name] = data.join(', ');
        }
      });

      // add form-specific values into the data
      formData.formDataNameOrder = JSON.stringify(fields);
      formData.formGoogleSheetName = form.dataset.sheet || 'responses'; // default sheet name
      formData.formGoogleSendEmail = form.dataset.email || ''; // no email by default

      return { data: formData, honeypot: honeypot };
    },
    handleFormSubmit(event) {
      // handles form submit without any jquery
      event.preventDefault(); // we are submitting via xhr below
      const form = event.target;
      const formData = this.getFormData(form);
      const data = formData.data;

      // If a honeypot field is filled, assume it was done so by a spam bot.
      if (formData.honeypot) {
        return false;
      }

      const url = form.action;
      const xhr = new XMLHttpRequest();
      xhr.open('POST', url);
      // xhr.withCredentials = true;
      xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');
      xhr.onreadystatechange = function() {
        if (xhr.readyState === 4 && xhr.status === 200) {
          form.reset();
          this.formSended = true;
        }
      };
      // url encode form data for sending as post data
      const encoded = Object.keys(data)
        .map(function(k) {
          return encodeURIComponent(k) + '=' + encodeURIComponent(data[k]);
        })
        .join('&');
      xhr.send(encoded);
    },
  },
};
</script>

<style lang="scss" scoped>
.section_title {
  color: $clr-accent;
}

.submitBtn {
  background-color: $clr-accent;
  border: none;
  transition: all 0.25s ease-in-out;

  &:hover {
    background-color: $clr-accent2;
  }
  &.disabled:hover {
    background-color: #6c757d;
  }
}
</style>
