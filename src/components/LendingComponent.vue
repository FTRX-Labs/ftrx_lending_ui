<script setup>


</script>

<template>
  <div class="main-container">

    <div class="second-container">
      <div class="lending-container">
        <h2>FTRX Lending</h2>

        <!-- SOL Borrow/Redeem Section -->
        <div class="lending-section">
          <h3>SOL</h3>

          <div class="action-group">
            <input type="number" placeholder="Amount to borrow/redeem" v-model="solAmount" />
            <button class="borrow-button" @click="borrow('SOL')">Borrow</button>
            <button class="redeem-button" @click="redeem('SOL')">Redeem</button>
            <button class="deposit-button" @click="deposit('SOL')">Deposit</button>
            <button class="withdraw-button" @click="withdraw('SOL')">Withdraw</button>
            <!-- SOL Tooltip Trigger -->
            <button class="info-button" @mouseenter="showGlobalInfo('SOL')" @mouseleave="hideGlobalInfo()">?</button>
          </div>

          <!-- SOL Tooltip -->
          <div v-if="showInfo === 'SOL'" class="tooltip">
            <p><strong>Total Deposited (Global):</strong> {{ solGlobalDeposits }} SOL</p>
            <p><strong>Total Borrowed (Global):</strong> {{ solGlobalBorrowed }} SOL</p>
          </div>
        </div>

        <!-- USDC Borrow/Redeem Section -->
        <div class="lending-section">
          <h3>USDC</h3>
          <div class="action-group">
            <input type="number" placeholder="Amount to borrow/redeem" v-model="usdcAmount" />
            <button class="borrow-button" @click="borrow('USDC')">Borrow</button>
            <button class="redeem-button" @click="redeem('USDC')">Redeem</button>
            <button class="deposit-button" @click="deposit('USDC')">Deposit</button>
            <button class="withdraw-button" @click="withdraw('USDC')">Withdraw</button>
            <!-- USDC Tooltip Trigger -->
            <button class="info-button" @mouseenter="showGlobalInfo('USDC')" @mouseleave="hideGlobalInfo()">?</button>
          </div>

          <!-- USDC Tooltip -->
          <div v-if="showInfo === 'USDC'" class="tooltip">
            <p><strong>Total Deposited (Global):</strong> {{ usdcGlobalDeposits }} USDC</p>
            <p><strong>Total Borrowed (Global):</strong> {{ usdcGlobalBorrowed }} USDC</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      solAmount: '', // Amount for SOL
      usdcAmount: '', // Amount for USDC

      // Global Stats for SOL and USDC
      solGlobalDeposits: 1000,  // Example global deposit value for SOL
      solGlobalBorrowed: 500,   // Example global borrowed value for SOL
      usdcGlobalDeposits: 5000, // Example global deposit value for USDC
      usdcGlobalBorrowed: 2500, // Example global borrowed value for USDC

      showInfo: null, // To track which token's tooltip is visible
    };
  },
  methods: {
    borrow(token) {
      let amount = token === 'SOL' ? this.solAmount : this.usdcAmount;
      if (!amount || amount <= 0) {
        alert(`Please enter a valid amount to borrow for ${token}`);
        return;
      }
      alert(`Borrowing ${amount} of ${token}`);
    },
    redeem(token) {
      let amount = token === 'SOL' ? this.solAmount : this.usdcAmount;
      if (!amount || amount <= 0) {
        alert(`Please enter a valid amount to redeem for ${token}`);
        return;
      }
      alert(`Redeeming ${amount} of ${token}`);
    },
    showGlobalInfo(asset) {
      this.showInfo = asset;
    },
    hideGlobalInfo() {
      this.showInfo = null;
    }
  }
};
</script>

<style scoped>


.main-container {
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: column; /* Stacks elements vertically */
  justify-content: flex-start; /* Aligns items at the top */
  align-items: center; /* Centers items horizontally */

}
.second-container {

  width: 100%;
  height: 100%;
  display: flex;

  justify-content: center;
  align-items: center;

}

.top_zone {

  width: 100%;
  height: 10vh; /* 10% of the viewport height */
  background-color: #007bff; /* You can adjust this to any color */
  margin-top: 20px; /* Space between the top zone and the content */
}

.lending-container {
  background-color: white;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  width: 600px;
  text-align: center;
  justify-content: center;
  align-items: center;
  margin-top: 10%;
}


.lending-section {
  margin-bottom: 30px;
}

h3 {
  margin-bottom: 10px;
  color: #333;
}

h2 {
  margin-bottom: 10px;
  color: #333;
}

.action-group {
  display: flex;
  justify-content: center;
  align-items: center;
}

input {
  width: 100px;
  padding: 8px;
  margin-right: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  -moz-appearance: textfield;
}

button {
  padding: 8px 16px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.borrow-button {
  background-color: #007bff;
  color: white;
}

.borrow-button:hover {
  background-color: #0056b3;
}

.redeem-button {
  background-color: #28a745;
  color: white;
  margin-left: 10px;
}

.deposit-button {
  background-color: #28a745;
  color: white;
  margin-left: 10px;
}

.deposit-button:hover {
  background-color: #218838;
}

.withdraw-button {
  background-color: #28a745;
  color: white;
  margin-left: 10px;
}

.withdraw-button:hover {
  background-color: #218838;
}

.redeem-button:hover {
  background-color: #218838;
}

/* Tooltip styling */
.tooltip {
  background-color: rgba(0, 0, 0, 0.75);
  color: #fff;
  padding: 10px;
  border-radius: 5px;
  font-size: 0.85rem;
  position: absolute;
  margin-top: 10px;
  z-index: 10;
  text-align: left;
}

.info-button {
  background-color: transparent;
  border: none;
  font-size: 1.5rem;
  cursor: pointer;
  color: #007bff;
  outline: none;
}

.info-button:hover {
  color: #0056b3;
}
</style>
