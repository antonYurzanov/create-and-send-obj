<template lang='pug'>
    .container
        button(@click.prevent="sendObj" v-if="car.name") Отправить объект
        button(@click.prevent="createObj" v-else) Создать объект
</template>

<script>

    import axios from 'axios'

    const BASEURL = 'http://localhost:3000/posts/'

    export default {
        name: 'app',
        data() {
            return {
                car: ''
            }
        },
        methods: {
            createObj() {
                function Car(name, year, brand, color) {
                    this.name = name;
                    this.year = year;
                    this.brand = brand;
                    this.color = color;
                }

                this.car = new Car('focus', '2019', 'ford', 'black')
                console.log(this.car)
            },
            sendObj() {
                axios
                    .post(BASEURL, this.car)
                    .then((responce) => {
                            this.car = {};
                            console.log(responce)
                        }, (responce) => console.error(responce)
                    )
            }
        }
    }
</script>

<style lang="scss">
    html {
        height: 100%;
        padding: 0;
        margin: 0;
    }

    body {
        padding: 0;
        margin: 0;
        height: 100%;
        font: 14px Arial, Helvetica, sans-serif;
        color: #6e6e6e;
        background: #eeeeee;
    }

    a {
        color: #6e6e6e;
        text-decoration: underline;
        transition: all linear 0.2s;
    }

    a:hover {
        color: #6e6e6e;
        text-decoration: none;
    }

    p {
        padding: 0 0 30px 0;
        margin: 0;
    }

    p:last-of-type {
        padding-bottom: 0;
    }

    form, input, select, textarea {
        padding: 0;
        margin: 0;
        outline: medium none;
        resize: none;
    }

    textarea {
        overflow: hidden;
    }

    select, input[type='radio'], input[type='checkbox'], input[type='button'], input[type='submit'], label, button {
        cursor: pointer;
    }

    article, aside, details, figcaption, figure, footer, header, hgroup, main, menu, nav, section, summary {
        display: block;
    }

    audio, canvas, progress, video {
        display: inline-block;
        vertical-align: baseline;
    }

    .button {
        transition: all linear 0.2s;
    }

    table {
        border-spacing: 0;
        border-collapse: collapse;
    }

    td {
        padding: 0;
    }

    img {
        max-width: 100%;
        border: none;
    }

    h1, h2, h3, h4, h5, h6 {
        padding: 0;
        margin: 0 0 10px 0;
        font-weight: normal;
    }

    *:focus {
        outline: none;
    }

    h1 {
        font-size: 22px;
    }

    h2 {
        font-size: 20px;
    }

    h3 {
        font-size: 18px;
    }

    h4 {
        font-size: 16px;
    }

    h5 {
        font-size: 14px;
    }

    h6 {
        font-size: 12px;
    }

    .clear:after {
        display: block;
        content: '';
        clear: both;
    }

    .content {
        position: relative;
        max-width: 1170px;
        width: 100%;
        margin: 0 auto;
        box-sizing: border-box;
    }

    .container {
        max-width: 600px;
        width: 100%;
        margin: 0 auto;
        position: relative;
        min-height: 100%;
        height: auto !important;
        height: 100%;
        display: flex;
        flex-flow: column nowrap;
        justify-content: center;
        align-items: center;
        box-sizing: border-box;
        padding: 40px 0;
    }
</style>
