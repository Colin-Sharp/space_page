<template>
    <div class="museum-highlight">
        
        <img class="museum-highlight__image" :src="image" :alt="highlight.name">
     
        <div class="museum-highlight__content">
            <h3>{{highlight.name}}</h3>
            <p>{{highlight.description}}</p>
            <div v-if="news">
                <h4>News</h4>
                <p v-if="news.date">
                    <span>Date:</span> {{hightlight.news.date}}
                </p>
                <p v-if="news.title">
                    <span>Title:</span> {{hightlight.news.title}}
                </p>
            </div>
            <div v-if="!!quiz">
                <h4>Quiz</h4>
                <span>Link:</span> <a :href="quiz" target="blank">{{quiz}}</a>
            </div>
        </div>
    </div>
</template>

<script>
import _ from 'lodash';

export default {
    name: 'MuseumHighlight',
    components: {

    },
    mixins: [
    ],
    props: {
        highlight: Object
    },
    data() {
        return {

        };
    },
    computed: {
        news() {
            if (!this.highlight.news) return null;

            return _(this.highlight.news).map((item) => {
                return {
                    date: item?.date || null,
                    title: item?.title || null
                };
            }).value();
        },
        image() {
            return this.highlight.image || 'https://images.unsplash.com/photo-1538370965046-79c0d6907d47?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1169&q=80';
        },
        quiz() {
            return this.highlight.quiz || null;
        }
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
        max-width: 100%;
    }
    &__content {
        padding: 10px;
        a {
            color: rgb(221, 221, 24);
        }
        span {
            font-weight: 600;
        }
    }
}
</style>
