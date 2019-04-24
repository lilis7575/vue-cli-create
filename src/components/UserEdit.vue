<template>
  <div class="yellow lighten-3 pa-3">
    <h3>회원 정보를 수정할 수 있습니다.</h3>
    <p>수정사항</p>
    <v-text-field label="Name" v-model="user.name"></v-text-field>
    <v-text-field label="Address" v-model="user.address"></v-text-field>
    <v-text-field label="Phone" v-model="user.phone"></v-text-field>
    <v-switch v-model="user.hasDog" :label="`Has Dogs`"></v-switch>
    <v-btn @click="save">저장</v-btn>
  </div>
</template>

<script>
export default {
  props: ["name", "address", "phone", "hasDog"],
  data() {
    return {
      user: {}
    };
  },
  methods: {
    save() {
      console.log(this.user);
      this.$emit("child", this.user, 1, 2, 3, 4);
    }
  },
  created() {
    this.user.name = this.name;
    this.user.address = this.address;
    this.user.phone = this.phone;
    this.user.hasDog = this.hasDog;
  }
};
</script>