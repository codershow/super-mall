<template>
    <div class="recommends">
        <div v-for="(item,index) in recommends" :key="index" class="recommends-item">
            <a :href="item.link">
                <img :src="item.image" alt="">
            </a>
            <div>{{item.title}}</div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'HomeRecommendView',
    props: {
        recommends: {
            type: Array,
            default() {
                return []
            }
        }
    }
};
</script>

<style>
    .recommends {
        display: flex;
        text-align: center;
        font-size: 12px;
        padding: 10px 0 20px;
        border-bottom: 8px solid #eee;
    }

    .recommends .recommends-item {
        flex: 1;
    }

    .recommends-item img {
        width: 80%;
        margin-bottom: 5px;
    }
</style>