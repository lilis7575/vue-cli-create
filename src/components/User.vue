<template>
  <div class="blue lighten-3 pa-3">
    <h1>User 컴포넌트</h1>
    <p>이름: {{ name }}</p>
    <p>{{ getDateAndTime(createAt) }}</p>
    <p>{{ helloToMixin }}</p>
    <v-btn @click="changeName()">이름변경</v-btn>
    <hr>
    <v-layout row wrap>
      <v-flex xs12 sm6>
        <UserDetail :name="name" :address="address" :phone="phone" :hasDog="hasDog"></UserDetail>
      </v-flex>
      <v-flex xs12 sm6>
        <UserEdit :name="name" :address="address" :phone="phone" :hasDog="hasDog" @child="parents"></UserEdit>
      </v-flex>
    </v-layout>
  </div>
</template>

<script>
import UserDetail from "./UserDetail.vue";
import UserEdit from "./UserEdit.vue";
import { dateFormat } from "../mixins/dateFormat";

export default {
  data() {
    return {
      name: "Vue JS",
      address: "korea",
      phone: "010-1111-2222",
      hasDog: true,
      createAt: null
    };
  },
  components: {
    UserDetail,
    UserEdit
  },
  created() {
    console.log("user.vue");
    this.createAt = new Date();
  },
  computed: {
    helloToMixin() {
      return this.mixinData + " => 안녕하세요~~";
    }
  },
  methods: {
    changeName() {
      this.name = "뷰 제이에스~";
    },
    parents(obj, p1, p2, p3, p4) {
      this.name = obj.name;
      this.address = obj.address;
      this.phone = obj.phone;
      this.hasDog = obj.hasDog;
    },
    getDateAndTime(date) {
      // mixin 에 있는 함수보다 로컬 함수가 우선 수행된다.
      if (date != null) {
        let hour = date.getHours();
        let minutes = date.getMinutes();
        let fullDate = `${date.getFullYear()}/${date.getMonth() +
          1}/${date.getDate()}`;

        return `${hour}:${minutes} ${fullDate} `;
      } else {
        return null;
      }
    }
  },
  mixins: [dateFormat]
};
</script>