<template>
    <div>
        <Goals
            :goals="resume.goals"
        />
        <sbSection 
            v-for="(section,i) in this.resume.sections"
            :key="i+1"
            :section="section"
            :openSection="openSection"
            @sectionClick="handleSectionClick"
        />

    </div>
</template>

<script>
import Goals from '../components/goals'
import sbSection from '../components/sbSection'
const resumeData = require("../resume.json")

export default {
    name: "Resume",
    data: function() {
        return {
            resume: resumeData,
            openSection: 0
        }
    },
    components: {
        Goals,
        sbSection
    },
    methods: {
        handleSectionClick: function(key) {
            if (this.openSection === key) { this.openSection = 0 }
            else { this.openSection = key }
        }

    }

}
</script>

<style>

/* .skillbox {
 
    width: 100%;
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
}
.skillbox *::first-letter {
    text-transform: capitalize;
}
.skillbox h3 {
    justify-self: center;
}
span.heading-wrapper {
    display: flex;
    justify-content: space-between;
}
span.heading-wrapper i {
    justify-self: flex-end;
} */
</style>
