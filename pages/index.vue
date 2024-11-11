<template>
    <main>
        <NavBar class="nav-sans-vai"/>
        <Particules />
        <Intro />
        <div class="cards flex items-center justify-center px-14 ">
            <Cards />
        </div>
        <div class="slide">
            <PicturesSlide />
        </div>
    </main>
</template>


<style scoped>
@import url('https://fonts.cdnfonts.com/css/red-hat');


main{
    font-family: 'Red Hat Display', sans-serif;
}

.cards{
    margin-top: 11rem;
}

.slide {
    padding-top: 11rem;
}

</style>