<style>
body,
* {
  font-family: MiriamLibre, system-ui
}
</style>
<template>
  <Header class="z-10"></Header>
  <main>
    <section class="hero-section">
      <Hero></Hero>
    </section>
    <div class="px-12">

      <ClientOnly fallback-tag="span" fallback="Loading comments...">
        <section class="carousel-section my-12 h-[205px]">
          <Carousel></Carousel>
        </section>
      </ClientOnly>
      <section class="ecosystem">
        <Ecosystem></Ecosystem>
      </section>
      <section class="Core mt-12">
        <CoreSection></CoreSection>
      </section>
      <section id="buidl" class="buidl mt-12">
        <BuidlSection></BuidlSection>
      </section>
    </div>
  </main>
</template>



