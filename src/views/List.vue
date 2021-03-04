<template>
  <div class="home pa-6">
    <v-list
      subheader
      flat
    >

      <v-list-item
        v-for="item in shoppingList"
        :key="item.id"
      >
        <template v-slot:default="{ active, }">
          <v-list-item-action>
            <v-checkbox
              :input-value="active"
              color="primary"
            ></v-checkbox>
          </v-list-item-action>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }} </v-list-item-title>
          </v-list-item-content>
        </template>
      </v-list-item>

    </v-list>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'List',
  data: () => ({
    shoppingList: [
      {
        id: 1,
        title: 'Muesli'
      },
      {
        id: 2,
        title: 'Milk'
      },
      {
        id: 3,
        title: 'Aple'
      }
    ]
  }),
  components: {
  }
}
</script>
