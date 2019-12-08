<template>
  <app-navigator></app-navigator>
</template>

<script>
import {
  createAppContainer,
  createStackNavigator,
  createDrawerNavigator,
  createBottomTabNavigator
} from "vue-native-router";

import HomeScreen from './src/views/HomePage';
import DetailsScreen from './src/views/DetailPage';
import LinkScreen from './src/views/LinkPage';

const DrawerNavigator = createDrawerNavigator(
  {
    Home: { screen: HomeScreen },
    Link: LinkScreen
  }
)

const StackNavigator = createStackNavigator(
  {
    Home: DrawerNavigator,
    Details: DetailsScreen,
  },
  {
    initialRouteName: 'Home',
  }
);

const btmTabNavigator = createBottomTabNavigator({
  Heroes: StackNavigator
})

const AppNavigator = createAppContainer(btmTabNavigator);

export default {
  components: { AppNavigator },
}
</script>