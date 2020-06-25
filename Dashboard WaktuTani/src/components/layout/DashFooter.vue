<template>
  <footer class="main-footer">
    <strong>Copyright &copy; {{ year }}
    <a href="javascript:;">WAKTUTANI</a>.</strong> fargif991@gmail.com.
  </footer>
</template>

<script>
export default {
  name: 'DashFooter',
  data: function () {
    return {
      year: new Date().getFullYear()
    }
  }
}
</script>
