<template>
  <div>
    <ModalDialog
    ref="showDialog"
    :dataDetails="dataDetails"
    />
  <div v-if="data.length > 0">
    <div class="card mb-3 bg-card p-1" v-for="flag in data" :key="flag"
    @click="showModal(flag)"
    >
      <div class="row">
        <div class="col-md-3">
          <img
            :src="flag.flags.png"
            class="img-fluid rounded-start w-100 h-100"
            alt="..."
          />
        </div>
        <div class="col-md-9">
          <div class="card-body">
            <h5 class="card-title">{{ flag.name.official }}</h5>
            <ul>
              <li>{{ flag.cca2 }}</li>
              <li>{{ flag.cca3 }}</li>
              <li>{{ flag.name.nativeName }}</li>
              <li>{{ flag.altSpellings }}</li>
              <li class="p-0 m-0">
                <span>{{ flag.idd.root }}</span>
                <span v-for="item in flag.idd.suffixes" :key="item">
                  {{ item }}</span
                >
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div v-else>
    <h1 class="text-center">Not found.</h1>
  </div>
  </div>
</template>

<script>
import ModalDialog from "./ModalDialog.vue";
export default {
  props: ["data"],
  components: {
    ModalDialog,
  },
  data() {
    return {
      dataDetails: '',
    }
  },
  methods: {
    showModal(country){
      this.dataDetails = country;
      this.$refs.showDialog.openModalDialog();
    }
  },
};
</script>

<style scoped>
.bg-card {
  background: rgba(0, 0, 0, 0.1);
  transition: box-shadow 0.1s ease, transform 0.3s ease-in-out;
}
.bg-card:hover {
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.5);
  transform: scale(1.01);
}
</style>
