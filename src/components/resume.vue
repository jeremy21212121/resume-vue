<template>
    <div>
        <blockquote class="blockquote">
            <!-- <span class="qu">"</span> -->
            {{resume.description}}
            <!-- <span class="qu">"</span> -->
        </blockquote>
        
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

blockquote {
    border-left: solid 4px rgba(0,0,0,0.54);
    margin-left: 4px;
}
</style>
