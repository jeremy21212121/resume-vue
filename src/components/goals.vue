<template>
<section class="elevation-2 ma-1 goals">
    <span class="wrapper" @click.prevent="toggle">
        <span>
            <v-icon class="ma-1">check</v-icon>
            <h2 class="heading">Goals</h2>
        </span>
        <a href="#" class="icon-link" :class="{closed: !open}">
            <v-icon>keyboard_arrow_down</v-icon>
        </a>
    </span>
    <ol :class="{ closed: !open}">
        <li v-for="(goal,i) in goals" :key="i+1" :title="goal.title+' term'">
            <v-icon class="ma-1">{{goal.icon}}</v-icon>
            <p class="ma-1">{{goal.description}}</p>
        </li>
    </ol>
</section>
</template>
<script>
export default {
    name: "Goals",
    data: function() {
        return {
            open: false
        }
    },
    props: {
        goals: Array
    },
    methods: {
        toggle: function() {
            this.open = !this.open
        }
    }
}
</script>
<style scoped>
section {
    padding-bottom: 10px;
}
span {
    display: flex;
}
span.wrapper {
    justify-content: space-between;
}
h2 {
    margin: 10px;
}
a.icon-link {
    display: flex;
    text-decoration: none;
    justify-self: flex-end;
    margin: 10px;
    transition: 0.3s cubic-bezier(0.25, 0.8, 0.5, 1);
    transform: rotate(180deg);
}
a.icon-link.closed {
    transform: rotate(0deg);
}
ol {
    list-style-type: none;
    overflow: hidden;
    transition: all 0.5s ease-in-out;
    max-height: 50vh;
    opacity: 1;
}
ol.closed {
    max-height: 0px;
    opacity: 0;
}
li {
    display: flex;
}
p {
    margin: 0;
    /* line-height: 2; */
}
p::first-letter {
    text-transform: capitalize;
}
</style>
