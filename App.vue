<template>
  <view class="container">
    <text>Location:</text>
    <text>{{location.latitude}}</text>
    <touchable-opacity :on-press="getLocation" >
        <text>get location</text>
    </touchable-opacity>
  </view>
</template>

 <script>
import { Constants, Location, Permissions } from "expo";

export default {
  data: function() {
    return {
      location: {},
      errorMessage: ""
    };
  },
  methods: {
    getLocation: function() {
      Permissions.askAsync(Permissions.LOCATION).then(status => {
        if (status !== "granted") {
          errorMessage = "Permission to access location was denied";
        }
        Location.getCurrentPositionAsync({}).then(location1 => {
          location = location1;
        });
      }).catch((err)=>{
        console.log(err);
     });
    }
  }
};
</script>
