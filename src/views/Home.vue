<template>
    <Transition name="grow-content">
        <div id="content" v-if="show">
            <PriceRow />
            <div id="skill-row">
                <h1>Specialties</h1>
                <div id="skills">
                    <Skill :isVisible="skillsVisible" direction="left" name="cSharp" />
                    <Skill :isVisible="skillsVisible" direction="left" delay="0.5" name="php" />
                    <Skill :isVisible="skillsVisible" direction="left" delay="1" name="mysql" />
                    <Skill :isVisible="skillsVisible" direction="right" delay="1" name="flutter" />
                    <Skill :isVisible="skillsVisible" direction="right" delay="0.5" name="vue" />
                    <Skill :isVisible="skillsVisible" direction="right" name="htmlcss" />
                </div>
            </div>
            <div id="project-row">
                <h1>Served</h1>
                <div id="projects">
                    <Project :isVisible="projectsVisible" direction="up" name="vehicult"
                        link="vehicult.nl/storelink.php" />
                    <Project :isVisible="projectsVisible" direction="up" style="transition-delay: 0.1s" name="vechtdal"
                        link="vechtdaltweewielers.nl" />
                </div>
            </div>
            <div id="contact">
                <h1>Contact</h1>
                <ContactForm />
            </div>
        </div>
    </Transition>
</template>
<script setup>

import PriceRow from '../components/prices.vue';
import Skill from '../components/skill.vue';
import Project from '../components/project.vue';
import ContactForm from '../components/contact-form.vue';
import { ref, onMounted, onUnmounted } from 'vue';

const skillsVisible = ref(false);
const projectsVisible = ref(false);
const skillsScrollPoint = 550;
const projectsScrollPoint = 1450;

const show = ref(false);

onMounted(() => {
    show.value = true;
});

onMounted(() => {
    window.addEventListener('scroll', handleScroll);
});

onUnmounted(() => {
    window.removeEventListener('scroll', handleScroll);
});

const handleScroll = () => {
    skillsVisible.value = window.scrollY >= skillsScrollPoint;
    projectsVisible.value = window.scrollY >= projectsScrollPoint;
};


</script>

<style scoped>
#content {
    /* position: absolute; */
    width: 100%;
    margin-top: 18vh;
    padding: 7vh 0 12vh 0;
    border-top-left-radius: 21%;
    border-top-right-radius: 21%;
    border-bottom-left-radius: 25%;
    border-bottom-right-radius: 25%;
    background-color: darkcyan;
}

.grow-content-enter-active {
    animation: growContent 2s ease;
}

@keyframes growContent {
    from {
    }

    to {
    }
}

h1 {
    text-align: center;
    margin: 8vh auto;
}

#skill-row,
#project-row {
    margin: 10vh auto;
}

#skills,
#projects {
    background-color: black;
    padding: 5vh 5% 5vh 5%;
    border-radius: 200px;
}


#price-row,
#skills,
#projects {
    display: flex;
    justify-content: space-between;
}

#projects {
    margin: 5vh auto;
}

#skill-row {
    margin-top: 24vh;
    width: 72.5%;

    #skills {
        display: flex;

    }
}

#project-row {
    margin-top: 24vh;
    width: 60%;
}
</style>