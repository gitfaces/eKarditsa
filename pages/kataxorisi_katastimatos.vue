<template>
  <main
    class="flex flex-col flex-wrap mx-auto my-auto justify-center content-center items-center"
  >
    <h1
      class="text-main text-4xl font-bold my-10 w-full flex justify-center content-center items-center"
    >
      Καταχώρηση της επιχείρησης σας !
    </h1>

    <div
      class="flex justify-center content-center items-center bg-gray-200 mb-20"
    >
      <form
        @submit.prevent="(_) => {}"
        class="flex flex-wrap mx-10 justify-center items-start rounded-sm"
      >
        <div class="flex flex-col m-4">
          <p class="text-lg text-main">
            Θα χρειαστούμε τα στοιχεία επικοινωνίας σας
          </p>
          <input
            type="text"
            name="full_name"
            placeholder="Ονοματεπώνυμο *"
            class="rounded-sm mb-2 py-2 px-2 w-[500px] border border-transparent"
            v-model="newEntryInfo.full_name"
            :class="{
              '!border-red-400': errors.includes('full_name'),
            }"
          />
          <span
            v-show="errors.includes('full_name')"
            class="text-red-400 text-sm"
            >Υποχρεωτικό πεδίο</span
          >
          <input
            type="tel"
            name="phone"
            placeholder="Τηλέφωνο επικοινωνίας *"
            class="rounded-sm my-2 py-2 px-2 w-[500px] border border-transparent"
            v-model="newEntryInfo.phone"
            :class="{
              '!border-red-400': errors.includes('phone'),
            }"
          />
          <span v-show="errors.includes('phone')" class="text-red-400 text-sm"
            >Υποχρεωτικό πεδίο</span
          >
          <input
            type="email"
            name="email"
            placeholder="Email επικοινωνίας*"
            class="rounded-sm my-2 py-2 px-2 w-[500px] border border-transparent"
            v-model="newEntryInfo.email"
            :class="{
              '!border-red-400': errors.includes('email'),
            }"
          />
          <span v-show="errors.includes('email')" class="text-red-400 text-sm"
            >Υποχρεωτικό πεδίο</span
          >
          <p class="text-lg text-main py-5 mt-10">
            Ανεβάστε φωτογραφία με το logo της επιχείρησης σας
          </p>
          <input
            type="file"
            id="img"
            name="img"
            accept="image/*"
          />
          <span v-show="errors.includes('logo')" class="text-red-400 text-sm"
            >Υποχρεωτικό πεδίο</span
          >
          <!--<p class="text-lg text-main py-5 mt-10">
            Ανεβάστε 1-3 φωτογραφίες του χώρου της επιχειρήσεις σας
          </p>
           <label for="files"></label>
          <input
            type="file"
            @change="fileHandleKati"
            id="files"
            name="files"
            multiple 
          />
          -->
          <br /><br />
          <select
            v-model="newEntryInfo.category"
            class="p-2"
            :class="{
              '!border-red-400': errors.includes('category'),
            }"
          >
            <option value="">Κατηγορία καταστήματος</option>
            <option value="ΕΣΤΙΑΣΗ">ΕΣΤΙΑΣΗ</option>
            <option value="ΥΠΗΡΕΣΙΕΣ">ΥΠΗΡΕΣΙΕΣ</option>
            <option value="ΚΑΤΑΣΤΗΜΑΤΑ">ΚΑΤΑΣΤΗΜΑΤΑ</option>
            <option value="ΥΓΕΙΑ">ΥΓΕΙΑ</option>
            <option value="ΔΙΑΜΟΝΗ">ΔΙΑΜΟΝΗ</option>
          </select>
          <span
            v-show="errors.includes('category')"
            class="text-red-400 text-sm"
            >Υποχρεωτικό πεδίο</span
          >
        </div>
        <div class="flex flex-col m-4">
          <p class="text-lg text-main">Τα στοιχεία της επιχείρησης σας</p>
          <input
            type="text"
            name="company"
            placeholder="Επωνυμία *"
            class="rounded-sm mb-2 py-2 px-2 w-[500px] border border-transparent"
            v-model="newEntryInfo.company"
            :class="{
              '!border-red-400': errors.includes('company'),
            }"
          />
          <span v-show="errors.includes('company')" class="text-red-400 text-sm"
            >Υποχρεωτικό πεδίο</span
          >
          <input
            type="text"
            name="activity"
            placeholder="Επάγγελμα *"
            class="rounded-sm my-2 py-2 px-2 w-[500px] border border-transparent"
            v-model="newEntryInfo.activity"
            :class="{
              '!border-red-400': errors.includes('activity'),
            }"
          />
          <span
            v-show="errors.includes('activity')"
            class="text-red-400 text-sm"
            >Υποχρεωτικό πεδίο</span
          >
          <input
            type="text"
            name="site"
            placeholder="Ιστοσελίδα"
            class="rounded-sm my-2 py-2 px-2 w-[500px] border border-transparent"
            v-model="newEntryInfo.site"
          />
          <input
            type="tel"
            name="store_phone"
            placeholder="Τηλέφωνο καταστήματος *"
            class="rounded-sm my-2 py-2 px-2 w-[500px] border border-transparent"
            v-model="newEntryInfo.store_phone"
            :class="{
              '!border-red-400': errors.includes('store_phone'),
            }"
          />
          <span
            v-show="errors.includes('store_phone')"
            class="text-red-400 text-sm"
            >Υποχρεωτικό πεδίο</span
          >
          <input
            type="email"
            name="store_email"
            placeholder="Email καταστήματος*"
            class="rounded-sm my-2 py-2 px-2 w-[500px] border border-transparent"
            v-model="newEntryInfo.store_email"
            :class="{
              '!border-red-400': errors.includes('store_email'),
            }"
          />
          <span
            v-show="errors.includes('store_email')"
            class="text-red-400 text-sm"
            >Υποχρεωτικό πεδίο</span
          >
          <input
            type="text"
            name="store_address"
            placeholder="Διεύθυνση καταστήματος *"
            class="rounded-sm my-2 py-2 px-2 w-[500px] border border-transparent"
            v-model="newEntryInfo.store_address"
            :class="{
              '!border-red-400': errors.includes('store_address'),
            }"
          />
          <span
            v-show="errors.includes('store_address')"
            class="text-red-400 text-sm"
            >Υποχρεωτικό πεδίο</span
          >
          <input
            type="text"
            name="city_code"
            placeholder="Ταχ. κώδικας *"
            class="rounded-sm my-2 py-2 px-2 w-[500px] border border-transparent"
            v-model="newEntryInfo.city_code"
            :class="{
              '!border-red-400': errors.includes('city_code'),
            }"
          />
          <span
            v-show="errors.includes('city_code')"
            class="text-red-400 text-sm"
            >Υποχρεωτικό πεδίο</span
          >
          <textarea
            class="rounded-sm my-2 py-2 px-2 w-[500px] border border-transparent"
            name="store_description"
            id="store_description"
            cols="30"
            rows="5"
            placeholder="Περιγραφή της επιχείρησης, συστήνεται από 300 έως 1000 λέξεις *"
            v-model="newEntryInfo.store_description"
            :class="{
              '!border-red-400': errors.includes('store_description'),
            }"
          ></textarea>
          <span
            v-show="errors.includes('store_description')"
            class="text-red-400 text-sm"
            >Υποχρεωτικό πεδίο</span
          >

          <input
            type="submit"
            value="Αποστολή στοιχείων"
            class="bg-main text-white text-lg my-5 px-4 py-2 rounded-sm hover:text-secondary"
            @click="saveNewEntry()"
          />
          <span class="text-gray-500 text-sm p-0"
            >Τα στοιχεία με * είναι υποχρεωτικά.</span
          >
        </div>
      </form>
    </div>
  </main>
