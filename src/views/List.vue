<template>
  <div class="home pa-6">
    <v-list
      subheader
      flat
    >

      <div
        v-for="item in shoppingList"
        :key="item.id"
      >
        <v-list-item>
          <template v-slot:default="{ active, }">
            <v-list-item-action>
              <v-checkbox
                :input-value="active"
                color="primary"
              />
            </v-list-item-action>

            <v-list-item-content>
              <v-list-item-title>{{ item.title }} </v-list-item-title>
            </v-list-item-content>
          </template>
        </v-list-item>
        <v-divider />
      </div>

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
