<template>
  <li>
    <base-card>
      <header>
        <h3>{{ resourceTitle }}</h3>
        <base-button mode = "flat" v-on:click = "deleteResource(resourceId)">Delete</base-button>
      </header>
      <p>{{ resourceDescription }}</p>
      <nav>
        <a v-bind:href="resourceLink">View Resource</a>
      </nav>
    </base-card>
  </li>
</template>

<script>

export default {
  props: {
    resourceTitle: {
      type: String,
      required: true
    },
    resourceDescription: {
      type: String,
      required: true
    },
    resourceLink: {
      type: String,
      required: true
    },
    resourceId: {
      type: String,
      required: true
    }
  },
  inject: ["deleteResource"]
};
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
