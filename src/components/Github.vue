<template>
  <div>
    <div id="githubBody" class="hidden"></div>
    <div id="commitGraph"></div>
  </div>
</template>

<script>
export default {
  mounted() {
    this.getGithub();
  },
  methods: {
    getGithub: async () => {
      const proxyurl = "https://cors-anywhere.herokuapp.com/";
      const url = "https://github.com/13akstjq"; // site that doesn’t send Access-Control-*
      const result = await fetch(proxyurl + url) // https://cors-anywhere.herokuapp.com/https://example.com
        .then(response => response.text())
        .catch(() =>
          console.log("Can’t access " + url + " response. Blocked by browser?")
        );
      const Body = document.querySelector("#githubBody");
      const commitGraph = document.querySelector("#commitGraph");
      Body.innerHTML = result;
      const GraphHTML = Body.getElementsByClassName(
        "border border-gray-dark py-2 graph-before-activity-overview"
      )[0].innerHTML;
      // Body.innerHTML = CommitGraph;
      commitGraph.innerHTML = GraphHTML;
    }
  }
};
</script>

<style>
.hidden {
  display: none;
}
</style>
