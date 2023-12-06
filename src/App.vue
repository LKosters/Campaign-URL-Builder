<script setup>
import Hero from './components/Hero.vue'
import Footer from './components/Footer.vue'
</script>

<template>
  <Hero />

  <div class="container custom-padding-regular">
    <div class="card p-10 flex flex-col lg:flex-row">
      <div class="w-full lg:w-1/2 lg:pr-10">
        <h2 class="text-2xl text-white font-bold">Enter details of campaign</h2>

        <div class="form-campaign pt-10">
          <div class="pb-5">
            <p class="text-white font-bold pb-2"><i style="color: #EC86FD;" class="fa-solid fa-link mr-2"></i> Website URL
            </p>
            <input class="w-full" v-model="websiteURL" placeholder="Type here" type="text" />
          </div>

          <div class="pb-5">
            <p class="text-white font-bold pb-2"><i style="color: #93E2FC;" class="fa-solid fa-hashtag mr-2"></i> Campaign
              ID</p>
            <input class="w-full" v-model="campaignID" placeholder="Type here" type="text" />
          </div>

          <div class="pb-5">
            <p class="text-white font-bold pb-2"><i style="color: #FFD863;" class="fa-solid fa-bookmark mr-2"></i>
              Campaign Source</p>
            <input class="w-full" v-model="campaignSource" placeholder="Type here" type="text" />
          </div>

          <div class="pb-5">
            <p class="text-white font-bold pb-2"><i style="color: #FC91AE;" class="fa-solid fa-globe mr-2"></i> Campaign
              Medium</p>
            <input class="w-full" v-model="campaignMedium" placeholder="Type here" type="text" />
          </div>

          <div class="pb-5">
            <p class="text-white font-bold pb-2"><i style="color: #AFFF55;" class="fa-solid fa-signature mr-2"></i>
              Campaign Name</p>
            <input class="w-full" v-model="campaignName" placeholder="Type here" type="text" />
          </div>
        </div>
      </div>

      <div class="w-full lg:w-1/2">
        <h2 class="text-2xl text-white font-bold">Share your URL</h2>

        <div class="form-campaign pt-10">
          <div>
            <p class="text-white font-bold mb-2">Campaign URL</p>
            <input class="w-full mb-5" v-model="campaignURL" type="text" readonly />
            <button class="btn" @click="copyURL">Copy URL</button>
          </div>
        </div>
      </div>
    </div>
  </div>

  <Footer />
</template>

<script>
export default {
  data() {
    return {
      websiteURL: '',
      campaignID: '',
      campaignSource: '',
      campaignMedium: '',
      campaignName: '',
      campaignURL: ''
    }
  },
  watch: {
    websiteURL() {
      this.updateCampaignURL();
    },
    campaignID() {
      this.updateCampaignURL();
    },
    campaignSource() {
      this.updateCampaignURL();
    },
    campaignMedium() {
      this.updateCampaignURL();
    },
    campaignName() {
      this.updateCampaignURL();
    }
  },
  methods: {
    updateCampaignURL() {
      let url = this.websiteURL;
      if (this.campaignSource) {
        url += '?utm_source=' + this.campaignSource;
      }
      if (this.campaignMedium) {
        url += '&utm_medium=' + this.campaignMedium;
      }
      if (this.campaignName) {
        url += '&utm_campaign=' + this.campaignName;
      }
      if (this.campaignID) {
        url += '&utm_term=' + this.campaignID;
      }
      this.campaignURL = url.replace(/ /g, '+');
    },
    copyURL() {
      navigator.clipboard.writeText(this.campaignURL);
      const button = document.querySelector('.btn');
      button.textContent = 'Copied';

      setTimeout(() => {
        button.textContent = 'Copy URL';
      }, 2000);
    }

  }
}
</script>                                                                                                                                                                      