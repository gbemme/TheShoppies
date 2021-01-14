<template>
  <v-app id="app">
    <ShoppiesHeader></ShoppiesHeader>
    <v-main id="scrolling-techniques" class="overflow-y-auto">
            <router-view></router-view>
          </v-main>
        </v-app>
      </template>

      <script>

      import ShoppiesHeader from "@/movieAward/components/ShoppiesHeader";
      export default {
        name: 'App',

        components: {
          ShoppiesHeader
        },

        data: () => ({
          //
        }),
      };
      </script>
      <style>
      .search-no-border.v-text-field.v-text-field--solo:not(.v-text-field--solo-flat) > .v-input__control > .v-input__slot{
        box-shadow: none !important;
      }
      </style>
