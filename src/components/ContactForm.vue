<template>
  <form @submit.prevent="addProfile" ref="formSet">
    <div>
      <label>Name:</label>
      <input type="text" placeholder="Enter Your Name" v-model="FriendName" />
    </div>

    <div>
      <label>Phone:</label>
      <input type="tel" placeholder="Enter Your phone" v-model="FriendPhone" />
    </div>

    <div>
      <label>Email:</label>
      <input
        type="email"
        placeholder="Enter Your Email"
        v-model="FriendEmail"
      />
    </div>

    <div>
      <button type="submit">Add Friends</button>
    </div>
  </form>
</template>

<script>
export default {
  emits: ["add-contact"],
  data() {
    return {
      FriendName: "",
      FriendEmail: "",
      FriendPhone: "",
    };
  },
  methods: {
    addProfile() {
      const data = {
        id:new Date().getTime(),
        name: this.FriendName,
        email: this.FriendEmail,
        phone: Number(this.FriendPhone),
        isFavorite: false,
      };
      const s = this.$refs.formSet;
      this.$emit("add-profile",data,s);
      
    },
  },
};
</script>
