<template>
    <div class="modal fade" :id="getMovie" tabindex="-1" role="dialog" :aria-labelledby="getAriald" aria-hidden="true">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" :id="getMovie">{{ movie.title }}</h5>
                    <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                    <span aria-hidden="true">&times;</span>
                    </button>
                </div>
                <div class="modal-body">
                    <img :src="movie.backdrop_url" class="img-size" alt="">
                    <hr>
                    <h4><span class="badge badge-secondary badge-info">{{ movie.user_rating }}</span></h4>
                    <p>{{ movie.overview }}</p>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "MovieListItemModal",
    props: {
        movie: Object,
    },
    computed: {
        getMovie() {
            return `movie-${this.movie.id}`
        },
        getAriald() {
            return `modalLabel-${this.movie.id}`
        }
    }
}
</script>

<style>
.img-size {
    width: 100%;
}
</style>