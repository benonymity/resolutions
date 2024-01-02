<script setup>
import Resolutions from "./components/Resolutions.vue";
</script>

<template>
  <div class="grid-wrapper">
    <span class="copyright"
      >©{{ new Date().getFullYear() }} Benjamin Bassett</span
    >
    <span class="github"
      ><a href="https://github.com/benonymity/resolutions" target="_blank" data-umami-event="github">Github</a></span
    >
    <header>
      <a
        href="https://www.desiringgod.org/articles/the-resolutions-of-jonathan-edwards"
        target="_blank"
        style="text-decoration: none"
        data-umami-event="original"
      >
        <p class="title">
          <span class="real-title">The Resolutions of Johnathan Edwards</span>
        </p>
      </a>
    </header>
    <div class="wrapper">
      <div class="resolved">
        <p>Resolved:</p>
      </div>
      <Resolutions class="resolutions"/>
    </div>
  </div>
</template>

<style scoped>
header {
  display: grid;
  place-items: center;
  padding-top: 2%;
  font-size: 2.5rem; /* Increased font size for impact */
  margin: 0 auto;
  color: #333; /* Darker color for better readability */
}

.title {
  min-height: 128px;
  display: table;
  text-align: center;
  margin: 20px;
  margin-top: 0px;
  border: 2px solid #4a4a4a; /* Subtler border */
  border-radius: 10px;
  background-color: #f0f0f0; /* Light background for contrast */
  background-position: 50% 55%;
  background-image: url(https://dg.imgix.net/the-resolutions-of-jonathan-edwards-me4czyke-en/landscape/the-resolutions-of-jonathan-edwards-me4czyke.jpg?ts=1481913253&ixlib=rails-4.3.1&auto=format%2Ccompress&fit=min&w=350&h=197&dpr=2&ch=Width%2CDPR);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1); /* Soft box-shadow for depth */
  color: black;
}

.real-title {
  padding: 10px 20px;
  padding-top: 0px;
  margin: 20px;
  text-align: center;
  display: table-cell;
  vertical-align: middle;
}
.wrapper {
  display: grid;
  align-content: center;
  align-items: center;
  overflow: hidden;
}
a {
  color: inherit;
}

.copyright {
  padding-top: 10px;
  text-align: center;
  color: gray;
  font-family: sans-serif;
  font-size: 10px;
  line-height: 10px;
}
.github {
  text-align: center;
  color: gray;
  font-family: sans-serif;
  font-size: 10px;
  line-height: 14px;
}
.grid-wrapper {
  height: 100%;
  display: grid;
  align-content: center;
  align-items: center;
  overflow: hidden;
  background-color: #fafafa;
}

.resolved {
  grid-column-start: 1;
  margin-left: 20px;
  margin-right: 10px;
  font-size: 40px;
}

.resolutions {
  max-height: 85vh;
  grid-column-start: 2;
  margin-top: 10px;
  overflow-y: scroll;
  scrollbar-width: none;
}

.resolutions::-webkit-scrollbar {
  display: none;
}

@media screen and (max-width: 700px) {
  .wrapper {
    align-content: center;
    align-items: center;
    grid-template-columns: 1fr; /* Sets the layout to a single column */
  }
  .resolved {
    text-align: center;
  }
  .resolved,
  .resolutions {
    grid-column-start: auto; /* Resets the column start to default for small screens */
  }
}
</style>
