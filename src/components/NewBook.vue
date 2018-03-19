<template>
    <div class="panel panel-default">
        <div class="panel-heading">
            <h3>Add Book</h3>
        </div>
        <div class="panel-body">
            <form id="form" class="form-inline" @submit.prevent="addBook">
                <div class="form-group">
                    <label for="bookTitle">Title:</label>
                    <input type="text" id="bookTitle" class="form-control" v-model="newBook.title">
                </div>
                <div class="form-group">
                    <label for="bookAuthor">Author:</label>
                    <input type="text" id="bookAuthor" class="form-control" v-model="newBook.author">
                </div>
                <div class="form-group">
                    <label for="bookUrl">URL:</label>
                    <input type="text" id="bookUrl" class="form-control" v-model="newBook.url">
                </div>
                <input type="submit" class="btn btn-primary" value="Add Book">
            </form>
        </div>
    </div>
</template>


<script>
import { booksRef } from '../App.vue' 
    
export default {
    data() {
        return {
            newBook: {
                title: '',
                author: '',
                url: ''
            }  
        }
    },
    methods: {
        addBook() {
            booksRef.push(this.newBook)
            this.newBook.title = ''
            this.newBook.author = ''
            this.newBook.url = ''
        }
    }
}
</script>