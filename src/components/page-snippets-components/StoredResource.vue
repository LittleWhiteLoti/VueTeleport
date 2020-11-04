<template>
  <ul>
    <LearningResource
      v-for="(rss) in Resources" 
      :key="rss.id"
      :id="rss.id"
      :title="rss.title"
      :description="rss.description"
      :link="rss.link"
      @delete="deleteResource"
    />
  </ul>
</template>

<script>

  import LearningResource from "./LearningResource.vue";
 
  export default {
    inject: ['addResource'],
    components:
    {
        LearningResource
    },
    data() {
        const storedResources = 
        [          {
            id: 'official-guide',
            title: 'Official Guide',
            description: 'The official Vue.js documentation',
            link: 'https://vuejs.org',
          },
          {
            id: 'google',
            title: 'Google',
            description: 'Learn to Google...',
            link: 'https://google.com',
          },
        ];

        return {
            Resources: storedResources
        }
    },
    methods: {
        deleteResource(id)
        {
            this.Resources.map((element, i) => {
                return (id == element.id) ? this.Resources.splice(i, 1) : ""
            })
        }
    }
  }
</script>

<style scoped>
  ul {
    list-style: none;
    margin: 0;
    padding: 0;
    margin: auto;
    max-width: 40rem;
  }
</style>
