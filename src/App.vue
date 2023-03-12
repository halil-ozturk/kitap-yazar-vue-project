<script>
import AddAuthor from './components/AddAuthor.vue'
import AddBook from './components/AddBook.vue'
import SearchBar from './components/SearchBar.vue'
import Table from './components/Table.vue'
import Pagination from './components/Pagination.vue'
import GetAuthors from './components/GetAuthors.vue'
import axios from 'axios'

export default {
  components: {
    AddAuthor,
    AddBook,
    SearchBar,
    Table,
    Pagination,
    GetAuthors,
  },
  data() {
    return {
      author: null,
      bookName: null,
      authorID: null,
      authorList: [],
    }
  },
  beforeMount () {
    this.getAuthors()
  },
  methods: {
    addAuthor(authorName) {

      this.author = authorName
      var postData = {
        name: authorName,
      }
      axios.post("https://localhost:7161/api/service/postauthor",
        postData)
        .then()
        .catch()
    },
    getAuthors(){
      axios.get("https://localhost:7161/api/service/getallauthors")
      .then(
        response => (this.authorList = response)
      )
      .catch()
    },
    addBook(bookName, authorID) {
      this.bookName = bookName
      this.authorID = authorID
      var postData = {
        name: bookName,
        authorID: authorID,
        authorName: "",
      }
      axios.post("https://localhost:7161/api/service/postbook",
      postData)
      .then()
      .catch()
    }
  }
}
</script>

<template>
  <div class="container">
    <AddAuthor @addAuthor="addAuthor"></AddAuthor>
    <AddBook :sendAuthor=" authorList" @addBook="addBook"></AddBook>
    <SearchBar></SearchBar>
    <Table></Table>
    <Pagination></Pagination>
    <GetAuthors></GetAuthors>
  </div>
</template>






<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
