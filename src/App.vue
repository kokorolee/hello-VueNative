<template>
    <nb-container :style="{ backgroundColor: '#fff' }">
        <nb-header>
          <nb-body>
            <nb-title>Hello VueNative</nb-title>
          </nb-body>
          <nb-right />
        </nb-header>
        <nb-content :scrollEnabled="false">
            <nb-swipe-row
                :leftOpenValue="75"
                :rightOpenValue="-75"
                :left="getSwipeLeftComponet()"
                :right="getSwipeRightComponet()"
                :body="getSwipeBodyComponet()"
            />
        </nb-content>
    </nb-container>
</template>

<script>
import React from "react";
import { Button, Icon, Text, View } from "native-base";
export default {
  methods: {
    getSwipeLeftComponet: function() {
      return (
        <Button success onPress={() => alert("Add")}>
          <Icon active name="add" style={{ color: "#FFF" }} />
        </Button>
      );
    },
    getSwipeRightComponet: function() {
      return (
        <Button danger onPress={() => alert("Trash")}>
          <Icon active name="trash" />
        </Button>
      );
    },
    getSwipeBodyComponet: function() {
      return (
        <View style={{ paddingLeft: 20 }}>
          <Text>Swipe me to left and right</Text>
        </View>
      );
    }
  }
};
</script>
