<template>
    <div class="accordination">
        <div v-for="(item, index) in accordionItems" :key="index" class="accordion-item">
            <div class="accordion-header" @click="toggleItem(index)">
                {{ item.title }}
                <span v-if="item.expanded" class="icon">-</span>
                <span v-else class="icon">+</span>
            </div>
            <div v-if="item.expanded" class="accordion-content">
                <slot :name="item.name"></slot>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        accordionItems: {
            type: Array,
            required: true
        }
    },
    methods: {
        toggleItem(index) {
            this.$emit('create', index);
        },
        
    }
};
</script>

<style>
.accordination {
    display: flex;
    flex-direction: column;
    width: 100%;
    gap: 50px;
}
.accordion-item {
    border: 1px solid #000000;
    margin-bottom: 5px;
}
.accordion-header {
    background-color: teal;
    font-weight: bold;
    font-size: 20px;
    padding: 10px;
    cursor: pointer;
    display: flex;
    justify-content: space-between;
    align-items: center;
}
.accordion-content {
    background: #F4d35e;
    padding: 10px;
    overflow: hidden;
    transition: max-height 0.3s ease-out;
}
.icon {
    font-weight: bold;
    margin-left: 5px;
}
</style>