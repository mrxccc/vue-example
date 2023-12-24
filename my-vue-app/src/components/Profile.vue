<script setup lang="ts">
import { useWallet, useBalance } from "@connect2ic/vue"

const [wallet] = useWallet()
const [assets] = useBalance()
console.log("walletaaaaaaaaaa")
console.log(wallet.value)
console.log("walletbbbbbbb")

async function sayHi() {
  console.log(wallet.value)
  console.log(wallet.value.ic)
  let ledger = await wallet.value.ic("ss2fx-dyaaa-aaaar-qacoq-cai");
}
</script>
<template>
  <div class="example">
    <button @click="sayHi">点击这里sayHi aaa</button>
    <template v-if="wallet">
      <p>Wallet address: <span style="font-size: 0.7em">{{ wallet.principal }}</span></p>
      <table>
        <tbody>
          <template v-if="assets">
            <tr v-for="asset in assets">
              <td>
                {{ asset.name }}
              </td>
              <td>
                {{ asset.amount }}
              </td>
            </tr>
          </template>
        </tbody>
      </table>
    </template>
    <template v-else>
      <p class="example-disabled">Connect with a wallet to access this example</p>
    </template>
  </div>
</template>
