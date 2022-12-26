
<template>
</template>
   
  <script>
  import { defineComponent, ref } from "vue";
  import { useMessage } from "naive-ui";
   
  export default defineComponent({
    setup() {
      window.$message = useMessage(); 
    },
  });
  </script>