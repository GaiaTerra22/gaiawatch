<script setup>
import { ref } from 'vue'
import mostrarContenido from '../components/mostrarContenido.vue'

const contenido = ref([])

GET("/getLista").then(res => {
    contenido.value = res.contenido
})
</script>

<template>
    <article class="w-100 min-vh-100">
        <div class="content">
            <section class="beam-series-parent">
                <div class="container beam-series">
                    <div class="row">
                        <div class="col-12 text-white">
                            <div class="d-flex flex-column align-items-center gap-2 text-center">
                                <a href="/content"><img src="../components/img/generatedtext (2).png"
                                        class="img egiflex img-fluid" alt="egiflex"></a>
                                <p class="fs-2 fw-semibold fst-italic">
                                    Tu propia <span class="rounded p-1 fs-3 ">lista</span>
                                </p>
                            </div>
                        </div>
                    </div>
                    <mostrarContenido :contenido="contenido" :borrable="true" />
                </div>
            </section>
        </div>
    </article>
</template>

<style scoped>
.egiflex {
    transform: skew(-12deg);
    transform-origin: top;
}

a {
    text-decoration: none;
    color: white;
    font-weight: 600;
}

.dropdown-menu {
    text-align: start;
    background-color: rgba(0, 0, 0, .7);
    border: 0;
    backdrop-filter: blur(10px);
}

.dropdown-item:hover {
    background-color: transparent;
    color: white;
}

.search {
    background-color: transparent;
    backdrop-filter: blur(10px);
    font-weight: 600;
    color: white;
    border: 2px solid white;
}

.search:focus {
    box-shadow: none;
}

.search::placeholder {
    color: white;
}

button {
    color: white;

}

article {
    background-image: linear-gradient(to top, transparent, #730dd921), linear-gradient(to bottom, transparent, #730dd921), url('../components/img/1KgjKh5.png');
}

.content {
    backdrop-filter: blur(2px);
    min-height: 100vh;
}

.beam-series-parent {
    margin-bottom: 0rem;
}

.beam-series {
    padding-top: 6rem;
}

.beam-series p {
    word-wrap: normal;
}

.beam-series p span:first-child {
    background-color: #730DD9;
    font-weight: 700;
    text-transform: uppercase;
    white-space: nowrap;
}

@media screen and (max-width: 767px) {
    .equal-image {
        object-fit: cover;
        aspect-ratio: 0.5;
    }
}

.equal-image {
    object-fit: cover;
    aspect-ratio: 0.7;
}

figure {
    position: relative;
    transition: border 200ms ease-in-out;
}

figure:hover {
    border: 5px solid #730DD9;
}

figcaption {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    opacity: 0;
    transition: opacity 300ms ease;
}

.button-green-download2-big {
    background: #730DD9;
    border-radius: 3px;
    display: block;
    font-weight: 700;
    color: #fff;
    font-size: 16px;
    position: absolute;
    width: 130px;
    padding: 7px 0;
    margin: 0 auto;
    opacity: 0;
    z-index: 2;
    bottom: -30px;
    left: 50%;
    transform: translateX(-50%);
    transition: opacity 300ms ease, transform 300ms ease;
}

figure:hover figcaption,
figure:hover .button-green-download2-big {
    opacity: 1;
}

figure img {
    filter: blur(0);
    transition: all 300ms ease;
}

figure:hover img {
    filter: blur(2px);
}

figure span {
    position: absolute;
    bottom: 0;
    left: 50%;
    transform: translateX(-50%);
    opacity: 0;
    transition: opacity 300ms ease, transform 300ms ease;
}

figure:hover span {
    opacity: 1;
    transform: translate(-50%, -50%);
}
</style>