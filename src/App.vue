<template>
  <div>
    <h1>Props, Emit, Attributes, Slot</h1>
    <ChildComponent
      name="This is the child component"
      @parent-method-desu="parentMethod"
      class="wwkw"
    >
      <p>Ini Bre</p>
    </ChildComponent>
  </div>
</template>

<script>
import ChildComponent from "./components/ChildComponent.vue";

export default {
  name: "App",
  components: {
    ChildComponent,
  },

  setup() {
    const parentMethod = (val) => {
      console.log("Parent Component Method class nya =>" + val);
    };

    return {
      parentMethod,
    };
  },
};
</script>
