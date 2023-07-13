<template>
    <div class="star-rating">
        <span v-for="index in starLimit" :key="index" class="star star--outlined"></span>
    </div>
    <div class="star-rating__colored" :style="ratingWidthStyle">
        <span v-for="index in starLimit" :key="index" class="star star--colored"></span>
    </div>
</template>

<script>
export default {
    name: "StarRating",
    props: {
        rating: {
            type: Number,
            default: 1,
        },
        starLimit: {
            type: Number,
            default: 5,
        },
    },
    computed: {
        ratingWidth() {
            return this.rating / this.starLimit * 100
        },
        ratingWidthStyle() {
            return `width: ${this.ratingWidth}%;`
        }
    }
};
</script>

<style lang="scss" scoped>
.star-rating {
    position: relative;
    display: inline-flex;

    &__colored {
        position: absolute;
        display: inline-flex;
        width: 0;
        height: 100%;
        top: 0;
        left: 0;
        overflow: hidden;
    }

    .star {
        display: inline-block;
        width: 16px;
        height: 16px;
        margin: 0 3px;
        flex-shrink: 0;

        &--colored {
            background: url("../images/star-orange.svg") center no-repeat;
        }

        &--outlined {
            background: url("../images/star-blue.svg") center no-repeat;
        }
    }
}
</style>
