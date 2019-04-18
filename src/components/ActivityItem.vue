<template>
  <article class="post">
    <h4>{{ activity.title }}</h4>
    <div class="media">
      <div class="media-left">
        <p class="image is-32x32">
          <img src="./../assets/user.png">
        </p>
      </div>
      <div class="media-content">
        <div class="content">
          <p>
            <a href="#">Filip Jerga</a> updated {{ activity.updatedAt }} ago &nbsp;
          </p>
        </div>
      </div>

      <div class="media-right">
        <span>Progress Bar Here</span>
      </div>
    </div>
  </article>
</template>

<script>
export default {
  name: 'ActivityItem',
  // props: ['activity']
  props: {
    activity: {
      type: Object,
      require: true
    }
  }
}
</script>

<style scoped></style>
