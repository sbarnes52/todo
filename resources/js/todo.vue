<template>

    <h1 :class="titleClass">To-do List</h1> <!--Displays a header with the title style class-->

    <form @submit.prevent="addItem(newItem)"> <!--An input box and button that do not reload the page-->
        <input v-model="newItem">
        <button>Add item</button> <!--Adds the current input to the to-do list-->
    </form>

    <ol> <!--Displays the to-do list as a numbered list-->
        <li :class="itemClass" v-for="item in itemList" :key="item.id">
            {{ item.text }} <!--Displays only the text of a list item-->
            <button @click="removeItem(item)">Remove</button> <!--Removes its associated item from the list-->
        </li>
    </ol>

</template>

<script>

let id = 0; // Initialises the id value that will be used to generate ids for items

export default {
    data() {
        return {
            titleClass: 'title', // Used to bind styles to elements
            itemClass: 'item',
            newItem: 'Add item here', // The item to be added to the to-do list, starts prefilled
            itemList: [
                {id: id++, text: 'Example Item 1'}, // An example item in the to-do list, with a unique id and some text to display
                {id: id++, text: 'Example Item 2'},
            ],
        }
    },

    methods: {
        addItem (addition) { // Adds the current input box's value to the end of the to-do list
            this.itemList.push({id: id++, text: addition});
        },
        removeItem (removal) { // Removes an item from the list upon clicking its button
            this.itemList = this.itemList.filter(item => item !== removal);
        },
    },
}

</script>

<style>

.title{ /* Used to change the style of the title heading */
    color:navy;
}

.item{ /* Used to change the style of each list item */
    color:black;
}

</style>