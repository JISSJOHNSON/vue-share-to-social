<template>
  <v-speed-dial
    id="shareButton"
    v-model="fab"
    right
    bottom
    fixed
    transition="slide-y-reverse-transition"
    direction="top"
  >
    <template v-slot:activator>
      <v-btn v-model="fab" :color="icon.color" dark fab>
        <v-img v-if="fab" :src="icon.close" height="30px" contain></v-img>
        <v-img v-else :src="icon.share" height="30px" contain></v-img>
      </v-btn>
    </template>
    <template v-for="(item,i) in shareButtons">
      <v-tooltip bottom :key="i" transition="slide-y-transition" v-if="item.enable">
        <template v-slot:activator="{ on, attrs }">
          <a :href="item.url" target="_blank" style="text-decoration: none;" v-bind="attrs" v-on="on">
            <v-btn fab dark :color="item.color??'#ffffff'">
              <v-img :src="item.icon" height="30px" contain></v-img>
            </v-btn>
          </a>
        </template>
        <span class="text-capitalize" style="font-size: 12px">
        {{ item.name }}
        </span>
      </v-tooltip>
    </template>
  </v-speed-dial>
</template>

<script>

export default {
  name: "SocialShare",
  props: {
    items: {
      type: Array,
      required: false,
      default: () => {
        return []
      }
    },
    options: {
      type: Object,
      required: false,
      default: () => {
        return {}
      }
    },
    icon: {
      type: Object,
      required: false,
      default: () => {
        return {
          color: '#ffffff',
          share: 'https://img.icons8.com/color/search/share',
          close: 'https://img.icons8.com/color/search/cancel',
        }
      }
    }
  },
  data() {
    return {
      fab: false,
      defaultItems: [
        {
          name: 'mail',
          url: 'mailto:?body=',
          icon: 'https://img.icons8.com/color/search/envelope',
          enable: true,
        },
        {
          name: 'linkedin',
          url: 'https://www.linkedin.com/sharing/share-offsite/?url=',
          icon: 'https://img.icons8.com/color/search/linkedin',
          enable: true,
        },
        {
          name: 'twitter',
          url: 'https://twitter.com/intent/tweet?text=',
          icon: 'https://img.icons8.com/color/search/twitter',
          enable: true,
        },
        {
          name: 'facebook',
          url: 'https://www.facebook.com/sharer/sharer.php?u=',
          icon: 'https://img.icons8.com/color/search/facebook',
          enable: true,
        },
        {
          name: 'whatsapp',
          url: 'https://api.whatsapp.com/send?text=',
          icon: 'https://img.icons8.com/color/search/whatsapp',
          enable: true,
        },
      ]
    }
  },
  computed: {
    shareButtons() {
      let shareItems = [];
      this.items.forEach(item => {
        if (typeof item === "string") {
          shareItems.push(
            this.defaultItems.find(shareItem => {
              return shareItem.name === item;
            })
          );
        } else shareItems.push(item);
      });
      return shareItems.map(obj => {
        return {
          name: obj.name,
          url: obj.url + window.location.href,
          icon: obj.icon ?? 'https://img.icons8.com/color/search/link',
          enable: !!(obj.enable ?? obj.enable === undefined),
        };
      });
    }
  }
}
</script>
