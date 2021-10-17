<template>
  <li>{{ title }}</li>
</template>

<script>
export default {
  name: "ProductListEntry",
  props: {
    title: {
      type: String,
    },
  },
};
</script>
