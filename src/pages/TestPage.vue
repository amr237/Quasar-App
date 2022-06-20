<template>
  <div class="test"></div>
  <div class="q-pa-md">
    <div class="row grid">
      <div class="col-xs-2">.col</div>
      <div class="col-xs-8">
        <p
          class="text-h3 text-weight-bold text-center text-pink-13 cursor-pointer"
        >
          Align text to the center
        </p>
      </div>
      <div class="col-xs-2">.col</div>
    </div>
    <div class="row" style="height: 150px">
      <div class="col-4 col-md-6">.col-4 .col-md-6</div>
      <div class="col-4 col-md-6">.col-4 .col-md-6</div>
      <div class="col-4 col-md-6">.col-4 .col-md-6</div>
    </div>

    <q-btn-dropdown class="glossy" color="purple" label="Account Settings">
      <div class="row no-wrap q-pa-md">
        <div class="column">
          <div class="text-h6 q-mb-md">Settings</div>
          <q-toggle v-model="mobileData" label="Use Mobile Data" />
          <q-toggle v-model="bluetooth" label="Bluetooth" />
        </div>

        <q-separator vertical inset class="q-mx-lg" />

        <div class="column items-center">
          <q-avatar size="72px">
            <img src="https://cdn.quasar.dev/img/boy-avatar.png" />
          </q-avatar>

          <div class="text-subtitle1 q-mt-md q-mb-xs">John Doe</div>

          <q-btn color="primary" label="Logout" push size="sm" v-close-popup />
        </div>
      </div>
    </q-btn-dropdown>

    <q-btn label="Alert" color="primary" @click="alert = true" />
    <q-btn label="Confirm" color="primary" @click="confirm = true" />
    <q-btn label="Prompt" color="primary" @click="prompt = true" />

    <q-dialog v-model="alert">
      <q-card>
        <q-card-section>
          <div class="text-h6">Alert</div>
        </q-card-section>

        <q-card-section class="q-pt-none">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Rerum
          repellendus sit voluptate voluptas eveniet porro. Rerum blanditiis
          perferendis totam, ea at omnis vel numquam exercitationem aut, natus
          minima, porro labore.
        </q-card-section>

        <q-card-actions align="right">
          <q-btn flat label="OK" color="primary" v-close-popup />
        </q-card-actions>
      </q-card>
    </q-dialog>

    <q-dialog v-model="confirm" persistent>
      <q-card>
        <q-card-section class="row items-center">
          <q-avatar icon="signal_wifi_off" color="primary" text-color="white" />
          <span class="q-ml-sm"
            >You are currently not connected to any network.</span
          >
        </q-card-section>

        <q-card-actions align="right">
          <q-btn flat label="Cancel" color="primary" v-close-popup />
          <q-btn flat label="Turn on Wifi" color="primary" v-close-popup />
        </q-card-actions>
      </q-card>
    </q-dialog>

    <q-dialog v-model="prompt" persistent>
      <q-card style="min-width: 350px">
        <q-card-section>
          <div class="text-h6">Your address</div>
        </q-card-section>

        <q-card-section class="q-pt-none">
          <q-input
            dense
            v-model="address"
            autofocus
            @keyup.enter="prompt = false"
          />
        </q-card-section>

        <q-card-actions align="right" class="text-primary">
          <q-btn flat label="Cancel" v-close-popup />
          <q-btn flat label="Add address" v-close-popup />
        </q-card-actions>
      </q-card>
    </q-dialog>
  </div>
</template>

<script>
import { ref } from "vue";
export default {
  setup() {
    return {
      mobileData: ref(false),
      bluetooth: ref(false),
      alert: ref(false),
      confirm: ref(false),
      prompt: ref(false),

      address: ref(""),
    };
  },

  name: "TestPage",
};
</script>

<style scoped>
.grid div {
  padding: 10px 15px;
  background: rgba(8, 232, 228, 0.15);
  border: 1px solid rgba(4, 0, 11, 0.895);
}
.grid {
  margin-top: 1rem;
}
.q-focus-helper,
.q-focusable,
.q-manual-focusable,
.q-hoverable {
  outline: 0;
  display: inline-block;
  margin: 20px;
}
</style>
