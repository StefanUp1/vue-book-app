<template>
  <div id="app" class="container">
      <app-book-list :books="books"></app-book-list>
      <app-new-book></app-new-book>
  </div>
</template>

<script>
import Firebase from 'firebase'
import BookList from './components/BookList.vue'
import NewBook from './components/NewBook.vue'


    
let config = {
    apiKey: "AIzaSyAXFZwAhXmypO7WHfIRx2rc8tOjJqgeOmA",
    authDomain: "vue-book2-http.firebaseapp.com",
    databaseURL: "https://vue-book2-http.firebaseio.com",
    projectId: "vue-book2-http",
    storageBucket: "vue-book2-http.appspot.com",
    messagingSenderId: "777470277580"
}

let app = Firebase.initializeApp(config);
let db = app.database()

export const booksRef = db.ref('books')
    
export default {
    name: 'App',
    firebase: {
        books: booksRef
    },
    components: {
        appBookList: BookList,
        appNewBook: NewBook
    }
}
</script>

<style>
    #app {
        margin: auto;
        font-family: 'Avenir', Helvetica;
    }
</style>
