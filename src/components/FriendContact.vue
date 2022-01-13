<template>
  <li>
    <h2>{{ friendName }} {{isFavorite?"(Favorite)":""}}</h2>
    <button @click="toggleDetails">
      {{ detailsAreVisible ? "Hide" : "Show" }} Details
    </button>
    <button @click="checkFavorite">is Favorite</button>
    <ul v-if="detailsAreVisible">
      <li>
        <strong>Phone:</strong>
        {{ phoneNumber }}
      </li>
      <li>
        <strong>Email:</strong>
        {{ emailAddress }}
      </li>
    </ul>
  </li>
</template>

<script>
export default {
  // props: ['friendId', 'friendName',  'phoneNumber', 'emailAddress'],
  props: {
    id:{
      type:String,
      required:true
    },
    friendName: {
      type: String,
      required: true,
    },
    phoneNumber: {
      type: Number,
      required: true,
    },
    emailAddress: {
      type: String,
      required: false,
      default:'god@gmail.com'
    },
    isFavorite:{
      type:Boolean,
      required:true
    }
  },
  data() {
    return {
      detailsAreVisible: false
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },

    checkFavorite()
    {
      this.$emit('emit-binding',this.id);
    }
  },
};
</script>
