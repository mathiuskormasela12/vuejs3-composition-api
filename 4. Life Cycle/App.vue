<template>
  <h1>Life Cycle</h1>
</template>

<script>
import {
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onBeforeUnmount,
  onUnmounted,
  onActivated,
  onDeactivated,
  onErrorCaptured,
} from "vue";

export default {
  name: "App",

  setup() {
    onBeforeMount(() => {
      console.log(
        "This one will be executed when the component has not been installed yet (Will be run before onMounted is executed)"
      );
    });

    onMounted(() => {
      console.log(
        "This one will be executed when the component has been installed (after onBeforeMountd is executed, this one will be executed)"
      );
    });

    onBeforeUpdate(() => {
      console.log("This one will be executed when a data has not been updated");
    });

    onUpdated(() => {
      console.log(
        "This one will be executed when a data has been updated (will executed after onBeforeUpdate is executed)"
      );
    });

    onBeforeUnmount(() => {
      console.log(
        "This one will be executed when a component has not been deleted yet"
      );
    });

    onUnmounted(() => {
      console.log(
        "This one will be executed when a component has been deleted (will be executed after onBeforeMOunted is executed)"
      );
    });

    onActivated(() => {
      console.log("This one will be executed when the keep-alive is enabled");
    });

    onDeactivated(() => {
      console.log("This one will be executed when the keep-alive is disabled");
    });

    onErrorCaptured(() => {
      console.log(
        "This one will be executed when there is an error in Child Component"
      );
    });
  },
};
</script>
