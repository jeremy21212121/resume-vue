<template>
            <div 
                class="skillbox elevation-0 ma-1 pa-2"
                :class="{ skillActive: open, skillInactive: !open }"
                @click.prevent="emitEvent"
            >
                <span class="heading-wrapper">
                    <span class="heading-icon-wrapper">
                        <v-icon
                            v-if="skill.icon"
                        >
                        {{skill.icon}}
                        </v-icon>
                        <i
                            v-else-if="skill.svgIcon"
                            v-html="skill.svgIcon"
                            class="v-icon svg-icon"
                        >
                        </i>
                        <h3 class="heading pa-1">{{skill.title}}</h3>
                    </span>
                    <a 
                        href="#"
                        :aria-expanded="open"
                        aria-label="read more"
                    >
                        <v-icon xs>keyboard_arrow_down</v-icon>
                    </a>
                </span>
                <p 
                    class="description pa-1"
                    :aria-hidden="!open"
                >
                {{skill.description}}
                </p>
                <v-divider />
            </div>
            
    
</template>


<script>
export default {
    name: "Skillbox",
    props: {
        skill: Object,
        open: Boolean
    },
    data: function() {
        return {
            // isSkillActive: false
        }
    },
    methods: {
        emitEvent: function() {
            const eventName = (this.open ? "sbClose" : "sbOpen");
            const payload = this.$vnode.key;
            this.$emit(eventName, payload);
        }
        // toggle: function() {
        //     this.isSkillActive = !this.isSkillActive;

        //     const eventName = "skillbox" + ( this.isSkillActive ? "Open" : "Close" );
        //     this.$emit(eventName, this.$vnode.key)
        // },
        // disable: function() {
        //     this.isSkillActive = false;
        // }
    }
}
</script>

<style scoped>
.skillbox {
    transition: all 0.5s linear;
    min-width: 100%;
    max-width: 100%;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
}
.skillbox:last-of-type hr {
    display: none;
}
.skillbox a i {
    transform: rotate(0deg);
}
.skillbox *::first-letter {
    text-transform: capitalize;
}
/* .skillbox h3 {
    justify-self: center;
} */
span.heading-wrapper {
    display: flex;
    justify-content: space-between;
}
/* span.heading-wrapper i {
    justify-self: flex-end;
} */
.heading-wrapper a {
    text-decoration: none;
    margin-right: 10px;
}
.heading-icon-wrapper {
    display: flex;
    /* flex-direction: row-reverse; */
    flex-grow: 1;
    /* justify-content: flex-start; */
}
.heading-icon-wrapper i {
    margin-right: 20px;
    margin-left: 5px;
}
i.svg-icon {
    width: 24px;
    height: 24px;
}
p.description {
    /* display: none; */
    margin: 0;
    opacity: 0;
    max-height: 0px;
    transition: all 0.5s ease-in-out;
    
}

/* .skillbox.skillActive {
    min-width: 100%;
    max-width: 100%;
} */
.skillbox.skillActive a i {
    transform: rotate(180deg);
}
.skillbox.skillActive p.description {
    /* display: block; */
    margin: 8px 4px 8px 44px;
    opacity: 1;
    max-height: 200px;
}

.skillbox.skillInactive {
    justify-content: flex-start;
}
</style>

<style>
/* unscoped styles for v-html rendered elements*/
i.svg-icon svg {
    max-height: 24px;
}
</style>
