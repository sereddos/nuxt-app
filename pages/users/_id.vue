<template>
  <section>
    <h1>User page</h1>
    <hr>
    <p>Name: {{user.name}}</p>
    <p>Email: {{user.email}}</p>
    <p>Company: {{user.company.name}}</p>
  </section>
</template>

<script>
export default {
  validate({params}) {
    return /^\d+$/.test(params.id)
  },
  async asyncData({$axios, params}) {
    const user = await $axios.$get('https://jsonplaceholder.typicode.com/users/' + params.id)
    return {user}
  }
}
</script>