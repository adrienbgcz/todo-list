<template>
  <div class="all">
    <header class="header">
        <slot name="header" :app-name="appName"></slot>
    </header>

    <main class="main">
        <slot></slot>
    </main>

    <footer class="footer">
        <slot name="footer" :mail="mail"></slot>
    </footer>
  </div>
</template>

<script>
export default {
    name: "Layout",
    data: function () {
        return {
            appName: "TodoList",
            mail: "test@test.fr"
        }
    }
}


</script>


<style scoped>

.header {
    display: flex;
    justify-content: center;
    height : 100px;
}

.main {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-bottom: 200px;
}

.footer {
    display: flex;
    justify-content: center;
}



</style>