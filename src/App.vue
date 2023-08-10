<template>
  <v-form>
      <v-text-field label="your name" v-model="content.name" />
      <v-text-field label="applicant ID" v-model="content.applicant" />
      <v-select label="Destination Country" :items="['Germany', 'Italy']" v-model="content.destination" />
      <v-select label="Appointment Type" :items="['Schengen', 'Legal', 'Study']" v-model="content.type" />
      <v-select label="City" :items="origin" v-model="content.city" />
      <v-select label="Payment Type" :items="['Paid by Card', 'Transfer']" v-model="content.payment" />
      <v-text-field label="Total Persons" v-model="content.nPerson" type="number" />
      <v-text-field label="Sheba Number" v-model="content.shebaNumber" />
      <v-text-field label="Sheba Name" v-model="content.shebaName" />
      <v-select label="Service Type" :items="['Only Normal', 'Normal or Prime']" v-model="content.serviceType" />
      <v-text-field label="Gap between booking and appointment date" v-model="content.gap" type="number" />

      <v-btn @click.prevent="downloadItem()">Download</v-btn>
  </v-form>
</template>

<script>

export default {
  name: 'App',
    methods: {
      downloadItem() {
          let filename = 'test.txt';
          let text = JSON.stringify(this.content);

          let element = document.createElement('a');
          element.setAttribute('href', 'data:text/json;charset=utf-8,' + encodeURIComponent(text));
          element.setAttribute('download', filename);

          element.style.display = 'none';
          document.body.appendChild(element);

          element.click();
          document.body.removeChild(element);
      }
    },
    data() {
      return {
          content: {
              name: "",
              applicant: "",
              destination: "",
              type: "",
              city: "",
              payment: "",
              nPerson: "",
              shebaNumber: "",
              shebaName: "",
              serviceType: "",
              gap: 0
          },
          origin: [
              'AHWAZ',
              'ARAK',
              'ARDEBIL',
               'BANDARABBAS',
               'BIRJAND',
               'BOJNORD',
               'BUSHEHR',
              'ESFEHAN',
               'GORGAN',
               'HAMEDAN',
               'ILAM',
               'KARAJ',
               'KERMAN',
               'KERMANSHAH',
               'KHORAMABAD',
              'MASHHAD',
               'QAZVIN',
               'QOM',
               'RASHT',
               'SANANDAJ',
               'SARI',
               'SEMNAN',
               'SHAHREKORD',
              'SHIRAZ',
              'TABRIZ',
              'TEHRAN',
              'URUMIEH',
               'YASUJ',
               'YAZD',
               'ZAHEDAN',
               'ZANJAN'
          ]
      }
    }
}
</script>

<style>
</style>
