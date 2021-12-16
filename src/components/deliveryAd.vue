<template>
    <div class="deliveryAd">
        <div class="ad-search">
            <input
                type="text"
                v-model="search"
                placeholder="Pretraga po imenu vozača(case-insensitive)"
            />
            <br />
            <label> Polazak: </label>
            <select v-model="filterStart">
                <option value=""></option>
                <option value="Zagreb">Zagreb</option>
                <option value="Split">Split</option>
                <option value="Rijeka">Rijeka</option>
                <option value="Osijek">Osijek</option>
            </select>

            <label> Odredište: </label>
            <select v-model="filterEnd">
                <option value=""></option>
                <option value="Zagreb">Zagreb</option>
                <option value="Split">Split</option>
                <option value="Rijeka">Rijeka</option>
                <option value="Osijek">Osijek</option>
            </select>
        </div>

        <div class="deliveryAd-mainWrap" v-for="ad of filteredAds" :key="ad.id">
            <figure class="image is-128x128">
                <img class="is-rounded" v-bind:src="ad.img" />
            </figure>

            <div class="deliveryAd-contentWrap">
                <div class="deliveryAd-courierDest">
                    <p class="courierStart">{{ ad.start }}</p>
                    <p>&nbsp;-&nbsp;</p>
                    <p class="courierEnd">{{ ad.end }}</p>
                </div>

                <div class="deliveryAd-courierInfo">
                    <p>
                        <em>{{ ad.user }}</em>
                    </p>
                    <p>
                        <strong>{{ ad.price }} kn</strong>
                    </p>
                    <p><strong>Polazak:</strong> {{ ad.datetime }}</p>
                    <p><strong>Kapacitet:</strong> {{ ad.capacity }} %</p>
                    <p><strong>Napomena:</strong> {{ ad.msg }}</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from "axios";

export default {
  name: "deliveryAd",
  data() {
    return {
      ads: [],
      search: '',
      filterStart: '',
      filterEnd: ''
    }
  },

    computed: {
      filteredAds: function(){
          return this.ads.filter((ad) => {
              return ad.user.match(new RegExp(this.search, "i")) &&  ad.start.match(this.filterStart) && ad.end.match(this.filterEnd)
          });
      }
  },

  async created() {
    try {
      const res = await axios.get(`http://localhost:3000/ads`);

      this.ads = res.data;
    } catch (e) {
      console.error(e);
    }
  }
};

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.deliveryAd-mainWrap {
    border: 2px solid #7957d5;
    border-radius: 50px;
    box-shadow: 3px 3px 10px;
    overflow: hidden;
    width: 40%;
    min-width: 500px;
    margin: 0 auto 50px auto;
    display: flex;
    align-items: center;
    justify-content: flex-start;
}

.deliveryAd-mainWrap:hover {
    box-shadow: 10px 10px 15px;
    animation: box-shadow 1.5s ease-in-out;
    width: 41%;
    -webkit-transition: width 0.5s ease-in-out;
}

.image {
    margin: 35px;
    border: 2px solid #7857d58f;
    border-radius: 100px;
    box-shadow: 1px 1px 5px 1px #6040b8af;
}

.deliveryAd-contentWrap {
    margin: 30px 0;
}

.deliveryAd-courierDest {
    font-family: Arial;
    font-size: 30px;
    font-weight: bold;
    display: flex;
}

.deliveryAd-courierInfo {
    margin-left: 25px;
    font-size: 18px;
    font-family: Arial;
    line-height: 1.2;
}

.ad-search input {
    width: 300px;
    text-align: center;
    margin-bottom: 20px;
}

.ad-search select {
    width: 25%;
    margin-bottom: 20px;
}

.ad-search {
    width: 900px;
    margin: 0 auto;
    text-align: center;
}
</style>
