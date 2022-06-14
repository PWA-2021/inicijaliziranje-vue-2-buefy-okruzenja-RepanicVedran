<template>
    <div id="app">
        <nav class="navbar is-primary">
            <div class="container">
                <div class="navbar-brand">
                    <a class="navbar-item">
                        <h1 class="navbar-shoebox-title">SHOEBOX</h1>
                    </a>
                    <span class="navbar-burger" data-target="navbarMenuHeroA">
                        <span></span>
                        <span></span>
                        <span></span>
                    </span>
                </div>
                <div id="navbarMenuHeroA" class="navbar-menu">
                    <div class="navbar-end">
                        <a class="navbar-item" href="#"> Početna </a>
                        <a class="navbar-item" href="#kontakt"> Kontakt </a>
                    </div>
                </div>
            </div>
        </nav>

        <section class="hero is-link is-fullheight-with-navbar">
            <div class="hero-body">
                <p class="title">Svijet je manji nego ikad.</p>
            </div>
        </section>

        <section
            class="section is-small is-flex is-justify-content-space-around"
        >
            <div class="tile is-4 is-block mx-6">
                <a href="#dostavi">
                    <svg
                        class="mt-3"
                        style="width: 250px; height: 250px"
                        viewBox="0 0 24 24"
                    >
                        <path
                            fill="#7957D5"
                            d="M5,11L6.5,6.5H17.5L19,11M17.5,16A1.5,1.5 0 0,1 16,14.5A1.5,1.5 0 0,1 17.5,13A1.5,1.5 0 0,1 19,14.5A1.5,1.5 0 0,1 17.5,16M6.5,16A1.5,1.5 0 0,1 5,14.5A1.5,1.5 0 0,1 6.5,13A1.5,1.5 0 0,1 8,14.5A1.5,1.5 0 0,1 6.5,16M18.92,6C18.72,5.42 18.16,5 17.5,5H6.5C5.84,5 5.28,5.42 5.08,6L3,12V20A1,1 0 0,0 4,21H5A1,1 0 0,0 6,20V19H18V20A1,1 0 0,0 19,21H20A1,1 0 0,0 21,20V12L18.92,6Z"
                        />
                    </svg>
                    <h2>dostavi</h2>
                </a>
            </div>

            <div class="tile is-4 is-block mx-6">
                <a href="#posalji">
                    <svg
                        class="mt-3"
                        style="width: 250px; height: 250px"
                        viewBox="0 0 24 24"
                    >
                        <path
                            fill="#7957D5"
                            d="M21,16.5C21,16.88 20.79,17.21 20.47,17.38L12.57,21.82C12.41,21.94 12.21,22 12,22C11.79,22 11.59,21.94 11.43,21.82L3.53,17.38C3.21,17.21 3,16.88 3,16.5V7.5C3,7.12 3.21,6.79 3.53,6.62L11.43,2.18C11.59,2.06 11.79,2 12,2C12.21,2 12.41,2.06 12.57,2.18L20.47,6.62C20.79,6.79 21,7.12 21,7.5V16.5M12,4.15L10.11,5.22L16,8.61L17.96,7.5L12,4.15M6.04,7.5L12,10.85L13.96,9.75L8.08,6.35L6.04,7.5M5,15.91L11,19.29V12.58L5,9.21V15.91M19,15.91V9.21L13,12.58V19.29L19,15.91Z"
                        />
                    </svg>
                    <h2>pošalji</h2>
                </a>
            </div>
        </section>

        <h1 class="deliver-section-title" id="dostavi">Dostavi paket...</h1>

        <inputForm />

        <section class="is-medium section" id="posalji">
            <deliveryAd />
        </section>

        <footer id="kontakt">
            <p>
                Izradio: Vedran Repanić ~ Kolegij: Progresivne Web Aplikacije ~
                Kontakt: vrepanic@tvz.hr
            </p>
        </footer>
    </div>
</template>

<script>
import deliveryAd from "./components/deliveryAd.vue";
import inputForm from "./components/inputForm.vue";


export default {
    name: "App",
    components: {
        deliveryAd,
        inputForm
    },
};
</script>

<style>
.navbar-shoebox-title {
    font-weight: 800;
    font-size: 2rem;
}

.navbar-end {
    text-transform: uppercase;
    font-weight: 500;
}

.hero-body {
    background-image: linear-gradient(rgba(0, 0, 0, 0.65), rgba(0, 0, 0, 0)),
        url("https://www.elementfleet.com/binaries/content/gallery/elementfleet/hero/hero-1480x833-blurry-nighttime-street-min.jpg/hero-1480x833-blurry-nighttime-street-min.jpg/elementfleet%3Aherolarge");
    background-size: 100% 100%;
}

.title {
    color: rgba(255, 255, 255, 0.671) !important;
    font-family: Candara;
    font-size: 75px !important;
    padding: 20px;
    text-align: center;
    transform: translate(-50%, -50%);
    left: 50%;
    position: relative;
}

.tile {
    border: 5px solid #7957d5;
    border-radius: 1000px;
    text-align: center;
}

.tile:hover {
    box-shadow: 5px 5px 25px rgba(0, 0, 0, 0.9);
    transition: box-shadow 0.1s ease-in-out;
}

.tile h2 {
    margin: 0 auto;
    width: 150px;
    padding-bottom: 25px;
    text-transform: uppercase;
    font-size: 30px;
    font-weight: 700;
    color: #7957d5;
}

.deliver-section-title {
    font-size: 50px;
    text-align: center;
    padding: 25px 0px;
    color: white;
    background-color: #7957d5;
}

.deliver-section-title:hover {
    transition: color 1s ease-in-out;
    color: black;
    font-size: 75px;
    transition: font-size 0.5s ease-in-out;
}
.deliver-section {
    background-color: #7957d5;
}
.deliver-form {
    width: 40%;
    min-width: 400px;
    margin: 0 auto;
    background-color: #ab9dd3;
    padding: 20px 30px !important;
    border-radius: 15px;
}

footer {
    background-color: #7957d5;
    padding: 50px;
    width: 100%;
    position: absolute;
    bottom: 0px;
    text-align: center;
    font-size: 18px;
    color: white;
}

#app {
    position: relative;
}
</style>
