<template>
  <div>
    <h1>Jobs</h1>
    <div v-for="job in jobs" :key="job.id">
      <n-link :to="`jobs/${job.id}`">
        <b-card class="mb-2">
          <b-row>
            <b-col md="6">
              <p v-if="job.owner">{{job.owner.username}}</p>
              <h2>{{job.title}}</h2>
              <p>{{job.fulltime ? 'Full-time' : 'Part-time'}} / {{job.location}}</p>
              <b-badge v-if="job.category">{{job.category}}</b-badge>
            </b-col>
            <b-col
              md="6"
              class="d-flex justify-content-center align-items-center"
              style="border-right: 10px gold solid;"
            >{{job.created_at}}</b-col>
          </b-row>
        </b-card>
      </n-link>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios, env }) {
    return { jobs: await $axios.$get(`${env.API_URL}/jobs`) };
  }
};
</script>

<style scoped>
</style>