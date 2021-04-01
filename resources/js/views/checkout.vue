<template>
  <div class="home text-center py-5 mt-5">
    <checkout></checkout>
  </div>
</template>

<script>
import CheckoutComponent from '../components/checkout';
export default {
   components:{
     'checkout':CheckoutComponent,
   }
};
</script>
