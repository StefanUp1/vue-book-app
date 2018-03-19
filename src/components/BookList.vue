<template>
    <div>
        <div class="page-header">
          <h1>Vue.js 2 & Firebase Application</h1>
      </div>
      <div class="panel panel-default">
          <div class="panel-heading">
              <h3>Books Lists</h3>
          </div>
          <div class="panel-body">
              <table class="table table-striped">
                  <thead>
                      <tr>
                          <th>
                              Title
                          </th>
                          <th>
                              Author
                          </th>
                          <th>
                              Delete
                          </th>
                      </tr>
                  </thead>
                  <tbody>
                      <tr v-for="book in books">
                          <td>
                              <a :href="book.url">{{ book.title }}</a>
                          </td>
                          <td>
                              {{ book.author }}
                          </td>
                          <td>
                              <span class="glyphicon glyphicon-trash" @click="deleteBook(book)"></span>
                          </td>
                      </tr>
                  </tbody>
              </table>
          </div>
      </div>
    </div>
</template>


<script>
import toastr from 'toastr'
import { booksRef } from '../App.vue'
    
export default {
    name: 'booklist',
    props: ['books'],
    methods: {
        deleteBook(book) {
            booksRef.child(book['.key']).remove()
            toastr.success('Book removed')
        }
    }
}
</script>


<style scoped>
    .glyphicon-trash:hover {
        color: red;
        cursor: pointer;
    }
</style>