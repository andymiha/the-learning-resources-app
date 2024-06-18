<template>
  <li>
    <div>
      <header>
        <h3>{{ resource.title }}</h3>
        <button>Delete</button>
      </header>
      <p>{{ resource.description }}</p>
      <nav>
        <a :href="resource.link">View Resource</a>
      </nav>
    </div>
  </li>
</template>

<script>
export default {
  props: ['resource'],
  data() {
    return {};
  },
};
</script>
