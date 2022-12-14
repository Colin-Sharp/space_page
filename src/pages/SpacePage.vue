<template>
    <div class="space-page">
        <h1 class="space-page__title">
            Space
        </h1>
            <section class="space-page__highlights">
                <article class="space-page__highlights__card" v-for="item in sortedArray" v-bind:key="item.id" 
                    :class="{'space-page__highlights__card__from-parterns': item.fromPartners }">
                    <img class="space-page__highlights__card__star" src="../assets/star.png" alt="star">
                    <MuseumHighlight :highlight="item">
                    </MuseumHighlight>
                </article>
            </section>
    </div>
</template>

<script>
import _ from 'lodash';
import MuseumHighlight from '../components/MuseumHighlight.vue';

export default {
    name: 'SpacePage',
    components: {
        MuseumHighlight,
    },
    mixins: [
    ],
    props: {

    },
    data() {
        return {
            spaceHighlights: [
                {
                    date: '2020-04-20 12:20:00',
                    description: 'Asteroids are minor planets, especially of the inner Solar System. Larger asteroids have also been called planetoids.',
                    id: 1,
                    image: '',
                    name: 'Asteroids',
                },
                {
                    date: '2020-05-20 15:50:00',
                    description: 'A comet is an icy, small Solar System body that, when passing close to the Sun, warms and begins to release gases, a process called outgassing.',
                    id: 9,
                    image: '',
                    name: 'Comets',
                },
                {
                    date: '2020-05-01 9:22:00',
                    description: 'The term planet is ancient, with ties to history, astrology, science, mythology, and religion.',
                    id: 7,
                    image: '',
                    name: 'Planets',
                    news: {
                        date: '2020-08-18 18:00:00',
                        title: 'Attend our talk about Jupiter with Dr. Hogarth',
                    },
                    quiz: 'https://planetquiz.space',
                },
                {
                    date: '2020-07-05 4:10:00',
                    description: 'A meteor shower is a celestial event in which a number of meteors are observed to radiate, or originate, from one point in the night sky.',
                    id: 12,
                    image: '',
                    name: 'Meteor showers',
                    news: {
                        title: 'The Lyrids will peak at on April 21-22 2021, at night',
                    },
                },
            ],
            spacePartners: {
                observatory: {
                    createdAt: '2020-06-01 11:45:00',
                    info: 'The Mauna Kea Observatories (MKO) are a number of independent astronomical research facilities and large telescope observatories that are located at the summit of Mauna Kea on the Big Island of Hawai??i, United States.',
                    image: '',
                    name: 'Mauna Kea Observatories',
                },

            },
        };
    },
    computed: {
        partnersArray() {
            return _(this.spacePartners).map((item, key) => {
                return {
                    id: key,
                    fromPartners: true,
                    date: item.createdAt,
                    image: item.image,
                    name: item.name,
                    description: item.info,
                };
            }).value();
        },
        mergedArray() {
            return _.concat(this.partnersArray, this.spaceHighlights);
        },
        sortedArray() {
            return _.orderBy(this.mergedArray, 'date', 'desc');
        },
    },
    methods: {

    },
    created() {
    }
};
</script>

<style lang="scss" scoped>
.space-page {
    display: flex;
    flex-direction: column;
    width: 90%;
    margin: 0 auto;

    &__title {
        color: #2c3791;
        font-size: 24px;
        font-weight: 600;
        text-align: center;
        @media screen and (min-width: 40em) {
            text-align: left;
        }
    }

    &__highlights {
        display: flex;
        flex-direction: column;
        align-items: center;
        width: 100%;
        @media screen and (min-width: 40em) {
            justify-content: space-between;
            flex-direction: row;
            align-items: stretch;
            flex-wrap: wrap;
        }

        &__card {
            background: rgb(97, 130, 173);
            box-shadow: 0 0 4px rgba(0,0,0,0.4);
            position: relative;
            text-align: left;
            flex: auto;
            max-width: 100%;
            margin-bottom: 2rem;
            @media screen and (min-width: 40em) {
                flex: 0 1 calc(50% - 2em);
            }
            @media screen and (min-width: 70em) {
                flex: 0 1 calc(25% - 2em);
            }

            &__from-parterns {
                background: rgba(66, 158, 104, 0.616);
            }
            
            &__star {
                position: absolute;
                top: -17px;
                right: -17px;
                width: 40px;
                height: 40px;
                z-index: 10;
            }
        }
    }
}
</style>
