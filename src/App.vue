<template>
  <div>
    <h1>{{ title }}</h1>
    <p>{{ count }}</p>
    <button @click="count ++">추가</button>

    <HomeComponent/>
    <AppStatus/>
  </div>
</template>

<script>
import HomeComponent from "@/Home";

export default {
  data() {
    return {
      title: "안녕하세요.",
      count: 1
    };
  },
  components: {
    HomeComponent
  }
};
</script>
