<template>
    <div class="col-md-12 form-group">
        <label class="form-label">Yazar Adi Giriniz</label>
        <input class="form-control" v-model="authorName">
        <button @click="addAuthor" class="btn btn-primary form-control">Ekle</button>
    </div>
</template>


<script>
export default{
    data(){
        return{
        authorName : null,
        }
    },
    methods:{
        addAuthor(){
            this.$emit("addAuthor", this.authorName)
        }
    }
}
</script>