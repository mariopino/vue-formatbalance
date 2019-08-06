<template>
  <div>
    <h1>Polkadot util formatBalance function test</h1>

    <h2>DEC</h2>
    
    <p align="center">
      <table width="700">
        <tr>
          <td width="300"><strong>Raw balance</strong></td>
          <td>{{ balance }}</td>
        </tr>
        <tr>
          <td><strong>Balance (formatNumber)</strong></td>
          <td>{{ formatNumber(balance) }}</td>
        </tr>        
        <tr>
          <td><strong>Balance (formatDot)</strong></td>
          <td>{{ formatDot(balance) }} DOT</td>
        </tr>
        <tr>
          <td><strong>Balance (formatBalance)</strong></td>
          <td>{{ _formatBalance(balance) }} DOT</td>
        </tr>       
      </table>
    </p>

    <h2>HEX</h2>

    <p align="center"> 
      <table width="700">
        <tr>
          <td width="300"><strong>Raw balance</strong></td>
          <td>{{ balanceHex }}</td>
        </tr>
        <tr>
          <td width="300"><strong>Raw balance (DEC)</strong></td>
          <td>{{ parseInt(balanceHex, 16) }}</td>
        </tr>        
        <tr>
          <td><strong>Balance (formatNumber)</strong></td>
          <td>{{ formatNumber(parseInt(balanceHex, 16)) }}</td>
        </tr>          
        <tr>
          <td><strong>Balance (formatDot)</strong></td>
          <td>{{ formatDot(balanceHex) }} DOT</td>
        </tr> 
        <tr>
          <td><strong>Balance (formatBalance)</strong></td>
          <td>{{ _formatBalance(balanceHex) }} DOT</td>
        </tr>               
      </table>
    </p>

  </div>
</template>

<script>
import { formatBalance, isHex } from '@polkadot/util';

export default {
  data: function() {
    return {
      balance: '400437982902631', // 0.400 DOT
      balanceHex: '0x000000000000000014b9aad5d3b20000' // 1493.413 DOT
    }
  },
  methods: {
    formatNumber(amount) {
      if (isHex(amount)) {
        return (parseInt(amount, 16).toString()).replace(/(\d)(?=(\d{3})+(?!\d))/g, '$1,');
      } else {
        return (amount.toString()).replace(/(\d)(?=(\d{3})+(?!\d))/g, '$1,');
      }
    },
    formatDot(amount) {
      if (isHex(amount)) {
        return (parseInt(amount, 16) / 1000000000000000).toFixed(3);
      } else {
        return (amount / 1000000000000000).toFixed(3);
      }
    },
    _formatBalance(amount) {
      return formatBalance(amount);
    }
  }
}
</script>

<style>
</style>
