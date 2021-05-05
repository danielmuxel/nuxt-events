<template>
  <div>
    <h1>Events</h1>
  </div>
</template>

<script>
export default {
  asyncData({ $axios, error }) {
    return $axios
      .get('http://localhost:3000/events')
      .then((response) => {
        return { events: response.data }
      })
      .catch((e) => {
        error({
          statusCode: 503,
          message: 'Unable to fetch events as this time. Please try again',
        })
      })
  },
  head() {
    return {
      title: 'Event Listing',
    }
  },
}
</script>
