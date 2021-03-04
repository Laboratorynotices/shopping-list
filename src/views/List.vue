<template>
  <div class="home pa-6">
    <v-text-field
      outlined
      label="Add item"
      append-icon="mdi-cart-plus"
      clearable
      v-bind="newItemTitle"
      @click:append="addNewItem"
      @keyup.enter="addNewItem"
    />
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

            <div class="v-list-item__action">
              <button
                type="button"
                class="v-btn v-btn--icon v-btn--round theme--light v-size--default"
                @click.stop="deleteItem(item.id)"
              >
                <span class="v-btn__content">
                  <i
                    aria-hidden="true"
                    class="v-icon notranslate mdi mdi-delete theme--light grey--text text--lighten-1"
                  />
                </span>
              </button>
            </div>
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
    // Список покупок по умолчанию
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
    ],
    // Переменная для создания новых элементов из списка
    newItemTitle: ''
  }),
  components: {
  },
  methods: {
    /**
     * Отмечаем элемент как купленным.
     */
    doneBought (id) {
      // в списке покупок ищем нужную запись
      const item = this.shoppingList.filter(item => item.id === id)[0]
      // Изменяем статус покупки
      item.bought = !item.bought
    },
    /**
     * Удаляем элемент из списка
     */
    deleteItem (id) {
      // перебираем все элементы в списке и смотрим,
      // чтобы id его не сходился с той, что надо убрать.
      this.shoppingList = this.shoppingList.filter(item => item.id !== id)
    },
    /**
     * Добавляем новый элемент
     */
    addNewItem () {
      // Создаём новый элемент с правильной структурой
      const newItem = {
        id: Date.now(),
        title: this.newItemTitle,
        bought: false
      }
      // добавляем созданный элемент к уже существующему списку
      this.shoppingList.push(newItem)
      // очищаем поле ввода
      this.newItemTitle = ''
    }
  }
}
</script>
