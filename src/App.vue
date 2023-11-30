<template>
  <div class="custom-padding-regular">
    <h1 class="text-5xl text-white font-bold text-center">
      Campaign URL Builder
    </h1>
  </div>

  <div class="container custom-padding-regular">
    <div class="card p-10 flex flex-col lg:flex-row">
      <div class="w-full lg:w-1/2 lg:pr-10">
        <h2 class="text-2xl text-white font-bold">Enter details of campaign</h2>

        <div class="form-campaign pt-10">
          <div class="pb-5">
            <p class="text-white font-bold pb-2">Website URL</p>
            <input class="w-full" v-model="websiteURL" placeholder="Type here" type="text" />
          </div>

          <div class="pb-5">
            <p class="text-white font-bold pb-2">Campaign ID</p>
            <input class="w-full" v-model="campaignID" placeholder="Type here" type="text" />
          </div>

          <div class="pb-5">
            <p class="text-white font-bold pb-2">Campaign Source</p>
            <input class="w-full" v-model="campaignSource" placeholder="Type here" type="text" />
          </div>

          <div class="pb-5">
            <p class="text-white font-bold pb-2">Campaign Medium</p>
            <input class="w-full" v-model="campaignMedium" placeholder="Type here" type="text" />
          </div>

          <div class="pb-5">
            <p class="text-white font-bold pb-2">Campaign Name</p>
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
            <button class="btn">Copy URL</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      websiteURL: '',
      campaignURL: ''
    }
  },
  watch: {
    websiteURL(campaignURL) {
      this.campaignURL = campaignURL;
    }
  }
}
</script>
