<template>
    <div class="col-md-12 form-group mt-5">
        <label class="form-label">Kitap Adi Giriniz</label>
        <input class="form-control" type="Yazar Ekle" v-model="bookName">
        <select id="yazarlar" class="form-control" aria-label="Default select example" v-model="authorID">
            <option selected>Yazar Seçiniz</option>
            <option v-for = "item in sendAuthor.data" :key="item.authorID" :value="item.authorID">{{ item.authorName }}</option>
        </select>
        <button @click="AddBook" class="btn btn-primary form-control">Ekle</button>
    </div>
</template> 


<script>
export default{
    data(){
        return{
            bookName: null,
            authorID: null,
        }
    },
    props:["sendAuthor"],
    methods:{
        AddBook(){
            this.$emit("addBook", this.bookName, this.authorID)
        }
    },
}
</script>