<template>
  <div>
    <TheHeader title="Remember Me" />
    <BaseCard>
      <BaseButton
        @click="selectTab('stored-resources')"
        :class="selectedTab == 'stored-resources' ? '' : 'flat'">
        Stored Resources
      </BaseButton>
      <BaseButton
        @click="selectTab('add-resource')"
        :class="selectedTab == 'add-resource' ? '' : 'flat'"
        @add="addResource"
      >
      Add Resource
      </BaseButton>
    </BaseCard>
    <keep-alive>
      <component :is="selectedTab"></component>
    </keep-alive>
  </div>
</template>

<script>

/* There is a more optimal and cleaner way to do imports but you haven't learned it yet */
import TheHeader from "./components/layout-components/TheHeader.vue";
import BaseCard from "./components/ui-components/BaseCard.vue";
import BaseButton from "./components/ui-components/BaseButton";

import StoredResources from "./components/page-snippets-components/StoredResource.vue";
import AddResource from "./components/page-snippets-components/AddResource.vue";

export default {
  name: 'App',
  components: {
    TheHeader,
    BaseCard,
    BaseButton,
    StoredResources,
    AddResource
  },
  data()
  {
    return {
      selectedTab: 'stored-resources',
    }
  },
  computed:
  {

  },
  provide()
  {
    return {
      addResource: this.addResource,
    }
  },
  methods: {
    selectTab(tab)
    {
      this.selectedTab = tab;
    },
    addResource(id, title, description, link)
    {
        this.Resources.shift({ id: id, title: title, description: description, link: link});
    }
  }
}
</script>

<style>
  /* Glboal styles */
  /* Should avoid imports from url, include imports in the webpack.cofig.js */
  /* Read about PostCSS from https://cli.vuejs.org/guide/css.html#postcss */
  @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

  * {
    box-sizing: border-box;
  }

  html {
    font-family: 'Roboto', sans-serif;
  }

  body {
    margin: 0;
  }

</style>
