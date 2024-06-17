<template>
  <ul>
    <li></li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'The Official Vue.js dodumentation.',
          link: 'https//vue.js.org',
        },
        {
          id: 'google',
          title: 'Google',
          description: 'Learn to google...',
          link: 'https//google.org',
        },
      ],
    };
  },
};
</script>
