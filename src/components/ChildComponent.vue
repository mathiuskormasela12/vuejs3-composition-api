<template>
  <div>
    <p>{{ name }}</p>
    <button @click="show">Click Me</button>
  </div>
</template>

<script>
import { toRefs } from "vue";

export default {
  props: {
    name: {
      type: String,
      default: "-",
    },
  },

  setup(props, context) {
    const show = () => {
      // We're using toRefs because we want to desctructure the props object
      // We can destructue the props when we're using the toRefs only
      const { name } = toRefs(props);
      const { emit, attrs, slots } = context;
      console.log(slots);
      emit("parent-method-desu", attrs.class);
      console.log(name);
    };

    return {
      show,
    };
  },
};
</script>
