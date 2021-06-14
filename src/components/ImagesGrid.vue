<template>
  <section>

    <div class="grid grid-cols-5 gap-4 mx-4">

      <div v-for="imagesColumn in images" class="h-full" :key="imagesColumn">
        <div v-for="image in imagesColumn" class="mb-3 " :key="image">
          <img class="w-full rounded-md" :style="{'height': `${image.height}`}" :src="image.url" alt="" loading="lazy"
               @load="normalizeHeightOfImage(image, imagesColumn, $event)">
        </div>
      </div>

    </div>
  </section>
</template>

<script>
export default {
  name: "ImagesGrid",
  IMAGE_HEIGHT_LIMIT: 350,


  data() {
    return {
      images: [
        [
          {
            title: 'image',
            url: 'https://media.istockphoto.com/photos/colored-powder-explosion-abstract-closeup-dust-on-backdrop-colorful-picture-id1072093690?k=6&m=1072093690&s=612x612&w=0&h=Eyk67XBt4sr3Bk1MubM6dHpvEVNICX4L7FumWhcTwuY=',
          },
          {
            title: 'image',
            url: 'https://images.ctfassets.net/hrltx12pl8hq/3MbF54EhWUhsXunc5Keueb/60774fbbff86e6bf6776f1e17a8016b4/04-nature_721703848.jpg?fit=fill&w=480&h=270',
          },
          {
            title: 'image',
            url: 'https://cdn.pixabay.com/photo/2015/04/23/22/00/tree-736885_960_720.jpg',
          }
        ],
        [
          {
            title: 'image',
            url: 'https://media.istockphoto.com/photos/business-man-pushing-large-stone-up-to-hill-business-heavy-tasks-and-picture-id825383494?k=6&m=825383494&s=612x612&w=0&h=pamh6qxyNPCnNAVru4BrAHt2qTHAGCD9lDiN_6MbaNY=',
          },
          {
            title: 'image',
            url: 'https://ichef.bbci.co.uk/news/999/cpsprodpb/15951/production/_117310488_16.jpg',
          },
          {
            title: 'image',
            url: 'https://purewows3.imgix.net/images/articles/2020_03/calming-pictures-cat.jpg?auto=format,compress&cs=strip',
          },

        ],
        [
          {
            title: 'image',
            url: 'https://tourspoland.com/images/Pictures_Poland/beautiful_sunset_poland_sea.jpg',
          },
          {
            title: 'image',
            url: 'https://pbs.twimg.com/profile_images/1098225250469326848/2KN00JjZ_400x400.png',
          },
          {
            title: 'image',
            url: 'https://www.planetware.com/wpimages/2019/11/canada-in-pictures-beautiful-places-to-photograph-morraine-lake.jpg',
          },

        ],
        [
          {
            title: 'image',
            url: 'https://www.planetware.com/wpimages/2020/01/india-in-pictures-beautiful-places-to-photograph-taj-mahal.jpg',
          },
          {
            title: 'image',
            url: 'https://drifterplanet.com/wp-content/uploads/2017/12/Cancun-Private-Beach-Party.jpg',
          },
          {
            title: 'image',
            url: 'https://media.istockphoto.com/photos/villefranche-on-sea-in-evening-picture-id1145618475?k=6&m=1145618475&s=612x612&w=0&h=u6mv9zLy6WWdxnGxJ4i3bYOFQYJtxjmnkvgVoaGqf_U=',

          },

        ],
        [
          {
            title: 'image',
            url: 'https://media-exp1.licdn.com/dms/image/C4E1BAQE-Zxrt-01Idw/company-background_10000/0/1615323777521?e=2159024400&v=beta&t=8U_G8GwdzneRm4cihyeOfmKKJjk0e-qtZHmWqX4b1NQ',
            height: 250,
          },
          {
            title: 'image',
            url: 'https://www.planetware.com/wpimages/2020/01/china-in-pictures-beautiful-places-to-photograph-the-great-wall.jpg',
            height: 250,
          },
          {
            title: 'image',
            url: 'https://i.pinimg.com/originals/50/df/34/50df34b9e93f30269853b96b09c37e3b.jpg',
            height: 250,
          },

        ],
      ]
    };
  },

  methods: {


    normalizeHeightOfImage(img, imagesColumn, event) {

      if (event.target.height > this.$options.IMAGE_HEIGHT_LIMIT) {

        const indexCol = this.images.indexOf(imagesColumn);
        const indexImg = this.images[indexCol].indexOf(img);

        // event.target.style.height = `${this.$options.IMAGE_HEIGHT_LIMIT}px`;
        event.target.style.height = `auto`;
        this.images[indexCol][indexImg] = img;
        this.images = [...this.images];

      }

    },
  },
}
</script>

<style scoped>
img {
  object-fit: cover;
}
</style>
