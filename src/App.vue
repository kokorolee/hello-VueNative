<template>
    <nb-container :style="{ backgroundColor: '#fff' }">
        <nb-header>
          <nb-body>
            <nb-title>Hello VueNative</nb-title>
          </nb-body>
          <nb-right />
        </nb-header>
      <nb-header />
      <nb-content padder>
        <nb-form>
            <nb-item fixedLabel>
                <nb-label>Username</nb-label>
                <nb-input />
            </nb-item>
            <nb-item fixedLabel last>
                <nb-label>Password</nb-label>
                <nb-input v-if="!isShowpasswords" secureTextEntry />
                <nb-input v-else="isShowpasswords"/>
            </nb-item>
        </nb-form>
        <nb-button block @click="showPasswords()">
          <nb-text>
            Show
          </nb-text>
        </nb-button>
        <nb-button block :style="{ margin: 15, marginTop: 50 }">
            <nb-text>Sign In</nb-text>
        </nb-button>
             </nb-content>
    </nb-container>
</template>

<script>
import React from "react";
import { Button, Icon, Text, View } from "native-base";
export default {
  data: function(){
    return{
      email: '',
      password: '',
      isShowpasswords: false
    }
  },
  methods: {
    showPasswords: function(){
      alert("11")
      const _self = this
      _self.isShowpasswords = true
    },
  }
};
</script>
