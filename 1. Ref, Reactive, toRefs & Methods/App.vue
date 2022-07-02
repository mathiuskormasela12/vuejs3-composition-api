<template>
  <h1>Ref, Reactive, toRefs & Methods</h1>
  <!-- <p>Nama saya {{ biodata.name }}</p> -->
  <!-- We can access name directly because we have used the toRefs -->
  <p>Nama saya {{ name }}</p>
  <button type="button" @click="handleIncrement">
    Increment {{ counter }}
  </button>
  <br />
  <br />
  <input placeholder="Type Gfriend Member" v-model="value" />
  <button type="button" @click="handleAddMember">Add</button>
  <p>Gfriend Member</p>
  <ul v-if="members.length > 0">
    <li v-for="(member, index) in members" :key="index">{{ member }}</li>
  </ul>
  <p v-else>There are not members yet</p>
</template>

<script>
import { ref, reactive, toRefs } from "vue";

export default {
  name: "App",

  setup() {
    // Data/State in Composition Api (We can be able to use the ref, if we only use primitive data type)
    const counter = ref(0);
    const value = ref("");

    // Data/State in Composition Api (We can use this one if we're using non-primitive data type)
    const members = reactive([]);
    const biodata = reactive({
      name: "-",
    });

    // Methods
    const handleIncrement = () => {
      counter.value++;
    };

    const handleAddMember = () => {
      members.push(value.value);
      value.value = "";
    };

    setTimeout(() => {
      biodata.name = "Mathius";
    }, 2000);

    return {
      counter,
      handleIncrement,
      members,
      value,
      handleAddMember,
      // biodata,
      // we will used toRefs so that we can destructure the object
      ...toRefs(biodata),
    };
  },
};
</script>
