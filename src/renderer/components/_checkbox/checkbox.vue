<template>
  <div >
    <label class="container"> Encrypt
    <input type="checkbox" v-model="encrypt">
      <span class="checkmark"></span>
    </label>
  </div>
</template>

<script>
import { mapGetters, mapState } from 'vuex'

export default {
  computed: {
    ...mapGetters([
      'settings'
    ])
  },
  
  data() {
    return {
      encrypt: false
    }
  },
  created() {
    this.encrypt = this.settings.encrypt
  },
  watch: {
    encrypt: function (value) {
      if(value !== this.settings.encrypt) {
        this.$store.commit('setSetting', { key: 'encrypt', value})
      }
    }
  }
}
</script>

<style>
/* Customize the label (the container) */
.container {
  display: block;
  position: relative;
  padding-left: 27px;
  cursor: pointer;
  font-size: 1rem;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

/* Hide the browser's default checkbox */
.container input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
  
}

/* Create a custom checkbox */
.checkmark {
  position: absolute;
  top: 0;
  left: 0;
  height: 18px;
  width: 18px;
  background-color: #eee;
  border:1px solid transparent;
  border-radius:4px;
}

/* On mouse-over, add a grey background color */
.container:hover input ~ .checkmark {
  background-color: rgb(233, 233, 233);
}

/* When the checkbox is checked, add a blue background */
.container input:checked ~ .checkmark {
  background-color: #eee;
}

/* Create the checkmark/indicator (hidden when not checked) */
.checkmark:after {
  content: "";
  position: absolute;
  display: none;
}

/* Show the checkmark when checked */
.container input:checked ~ .checkmark:after {
  display: block;
}

/* Style the checkmark/indicator */
.container .checkmark:after {
  left: 5px;
  top: 2px;
  width: 4px;
  height: 8px;
  border: solid var(--main-color);
  border-width: 0 3px 3px 0;
  -webkit-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  transform: rotate(45deg);
}
</style>
