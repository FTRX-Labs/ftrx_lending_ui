<!-- src/components/TopZone.vue -->
<script setup>
import { WalletMultiButton } from "solana-wallets-vue";
</script>

<template>
  <div class="top-zone">
    <wallet-multi-button></wallet-multi-button>
  </div>
</template>

<script>
export default {
  name: 'TopZone',
};
</script>

<style scoped>
.top-zone {
  width: 100%; /* Full width */
  height: 20vh; /* 10% of the viewport height */

  display: flex; /* Flexbox for centering content */
  flex-direction: row-reverse; 
  margin-bottom: 20px; /* Space below the top zone */
}
</style>
