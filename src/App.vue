<template>
  <div id="app">
    <TopZone />
    <LendingComponent />
  </div>
</template>


<style>
html, body {
  height: 100%; /* Full height */
  margin: 0;    /* Remove default margins */
  padding: 0;   /* Remove default padding */
}
/* Reset default styling for the #app div */
#app {

  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: column; 

}
</style>


<script>
import { useConnection, useWallet } from "@solana/wallet-adapter-react";
import { WalletMultiButton } from "@solana/wallet-adapter-react-ui";
import { useEffect, useState } from "react";

import SolanaWallets from "solana-wallets-vue";

// You can either import the default styles or create your own.
import "solana-wallets-vue/styles.css";

import { WalletAdapterNetwork } from "@solana/wallet-adapter-base";

import {
  PhantomWalletAdapter,
  SolflareWalletAdapter,
} from "@solana/wallet-adapter-wallets";

const walletOptions = {
  wallets: [
    new PhantomWalletAdapter(),
    new SolflareWalletAdapter({ network: WalletAdapterNetwork.Devnet }),
  ],
  autoConnect: true,
};

import { initWallet } from "solana-wallets-vue";
initWallet(walletOptions);
import LendingComponent from './components/LendingComponent.vue';
import TopZone from './components/TopZone.vue'; // Import TopZone component

export default {
  components: {
    TopZone,
    LendingComponent,
  },
};


</script>
