<template>
  <p>Hello {{ name }} how are you?</p>
</template>

<script>
export default {
  name: 'Hello',
  props: {
    name: String('John')
  }
}

</script>
