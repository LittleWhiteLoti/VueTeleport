<template>
  <li>
    <BaseCard>
      <div>
        <header>
          <h3>{{ title }}</h3>
          <BaseButton mode="flat" @click="deleteResource">
            <template v-slot:default>
              Delete
            </template>
          </BaseButton>
        </header>
        <p>{{ description }}</p>
        <a v-bind:href="link">Link</a>
      </div>
    </BaseCard>
  </li>
</template>

<script>
  import BaseCard from "./../ui-components/BaseCard.vue";
  import BaseButton from "./../ui-components/BaseButton.vue";

  export default {
    components: {
      BaseCard,
      BaseButton,
    },
    props: {
      id: {
        type: String,
        required: true,
      },
      title: {
        type: String,
        required: true,
      },
      description: {
        type: String,
        required: true,
      },
      link: {
        type: String,
        required: true,
      },
    },
    data() {
        return {
        }
    },
    methods: {
        deleteResource()
        {
            this.$emit('delete', this.$props.id);
        }
    }
  }
</script>

<style scoped>
  li {
    margin: auto;
    max-width: 40rem;
  }

  header {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  h3 {
    font-size: 1.25rem;
    margin: 0.5rem 0;
  }

  p {
    margin: 0.5rem 0;
  }

  a {
    text-decoration: none;
    color: #ce5c00;
  }

  a:hover,
  a:active {
    color: #c89300;
  }
</style>
