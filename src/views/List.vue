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
        <v-list-item
          @click="doneBought(item.id)"
          :class="{ 'blue lighten-5' : item.bought }"
        >
          <template>
            <v-list-item-action>
              <v-checkbox
                :input-value="item.bought"
                color="primary"
              />
            </v-list-item-action>

            <v-list-item-content>
              <v-list-item-title
                :class="{ 'text-decoration-line-through' : item.bought }"
              >
                {{ item.title }}
              </v-list-item-title>
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
        title: 'Muesli',
        bought: false
      },
      {
        id: 2,
        title: 'Milk',
        bought: false
      },
      {
        id: 3,
        title: 'Aple',
        bought: false
      }
    ]
  }),
  components: {
  },
  methods: {
    doneBought (id) {
      // в списке покупок ищем нужную запись
      const item = this.shoppingList.filter(item => item.id === id)[0]
      // Изменяем статус покупки
      item.bought = !item.bought
    }
  }
}
</script>
