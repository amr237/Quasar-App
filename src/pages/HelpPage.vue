<template>
  <div class="help">
    <div class="q-pa-md q-gutter-sm">
      <q-bar>
        <q-btn dense flat :icon="fabApple" />
        <div class="text-weight-bold">App</div>
        <div class="cursor-pointer gt-md">File</div>
        <div class="cursor-pointer gt-md">Edit</div>
        <div class="cursor-pointer gt-md">View</div>
        <div class="cursor-pointer gt-md">Window</div>
        <div class="cursor-pointer gt-md">Help</div>
        <q-space />
        <q-btn dense flat icon="airplay" class="gt-xs" />
        <q-btn dense flat icon="battery_charging_full" />
        <q-btn dense flat icon="wifi" />
        <div>9:41</div>
        <q-btn dense flat icon="search" />
        <q-btn dense flat icon="list" />
      </q-bar>
    </div>

    <div class="q-pa-md">
      <div class="bg-cyan text-white">
        <q-toolbar>
          <q-btn flat round dense icon="assignment_ind" />

          <q-toolbar-title>Quasar</q-toolbar-title>

          <q-btn flat round dense icon="sim_card" class="q-mr-xs" />
          <q-btn flat round dense icon="gamepad" />
        </q-toolbar>
        <q-toolbar inset>
          <q-breadcrumbs active-color="white" style="font-size: 16px">
            <q-breadcrumbs-el label="Home" icon="home" />
            <q-breadcrumbs-el label="Components" icon="widgets" />
            <q-breadcrumbs-el label="Toolbar" />
          </q-breadcrumbs>
        </q-toolbar>
      </div>
    </div>

    <div class="q-pa-md q-gutter-sm">
      <q-banner inline-actions class="text-white bg-red">
        You have lost connection to the internet. This app is offline.
        <template v-slot:action>
          <q-btn flat color="white" label="Turn ON Wifi" />
        </template>
      </q-banner>
    </div>

    <div class="q-pa-md">
      <q-ajax-bar
        ref="bar"
        position="bottom"
        color="accent"
        size="10px"
        skip-hijack
      />

      <q-btn color="primary" label="Trigger" @click="trigger" />
    </div>
  </div>
  <div class="q-pa-md q-gutter-y-md">
    <div class="q-gutter-sm">
      <q-chip>
        <q-avatar color="red" text-color="white">50</q-avatar>
        Emails
      </q-chip>
      <q-chip>
        <q-avatar>
          <img src="https://cdn.quasar.dev/img/boy-avatar.png" />
        </q-avatar>
        John
      </q-chip>
    </div>

    <q-item clickable v-ripple>
      <q-item-section side>
        <q-avatar rounded size="48px">
          <img src="https://cdn.quasar.dev/img/avatar.png" />
          <q-badge floating color="teal">new</q-badge>
        </q-avatar>
      </q-item-section>
      <q-item-section>
        <q-item-label>Mary</q-item-label>
        <q-item-label caption>2 new messages</q-item-label>
      </q-item-section>
      <q-item-section side> 3 min ago </q-item-section>
    </q-item>
  </div>

  <div class="q-pa-md q-gutter-md">
    <q-badge rounded color="yellow" />
    <q-badge rounded color="green" />
    <q-badge rounded color="red" />
    <div class="q-gutter-md q-ml-none">
      <q-btn round icon="notifications">
        <q-badge floating color="red" rounded />
      </q-btn>
      <q-btn color="blue">
        Notifications
        <q-badge color="red" rounded floating />
      </q-btn>
    </div>
    <div><q-badge color="blue" rounded class="q-mr-sm" />Status</div>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  name: "HelpPage",
  setup() {
    const bar = ref(null);

    // we manually trigger it (this is not needed if we
    // don't skip Ajax calls hijacking)
    function trigger() {
      const barRef = bar.value;
      barRef.start();

      setTimeout(() => {
        const barRef = bar.value;
        if (barRef) {
          barRef.stop();
        }
      }, Math.random() * 3000 + 1000);
    }

    return {
      bar,
      trigger,
    };
  },
};
</script>
