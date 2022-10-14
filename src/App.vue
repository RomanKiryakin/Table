<template>
<ticketCard></ticketCard>
</template>
<script>

import ticketCard from "@/components/ticketCard";


export default {
  components: { ticketCard },
  el: '#app',
  data() {
    return {
      mess: "hello",
    }
  },
}


</script>




<style lang="scss">

</style>
