<template>
  <div class="list w-11/12 md:w-4/5 grid mx-auto">
    <h1
      class="text-center md:text-3xl text-xl font-semibold md:my-14 mt-8 mb-14 text-jungle font-silka"
    >
      Lista de favoritos
    </h1>

    <div class="w-4/8 grid grid-cols-1 md:grid-cols-3 justify-items-center">
      <div
        v-for="item in list"
        :key="item.id"
        class="mx-auto max-w-18.25 w-full md:w-11/12 mb-14"
      >
        <div class="flex" v-if="item.real_estate.length == 0">
          <div
            v-for="real_estate in item.real_estate"
            :key="real_estate.id"
            v-bind:style="{
              'background-image':
                'url(' + require('../assets/images/not-found.svg') + ')'
            }"
            class="w-full h-48 bg-cover bg-center rounded-xl border border-white"
          ></div>
        </div>
        <div class="flex" v-if="item.real_estate.length == 1">
          <div
            v-for="real_estate in item.real_estate"
            :key="real_estate.id"
            v-bind:style="{
              'background-image': 'url(' + real_estate.image + ')'
            }"
            class="w-full h-48 bg-cover bg-center rounded-xl border border-white"
          ></div>
        </div>

        <div class="flex" v-if="item.real_estate.length == 2">
          <div
            v-for="(real_estate, index) in item.real_estate"
            :key="real_estate.id"
            v-bind:style="{
              'background-image': 'url(' + real_estate.image + ')'
            }"
            class="w-full h-48 bg-cover bg-center rounded-xl relative border border-white"
            v-bind:class="{
              'w-full z-20': index == 0,
              'w-5/4 -ml-1/4 z-10': index == 1
            }"
          ></div>
        </div>

        <div class="flex" v-if="item.real_estate.length == 3">
          <div
            v-for="(real_estate, index) in item.real_estate"
            :key="real_estate.id"
            v-bind:style="{
              'background-image': 'url(' + real_estate.image + ')'
            }"
            class="w-full h-48 bg-cover bg-center rounded-xl relative border border-white"
            v-bind:class="{
              'w-full z-30': index == 0,
              'w-full -ml-1/4 z-20': index == 1,
              'w-full -ml-3/10 z-10': index == 2
            }"
          >
            <div
              v-if="index == 2 && item.amount_real_estate - 2 > 0"
              class="bg-jungle bg-opacity-70 text-white w-full h-full flex justify-end items-center rounded-xl relative pr-15/100"
            >
              +{{ item.amount_real_estate - 2 }}
            </div>
          </div>
        </div>
        <div class="mt-5 mb-3 font-semibold text-jungle font-silka text-lg">
          {{ item.name }}
        </div>
        <div class="font-extralight text-jungle-gray text-sm">
          {{ item.amount_real_estate }} propiedades guardadas
        </div>
      </div>

      <div class="mx-auto max-w-18.25 w-full md:w-11/12 mb-14">
        <div class="flex">
          <div
            class="w-full h-48 rounded-xl flex justify-center items-center border border-white bg-md-blue text-6xl text-blue-sky"
          >
            +
          </div>
        </div>
        <div
          class="mt-5 mb-3 font-semibold text-jungle font-silka text-lg text-blue-sky text-center"
        >
          Crear una nueva lista
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import env from "../config/env";

export default {
  name: "List",
  data() {
    return {
      list: []
    };
  },
  created() {
    this.listRealEstate();
  },
  methods: {
    async listRealEstate() {
      axios
        .get(`${env.endpointAPI}`)
        .then(response => {
          const result = response.data;
          if (result.data && result.included) {
            const data = result.data;
            const included = result.included;
            this.list = data.map(element => {
              const realEstate = element.attributes.real_estate_ids;
              let newRealEstate = [];
              if (realEstate) {
                realEstate.map(property => {
                  included.filter(item => {
                    if (property == item.id && newRealEstate.length < 3) {
                      newRealEstate.push({
                        id: item.id,
                        image: item.attributes.gallery_urls[0]
                          ? item.attributes.gallery_urls[0]
                          : "../assets/images/not-found.svg"
                      });
                    }
                  });
                });
              }
              return {
                id: element.id,
                name: element.attributes.name,
                real_estate: newRealEstate,
                amount_real_estate: element.attributes.real_estate_ids.length
              };
            });
          }
        })
        .catch(() => {
          alert("Ha ocurrido un problema");
        });
    }
  }
};
</script>
