<template>
    <div class="outerWrapper">
        <div class="innerWrapper">
        <div class="photo" :style="'background-image: url(' + photo + ')'"></div>
        <div class="description">
            <h2 class="title">{{ title }}</h2>
            <p class="description">
                {{ description }}
            </p>
        </div>
        </div>
        <div class="close" @click="$emit('closeModal')" />
    </div>
</template>
<script>
export default {
    name: 'Modal',
    props: {
        item: {
            type: Object,
            required: true,
        },
    },
    data: () => ({
        
        photo: null,
        title: null,
        description: null,
        
    }),
    mounted() {
        this.photo = this.item.links[0].href;
        this.title = this.item.data[0].title;
        this.description = this.item.data[0].description.substring(0, 200);
    },
};
</script>
<style scoped>
    .outerWrapper {
        background: #f6f6f6;
        max-width: 100%;
        height: 100%;
        width: 100%;
        position: fixed;
        top: 0;
        left: 0;
    }
    @media (min-width: 1024px) {
        .outerWrapper {
            max-width: 70%;
            height: 60%;
            left: 0;
            right: 0;
            top: 0;
            bottom: 0;
            margin: auto;
            box-shadow: 0 30px 30px -10px rgba(0, 0, 0, .3);
        }
    }
    .close {
        position: absolute;
        width: 30px;
        height: 30px;
        padding: 30px;
        right: 0;
        top: 0;
        cursor: pointer;
    }
    .close::before, .close::after {
        position: absolute;
        top: 30px;
        right: 20px;
        content: '';
        width: 20px;
        height: 2px;
        background: black;
        display: block;
    }
    .close::before {
        transform: rotate(45deg);
    }
    .close::after {
        transform: rotate(-45deg);
    }
    .innerWrapper {
        display: flex;
        height: 100%;
        padding: 50px;
        justify-content: center;
        align-items: center;
        flex-direction: column;
    }
    @media (min-width: 1024px) {
        .innerWrapper {
            flex-direction: row;
        }
        .innerWrapper .photo {
            min-width: 50%;
            margin-right: 20px;
        }
    }
    .innerWrapper .photo {
        width: 100%;
        height: 100%;
        overflow: hidden;
        flex: 0 0 70%;
        background-position: center;
        background-repeat: no-repeat;
        background-size: cover;
    }
    .innerWrapper .photo img {
        width: 100%;
    }
    .innerWrapper .description {
        color: #333;
        flex: 0 0 30%;
    }
    .innerWrapper .title {
        color: #1e3d4a;
    }
 
</style>
