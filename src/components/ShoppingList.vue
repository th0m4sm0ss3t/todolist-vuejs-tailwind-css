<template>
  <div
    class=
    "
      flex
      flex-col
      flex-wrap
      justify-between
      h-full
    "
  >
    <ul class="w-full">
      <li
        v-if="shoppingList.length < 1"
        class=
        "
          bg-blue-200
          border-b
          border-blue-50
          w-full
          p-6
          py-2
          text-center
        "
      >
        Your shopping list is currently empty.
      </li>
      <li
        v-else-if="shoppingList.length === 1"
        class=
        "
          bg-blue-200
          border-b
          border-blue-50
          w-full
          p-6
          py-2
          text-center
        "
      >
        Your shopping list has {{ shoppingList.length }} item.
      </li>
      <li
        v-else
        class=
        "
          bg-blue-200
          border-b
          border-blue-50
          w-full
          p-6
          py-2
          text-center
        "
      >
        Your shopping list has {{ shoppingList.length }} items.
      </li>
      <li
        v-for="(item, index) in shoppingList"
        :key="item.id"
        class=
        "
          bg-blue-100
          border-b
          border-blue-50
          w-full
          flex
          justify-between
          p-6
          py-2
        "
      >
        {{ item.name }}
        <span
          @click="removeElement(index)"
          class=
          "
            pl-6
            border-l-2
            border-green-600
            cursor-pointer
          "
        >
          <svg fill="none" viewBox="0 0 24 24" height="24" width="24" xmlns="http://www.w3.org/2000/svg">
            <path xmlns="http://www.w3.org/2000/svg" d="M7 4C7 2.89543 7.89543 2 9 2H15C16.1046 2 17 2.89543 17 4V6H18.9897C18.9959 5.99994 19.0021 5.99994 19.0083 6H21C21.5523 6 22 6.44772 22 7C22 7.55228 21.5523 8 21 8H19.9311L19.0638 20.1425C18.989 21.1891 18.1182 22 17.0689 22H6.93112C5.88184 22 5.01096 21.1891 4.9362 20.1425L4.06888 8H3C2.44772 8 2 7.55228 2 7C2 6.44772 2.44772 6 3 6H4.99174C4.99795 5.99994 5.00414 5.99994 5.01032 6H7V4ZM9 6H15V4H9V6ZM6.07398 8L6.93112 20H17.0689L17.926 8H6.07398ZM10 10C10.5523 10 11 10.4477 11 11V17C11 17.5523 10.5523 18 10 18C9.44772 18 9 17.5523 9 17V11C9 10.4477 9.44772 10 10 10ZM14 10C14.5523 10 15 10.4477 15 11V17C15 17.5523 14.5523 18 14 18C13.4477 18 13 17.5523 13 17V11C13 10.4477 13.4477 10 14 10Z" fill="#059669">
            </path>
          </svg>
        </span>
      </li>
    </ul>
    <form
      action=""
      @submit="addElement"
      class=
      "
        flex
        justify-center
        py-1
        w-full
        h-8
        mt-4
        mb-4
      "
    >
      <input
        type="text"
        v-model="addedItem"
        class=
        "
          border
          border-green-600
          rounded-lg
          text-green-600
          px-1
        "
      >
      <button type="submit">
        <svg fill="none" viewBox="0 0 24 24" height="24" width="24" xmlns="http://www.w3.org/2000/svg">
          <path xmlns="http://www.w3.org/2000/svg" d="M12 4C12.5523 4 13 4.44772 13 5V11H19C19.5523 11 20 11.4477 20 12C20 12.5523 19.5523 13 19 13H13V19C13 19.5523 12.5523 20 12 20C11.4477 20 11 19.5523 11 19V13H5C4.44772 13 4 12.5523 4 12C4 11.4477 4.44772 11 5 11H11V5C11 4.44772 11.4477 4 12 4Z" fill="#059669">
          </path>
        </svg>
      </button>
    </form>
    <p
      v-if='errorMessage !== ""'
      class=
      "
        m-4
        text-center
        text-red-600
        text-lg
        font-bold
      "
    >{{ errorMessage }}</p>
  </div>
</template>

<script>

export default {
  name: 'ShoppingList',
  data() {
    return {
      shoppingList: [],
      addedItem: '',
      futurAddedElementId: 1,
      errorMessage: '',
    };
  },
  methods: {
    addElement(event) {
      event.preventDefault();

      if (this.addedItem !== '') {
        this.shoppingList.push({
          id: this.futurAddedElementId + Math.floor(Math.random() * 150),
          name: this.addedItem,
        });

        this.addedItem = '';
        this.errorMessage = '';
      } else {
        this.errorMessage = 'Please enter an item.';
      }
    },
    removeElement(index) {
      this.shoppingList.splice(index, 1);
    },
  },
};
</script>