</template>

<script>
import Vue from "vue";
import VueSweetalert2 from "vue-sweetalert2";
import "sweetalert2/dist/sweetalert2.min.css";

export default {
  data() {
    return {
      newEntryInfo: {
        full_name: "eleni",
        phone: "6944355958",
        email: "elenitselioy15@gmail.com",
        company: "Walmart",
        activity: "store",
        site: "www.walmart.com",
        store_phone: "2100000000",
        store_email: "hello@walmart.com",
        store_address: "Sacramento",
        city_code: "95829",
        store_description: "Shop Walmart.com today for Every Day Low Prices. Join Walmart+ for unlimited free delivery from your store & free shipping with no order minimum.",
        category: "ΚΑΤΑΣΤΗΜΑΤΑ",
      },
      errors: [],
    };
  },
  methods: {
    initNewEntry() {
      this.newEntryInfo = {
        full_name: "",
        phone: "",
        email: "",
        company: "",
        activity: "",
        site: "",
        store_phone: "",
        store_email: "",
        store_address: "",
        city_code: "",
        store_description: "",
        category: "",
      };
    },
    fileHandleKati(e) {
      console.log(e);
      if (e.target.files) {
        this.upload(e.target.files);
      }
    },
    async saveNewEntry() {
      if (!this.objectCheck(this.newEntryInfo)) {
        return;
      }

      let fileinput=document.querySelector("#img")
      if(fileinput.files){
        let f = await this.upload(fileinput.files);
        if(!f){
          return;
        }
        else{
          this.newEntryInfo.logo=f;
        }
      }
      try {
        let payload = this.newEntryInfo;
        let response = await this.$axios.post(
          "https://api.ekarditsa.gr/",
          payload
        );
        
        this.initNewEntry();
        this.$swal.fire(
          "Επιτυχής αποστολή!",
          "Θα ενημερωθείτε σύντομα στο email επικοινωνίας που καταχωρήσατε, για την εξέλιξη του αιτήματος σας! ",
          "success"
        );
      } catch (error) {
        this.$swal.fire({
          icon: "error",
          title: "Ωχ...",
          text: "Κάτι πήγε στραβά, δοκίμασε ξανά αλλιώς επικοινώνησε μαζί μας!",
        });
      }
    },
    objectCheck(obj) {
      let errors = [];
      let keysOfObj = Object.keys(obj);
      console.log(keysOfObj);
      let valid = true;
      for (let key of keysOfObj) {
        if (!this.newEntryInfo[key] && key != "site") {
          valid = false;
          errors.push(key);
        }
      }
      if (errors.length) {
        console.error(errors);
        this.errors = errors;
      } else {
        this.errors = [];
      }
      console.log(obj, valid);
      return valid;
    },
    async upload(files) {
      const form = new FormData();
      // File parsed by multer from incoming request
      for (const f of files) {
        form.append("file", f);
      }
      try {
        let res = await this.$axios.$post(`/api/upload`, form, {
          headers: {
            "Content-Type": "multipart/form-data",
          },
        });
        return res;
      } catch (error) {
        
      }
      return false;
    },
    async formSubmit() {},
  },
};
</script>
