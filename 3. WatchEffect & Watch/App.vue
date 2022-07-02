<template>
  <h1>WatchEffect & Watch</h1>
  <button type="button" @click="count++">Click {{ count }}</button>
</template>

<script>
import { watchEffect, ref, watch, reactive } from "vue";

export default {
  name: "App",

  setup() {
    const count = ref(0);
    const mhs = reactive({
      nama: "Mathius",
    });

    // This one will be executed if there is value changing in count
    watchEffect(
      () => {
        alert(count.value);
      },
      {
        // These all for debugging (if we have created the producation build, these all can't be executed)
        // Untuk tracking
        onTrack() {},
        // ketika di triggre
        onTrigger() {},
        // The watchEffect will be executed before the component is installed (default)
        // flush: "pre",
        // The watchEffect will be executed after the component is installed
        flush: "post",
      }
    );

    // this one will be extecuted if there is value changing in count (data ref only)
    watch(count, (current, previous) => {
      window.alert(current);
      window.alert(previous);
    });

    // this one will be extecuted if there is value changing in count (data reactive only only)
    watch(
      () => mhs.nama,
      (current, previous) => {
        window.alert(current);
        window.alert(previous);
      }
    );

    return {
      count,
      mhs,
    };
  },
};
</script>
