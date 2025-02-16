<script setup>
import Header from "@/components/Header.vue";
import Intro from "@/components/Intro.vue";
import Skill from "@/components/Skill.vue";
import Publishing from "@/components/Publishing.vue";
import ProjectList from "@/components/ProjectList.vue";
import Contact from "@/components/Contact.vue";
</script>

<template>
  <div>
    <Header />

    <main id="mainContent" role="main">
      <Intro />
      <Skill />
      <Publishing />
      <ProjectList />
      <Contact />
    </main>
  </div>
</template>