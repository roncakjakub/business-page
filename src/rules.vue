<template>
  <div id="transportation-regulations">
    <section class="container-lg container-style justify-between items-center flex flex-row gap-5 py-24">
      <div>
        <img src="./assets/images/Ornament.svg" alt="ornament"/>
        <h3 class="heading-style">Prepravný poriadok</h3>
        <p>Ak by ste nenašli odpovede na Vaše otázky v tomto súbore, neváhajte nás kontaktovať.</p>
      </div>
      <a href="./prepravnyPoriadok.pdf" download="prepravnyPoriadok.pdf" class="border-solid border-black border-2 py-2 px-12">
        <span class="text-sm heading-color">Stiahnuť súbor</span>
      </a>
    </section>
  </div>
</template>

<script>
export default {
  name: 'TransportationRegulations',
  methods: {
    downloadItem (url) {
      Axios.get(url, { responseType: 'blob' })
          .then(response => {
            const blob = new Blob([response.data], { type: 'application/pdf' })
            const link = document.createElement('a')
            link.href = URL.createObjectURL(blob)
            link.download = label
            link.click()
            URL.revokeObjectURL(link.href)
          }).catch(console.error)
    }
  }
}
</script>

<style scoped>
/* Your CSS from style.css can go here, or you can link to your external CSS file */
</style>
