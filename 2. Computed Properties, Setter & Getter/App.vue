<template>
  <h1>Computed Properties, Setter, Getter</h1>
  <p>Halo nama saya {{ name }}</p>
  <p>Uisa saya {{ usia }} tahun</p>
</template>

<script>
import { computed, ref, onMounted } from "vue";

export default {
  name: "App",

  setup() {
    const age = ref(20);

    // Computed Properties
    const name = computed(() => "Mathius");

    // Setter & Getter
    const usia = computed({
      get() {
        return age;
      },
      set(val) {
        age.value = val;
      },
    });

    onMounted(() => {
      setTimeout(() => {
        usia.value = 21;
      }, 2000);
    });

    return {
      name,
      usia,
    };
  },
};
</script>
