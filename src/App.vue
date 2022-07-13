<template>
  <v-app>
    <SocialShare :items="items"/>
  </v-app>
</template>

<script>
import SocialShare from "@/components/SocialShare";

export default {
  name: 'App',
  components: {
    SocialShare,
  },
  data() {
    return {
      options: {
        color: 'blue',
        mdiIcon: 'share-variant',
        mdiClose: 'close',
        direction: 'top',
        top: false,
        right: true,
        bottom: true,
        left: false,
      },
      items: [
        'mail',
        'linkedin',
        'twitter',
        'facebook',
        'whatsapp',
        {
          name: 'telegram',
          url: 'https://telegram.me/share/url?url=',
          icon: 'https://img.icons8.com/color/search/instagram',
        },
      ],
    }
  },
};
</script>
