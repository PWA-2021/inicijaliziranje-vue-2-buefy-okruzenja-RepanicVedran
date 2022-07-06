<template>
    <section class="section is-medium deliver-section">
        <form @submit.prevent="addItem" class="deliver-form">
            <b-field label="Ime i prezime">
                <b-input value="" v-model="user"></b-input>
            </b-field>

            <b-field label="Kapacitet (dostupnih mjesta za kufer)">
                <b-slider
                    size="is-large"
                    :min="1"
                    :max="10"
                    ticks
                    v-model="capacity"
                >
                </b-slider>
            </b-field>

            <b-field grouped>
                <b-field label="Polazište" expanded>
                    <b-select placeholder="Odaberite" v-model="start" expanded>
                        <option value="Zagreb">Zagreb</option>
                        <option value="Split">Split</option>
                        <option value="Rijeka">Rijeka</option>
                        <option value="Osijek">Osijek</option>
                    </b-select>
                </b-field>
                <b-field label="Odredište" expanded>
                    <b-select placeholder="Odaberite" v-model="end" expanded>
                        <option value="Zagreb">Zagreb</option>
                        <option value="Split">Split</option>
                        <option value="Rijeka">Rijeka</option>
                        <option value="Osijek">Osijek</option>
                    </b-select>
                </b-field>
            </b-field>

            <b-field label="Napomena">
                <b-input v-model="msg" maxlength="30" type="textarea"></b-input>
            </b-field>

            <b-field label="Datum i vrijeme polaska">
                <b-datetimepicker
                    v-model="datetime"
                    rounded
                    placeholder="Odaberite..."
                    icon="calendar-today"
                    horizontal-time-picker
                >
                </b-datetimepicker>
            </b-field>

            <b-field label="Cijena">
                <b-numberinput
                    type="is-primary"
                    v-model="price"
                ></b-numberinput>
            </b-field>

            <b-field label="Link na sliku avatara">
                <b-input v-model="img"></b-input>
            </b-field>

            <b-button
                @click="addItem(), reloadPage()"
                type="is-primary"
                inverted
                outlined
                >Objavi</b-button
            >
            <b-button @click="resetData()" type="is-primary" inverted outlined
                >Očisti</b-button
            >
        </form>
    </section>
</template>

<script>
  import axios from 'axios';
  export default {
     name: "inputForm",
    data(){
        return {
                ads: [],
                id: "",
                start:"",
                end:"",
                user: "",
                capacity: "",
                price: "",
                datetime: "",
                msg: "",
                img: "",
            }
    },

    methods: {
         reloadPage() {
      setTimeout(() => {window.location.reload();},1500);
    },

         async addItem() {
            const res = await axios.post(`http://localhost:3000/ads`, 
                {
                    id: this.id,
                    start: this.start,
                    end: this.end,
                    user: this.user,
                    capacity: this.capacity,
                    price: this.price,
                    datetime: this.datetime,
                    msg: this.msg,
                    img: this.img,
                }).then((response) => {
                    console.log(response);
                });
    },

        resetData: function() {
            this.user = '';
            this.start = '';
            this.end = '';
            this.capacity = '';
            this.price = '';
            this.datetime = '';
            this.msg = '';
            this.img = '';
    }
    }
  };
</script>

<style scoped>
</style>