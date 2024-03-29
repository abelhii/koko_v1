<template>
  <div class="home">
    <header ref="header">
      <div class="content">
        <Scroll class="scroll-text" :scrollWord="scrollWord" />
        <p>
          <span data-tooltip="Koko">Wardah</span> is a designer focused on
          creating user-centric experiences and eye-catching user interfaces.
        </p>
        <DownArrow v-on:click="scrollTo('projects')" />
      </div>
    </header>
    <section ref="projects">
      <div class="content">
        <h1>PROJECTS</h1>
        <div class="projects">
          <div v-for="project in projects" :key="project.id">
            <ProjectCard :project="project" />
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Scroll from "@/components/Scroll.vue";
import DownArrow from "@/components/DownArrow.vue";
import ProjectCard from "@/components/Projects/ProjectCard.vue";
import { kokoStore, scrollMeTo } from "@/main";

export default defineComponent({
  name: "Home",
  components: {
    Scroll,
    DownArrow,
    ProjectCard,
  },
  data() {
    return {
      scrollWord: "DESIGN USER INTERFACE USER EXPERIENCE BRANDING",
      projects: kokoStore.store.projects,
    };
  },
  methods: {
    scrollTo(refName: string) {
      const element = this.$refs[refName] as HTMLElement;
      scrollMeTo(element);
    },
  },
});
</script>

<style lang="scss" scoped>
@import "../styles/_defaultVars.scss";

.home {
  display: grid;
  height: 100%;
  margin: auto;

  header {
    min-height: calc(100vh - 112px); // header height
    overflow: hidden;

    > .content {
      display: grid;
      place-items: center;
      height: 100%;

      p {
        text-align: left;
        font-size: 1.5rem;
        font-weight: 600;

        span {
          color: $dark-blue;
          cursor: pointer;
        }
      }

      :last-child {
        align-self: end;
        margin-bottom: 2rem;
      }
    }
  }

  section {
    padding: 4rem 0;
    min-height: 100vh;
    color: white;
    background-color: $black;

    .content {
      h1 {
        font-size: 2rem;
      }

      .projects {
        display: grid;
        gap: 4rem;
        grid-template-columns: 1fr;
      }
    }
  }
}


@media (min-width: 768px) {
  .home {
    section {
      .content {
        .projects {
          gap: 3rem;
          grid-template-columns: 1fr 1fr;
        }
      }
    }
  }
}

@media (min-width: 1024px) {
  .home {
    .content {
      padding: 0 6rem;
    }

    header > .content {
      p {
        font-size: 3rem;
      }
    }

    section {
      .content {
        h1 {
          font-size: 4rem;
        }

        .projects {
          gap: 4rem;
        }
      }
    }
  }
}
</style>
