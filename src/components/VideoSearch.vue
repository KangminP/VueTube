<template>
    <div class="container mt-5">
        <div class="input-group mb-3 w-50 mx-auto">
            <input type="text" class="form-control" v-model="keyword" @keydown.enter="searchVideo">
            <div class="input-group-append">
                <button class="btn btn-outline-secondary" type="button" id="button-addon2" @click="searchVideo">검색</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'VideoSearch',
    data() {
        return {
            keyword: '',
        }
    },
    methods: {
        searchVideo() {
            this.$emit('search-video', this.keyword)
            this.keyword = ''
        }
    }
}
</script>

<style>

</style>