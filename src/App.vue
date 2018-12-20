<template>
  <nb-container>
    <nb-header />
    <nb-content>
      <nb-list
        :leftOpenValue="75"
        :rightOpenValue="-75"
        :dataSource="getListArr()"
        :renderRow="getListItemRow"
        :renderLeftHiddenRow="getLeftHiddenRowComponet"
        :renderRightHiddenRow="getRighttHiddenRowComponet"
      >
      </nb-list>
    </nb-content>
    <nb-header searchBar rounded>
        <nb-input v-model="messages" placeholder="Your messages" />
      <nb-button v-bind:on-press="sendMessage"transparent>
        <nb-icon active name="search" />
      </nb-button>
    </nb-header>
  </nb-container>
</template>
<script>
import React from "react";
import { ListView } from "react-native";
import { Button, Icon, Text, ListItem } from "native-base";
export default {
  data: function() {
    return {
      messages: '',
      ds: new ListView.DataSource({ rowHasChanged: (r1, r2) => r1 !== r2 }),
      basic: true,
      listViewData: [
        "Dummy message"
      ]
    };
  },
  methods: {
    sendMessage: function (){
      let _self = this
      if (_self.messages != ''){
        _self.listViewData.push(_self.messages)
        _self.messages = ''
      }
    },
    deleteRow: function(secId, rowId, rowMap) {
      rowMap[`${secId}${rowId}`].props.closeRow();
      const newData = [...this.listViewData];
      newData.splice(rowId, 1);
      this.listViewData = newData;
    },
    getLeftHiddenRowComponet: function(data) {
      return (
        <Button full onPress={() => alert(data)}>
          <Icon active name="information-circle" />
        </Button>
      );
    },
    getRighttHiddenRowComponet: function(data, secId, rowId, rowMap) {
      return (
        <Button full danger onPress={_ => this.deleteRow(secId, rowId, rowMap)}>
          <Icon active name="trash" />
        </Button>
      );
    },
    getListArr: function() {
      return this.ds.cloneWithRows(this.listViewData);
    },
    getListItemRow: function(data) {
      return (
        <ListItem>
          <Text>{data}</Text>
        </ListItem>
      );
    }
  }
};
</script>
