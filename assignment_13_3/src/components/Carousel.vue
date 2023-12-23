<template>
    <div class="carousel">
        <div class="carousel-container" :style="{ transform: `translateX(-${currentIndex * 100}%)` }">
        <div v-for="(item, index) in items" :key="index" class="carousel-item">
            <img :src="item.src" :alt="item.alt" class="carousel-image" />
            <div class="carousel-caption" v-if="item.caption">{{ item.caption }}</div>
            </div>
        </div>
        <button class="prev" @click="prevItem">&#10094;</button>
        <button class="next" @click="nextItem">&#10095;</button>
        <div class="indicators">
            <span v-for="(item, index) in items" :key="index" :class="{ active: index === currentIndex }" @click="goToItem(index)"></span>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        items: {
            type: Array,
            required: true
        }
    },
    data() {
        return {
            currentIndex: 0,
            intervalId: null,
            intervalDuration: 3000
        };
    },
    methods: {
        prevItem() {
            this.currentIndex = (this.currentIndex - 1 + this.items.length) % this.items.length;
        },
        nextItem() {
            this.currentIndex = (this.currentIndex + 1) % this.items.length;
        },
        goToItem(index) {
            this.currentIndex = index;
        },
        startAutoplay() {
            this.intervalId = setInterval(() => {
            this.nextItem();
            }, this.intervalDuration);
        },
        stopAutoplay() {
            clearInterval(this.intervalId);
            }
        },
        mounted() {
            this.startAutoplay();
        },
        beforeDestroy() {
            this.stopAutoplay();
        }
    };
</script>
<style scoped>
.carousel {
    position: relative;
    max-width: 100%;
    overflow: hidden;
}

.carousel-container {
    display: flex;
    transition: transform 0.5s ease;
}

.carousel-item {
    flex: 0 0 100%;
}

.carousel-image {
    width: 100%;
}

.prev,
.next {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
}

.indicators {
    text-align: center;
}

.indicators span {
    display: inline-block;
    width: 10px;
    height: 10px;
    margin: 0 5px;
    border-radius: 50%;
    background-color: #ccc;
    cursor: pointer;
}
.indicators span.active {
    background-color: #333;
}
</style>