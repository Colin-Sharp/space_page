<template>
    <div class="museum-highlight">
        <!-- I have added a default image just for display as the data didn't have any images -->
        <img class="museum-highlight__image" :src="!!image ? image : 'https://images.unsplash.com/photo-1538370965046-79c0d6907d47?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1169&q=80'" alt="name">
     
        <div class="museum-highlight__content">
            <h3>{{name}}</h3>
            <p>{{description}}</p>
            <div v-if="news && news.date || news && news.title">
                <h4>News</h4>
                <p v-if="news && news.date">Date: {{news.date}}</p>
                <p v-if="news && news.title">Title: {{news.title}}</p>
            </div>
            <div v-if="quiz">
                <h4>Quiz</h4>
                 <a href="quiz" target="blank">{{quiz}}</a>
            </div>
        </div>
    </div>
</template>

<script>

export default {
    name: 'MuseumHighlight',
    components: {

    },
    mixins: [
    ],
    props: {
        date: String,
        description: String,
        id: String || Number,
        image: String,
        name: String,
        fromPartners: Boolean,
        news: Object,
        quiz: String
    },
    data() {
        return {

        };
    },
    computed: {
        
    },
    methods: {

    },
    created() {

    },
};
</script>

<style lang="scss" scoped>
.museum-highlight {
    &__image {
        max-width: 400px;
        @media screen and (max-width: 480px) {
            max-width: 300px;
        } 
    }
    &__content {
        padding: 10px;
    }
}
</style>
