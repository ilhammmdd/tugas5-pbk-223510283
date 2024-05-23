<template>
  <q-layout view="lHh Lpr lFf">
    <!-- Navbar -->
    <q-header elevated class="bg-primary text-white">
      <div class="navbar q-px-md q-pt-sm q-pb-md row items-center justify-between">
        <div class="logo">
          <h3>My Shop</h3>
        </div>
        <div class="search-bar row items-center">
          <q-input filled v-model="search" placeholder="Search..." class="q-mr-sm"/>
          <q-btn round icon="search" color="white" @click="performSearch"/>
        </div>
        <div class="nav-items row items-center">
          <q-btn flat label="Cart" to="/cart" class="q-ml-md"/>
          <q-btn flat label="Login" to="/login" class="q-ml-md"/>
          <q-btn flat label="Help" to="/help" class="q-ml-md"/>
        </div>
      </div>
    </q-header>

    <!-- Main Content -->
    <q-page-container>
      <q-page class="q-pa-md">
        <!-- Carousel -->
        <q-carousel v-model="slide" arrows infinite animated class="carousel">
          <!-- Update the image sources here -->
          <q-carousel-slide v-for="n in 3" :key="n" :name="n" :img-src="carouselImages[n-1]" />
        </q-carousel>

        <!-- Cards -->
        <div class="q-gutter-md row justify-center">
          <q-card v-for="item in items" :key="item.id" class="my-card q-col-xs-12 q-col-sm-6 q-col-md-4">
            <q-img :src="item.image" ratio="16/9" contain/>
            <q-card-section>
              <div class="text-h6">{{ item.title }}</div>
              <div class="text-subtitle2">{{ item.description }}</div>
            </q-card-section>
            <q-card-actions align="right">
              <q-btn flat label="Buy Now" color="primary" />
            </q-card-actions>
          </q-card>
        </div>
      </q-page>
    </q-page-container>

    <!-- Footer -->
    <q-footer class="bg-primary text-white q-pa-md">
      <q-toolbar>
        <q-toolbar-title>© 2024 Ilham.Shop</q-toolbar-title>
        <div class="row items-center">
          <q-btn flat label="Privacy Policy" to="/privacy" class="q-ml-md text-white"/>
          <q-btn flat label="Terms of Service" to="/terms" class="q-ml-md text-white"/>
        </div>
      </q-toolbar>
    </q-footer>
  </q-layout>
</template>

<script>
export default {
  data() {
    return {
      search: '',
      slide: 1,
      carouselImages: [
        'https://www.static-src.com/wcsstore/Indraprastha/images/catalog/full/catalog-image/MTA-153648499/samsung_samsung_galaxy_s24_ultra_12-512gb_-upgrade_dari_12-256gb-_handphone_ai-_smartphone-_s_pen_full05_kn5ognlp.jpg',
        'https://www.blibli.com/friends-backend/wp-content/uploads/2024/02/MicrosoftTeams-image-1-26.jpg',
        'https://awsimages.detik.net.id/community/media/visual/2023/04/04/adv-blibli.png?w=1200',
      ],
      items: [
        { id: 1, title: 'Item 1', description: 'Description 1', image: 'https://awsimages.detik.net.id/community/media/visual/2023/04/04/adv-blibli.png?w=1200' },
        { id: 2, title: 'Item 2', description: 'Description 2', image: '' },
        { id: 3, title: 'Item 3', description: 'Description 3', image: '' },
        { id: 4, title: 'Item 4', description: 'Description 4', image: '' },
        { id: 5, title: 'Item 5', description: 'Description 5', image: '' },
        { id: 6, title: 'Item 6', description: 'Description 6', image: '' },
      ]
    };
  },
  methods: {
    performSearch() {
      console.log('Search for:', this.search);
    }
  }
}
</script>

<style scoped>
h3 {
  font-weight: bold;
}

.navbar {
  background-color: var(--q-primary);
}

.carousel {
  margin-bottom: 20px;
}

.my-card {
  transition: transform 0.2s ease-in-out;
}
.my-card:hover {
  transform: scale(1.05);
}
</style>
