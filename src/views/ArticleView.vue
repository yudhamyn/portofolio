<template>
  <div class="w-full md:w-3/5 mx-auto md:mt-5">
    <div class="bg-white rounded-xl mx-3 p-5 md:p-10 md:mx-0">
      <div>
        <h1 class="text-xl md:text-4xl text-black text-left font-bold leading-relaxed">{{ article.title }}</h1>
        <div class="mt-3 text-left text-gray-800 text-sm">Published at <span>{{ article.date }}</span></div>
        <div class="h-[2px] w-20 my-5 md:my-10 bg-[#00f9ff] md:w-1/3 aos-init aos-animate mr-2"></div>
        <div>
          <swiper ref="swiper" :slides-per-view="1" pagination @slideChange="updatePagination">
            <swiper-slide v-for="(image, index) in article.images" :key="index">
              <div class="relative w-full h-0 pb-[50%]">
                <img :src="getImageUrl(image)" @click="openLightbox(index)" class="absolute top-0 left-0 w-full h-full object-cover rounded-lg cursor-pointer" alt="Thumbnail">
              </div>
            </swiper-slide>
          </swiper>
          <div class="swiper-pagination-container">
            <div v-for="(image, index) in article.images" :key="index" class="swiper-pagination-item" @click="goToSlide(index)" :class="{ active: index === currentSlide }"></div>
          </div>
        </div>
        <div class="text-left text-black mt-8">
          <ul>
            <li v-for="(point, index) in article.desc" :key="index">{{ point }}</li>
          </ul>
        </div>
      </div>
    </div>
    <div v-if="lightboxOpen" class="fixed inset-0 bg-black bg-opacity-75 flex justify-center items-center z-50" @click="closeLightbox">
      <img :src="getImageUrl(article.images[lightboxIndex])" class="max-w-full max-h-full">
    </div>
  </div>
</template>

<script>
import { useRoute } from 'vue-router';
import { Swiper, SwiperSlide } from 'swiper/vue';
import 'swiper/swiper-bundle.css';

export default {
  components: {
    Swiper,
    SwiperSlide
  },
  data() {
    return {
      defaultImage: 'default-image.png', // Ganti dengan jalur gambar default Anda
      articles: [
        {
          id: 1,
          slug: 'introduction-to-nodejs',
          date: 'May 18, 2023',
          title: 'Introduction to NodeJS',
          desc: [
            'Learn the basics of NodeJS, a powerful JavaScript runtime.',
            'Understand how to set up and run a NodeJS application.',
            'Explore the vast ecosystem of NodeJS modules and packages.'
          ],
          images: ['comingsoon', 'yudha', 'yudha']
        },
        {
          id: 2,
          slug: 'latest-tech-trends',
          date: 'June 25, 2023',
          title: 'Latest Tech Trends',
          desc: [
            'Discover the latest trends in technology and how they are shaping the future.',
            'Examine the impact of artificial intelligence and machine learning.',
            'Understand the growing importance of cybersecurity in today\'s digital world.'
          ],
          images: ['tech_image1', 'tech_image2']
        },
        {
          id: 3,
          slug: 'vuejs-for-beginners',
          date: 'Thursday',
          title: 'VueJS for Beginners',
          desc: [
            'A beginner\'s guide to building applications with VueJS.',
            'Learn about VueJS components, directives, and the Vue instance.',
            'Understand how to manage state and handle events in VueJS.'
          ],
          images: ['vuejs_image1', 'vuejs_image2']
        },
        {
          id: 4,
          slug: 'reactjs-advanced',
          date: 'Thursday',
          title: 'ReactJS Advanced',
          desc: [
            'Dive deeper into advanced concepts of ReactJS.',
            'Learn about hooks, context API, and advanced component patterns.',
            'Explore performance optimization techniques for React applications.'
          ],
          images: ['react_image1', 'react_image2']
        },
        {
          id: 5,
          slug: 'css-tricks-and-tips',
          date: 'Friday',
          title: 'CSS Tricks and Tips',
          desc: [
            'Discover useful CSS tricks and tips for modern web development.',
            'Learn about CSS grid, flexbox, and responsive design techniques.',
            'Understand how to use CSS preprocessors like SASS and LESS.'
          ],
          images: ['css_image1', 'css_image2']
        },
        {
          id: 6,
          slug: 'javascript-best-practices',
          date: 'Sunday',
          title: 'JavaScript Best Practices',
          desc: [
            'Follow best practices for writing clean and maintainable JavaScript code.',
            'Understand how to structure your JavaScript applications effectively.',
            'Learn about modern JavaScript features and how to use them.'
          ],
          images: ['javascript_image1', 'javascript_image2']
        },
        {
          id: 7,
          slug: 'html-semantics',
          date: 'Tuesday',
          title: 'HTML Semantics',
          desc: [
            'Learn the importance of using semantic HTML tags.',
            'Understand how to improve accessibility and SEO with semantic HTML.',
            'Explore examples of semantic HTML usage in modern web development.'
          ],
          images: ['html_image1', 'html_image2']
        }
      ],
      article: {},
      currentSlide: 0,
      lightboxOpen: false,
      lightboxIndex: 0
    };
  },
  mounted() {
    this.getArticleDetails();
  },
  methods: {
    getArticleDetails() {
      const route = useRoute();
      const articleId = parseInt(route.params.id);
      this.article = this.articles.find(article => article.id === articleId) || {};
    },
    getImageUrl(imageUrl) {
      const supportedFormats = ['jpg', 'png', 'gif'];
      for (let format of supportedFormats) {
        let fullPath = `/portofolio/img/${imageUrl}.${format}`;
        if (this.imageExists(fullPath)) {
          return fullPath;
        }
      }
      return this.defaultImage; // or a default image path if no image is found
    },
    imageExists(url) {
      const http = new XMLHttpRequest();
      http.open('HEAD', url, false);
      http.send();
      return http.status !== 404;
    },
    updatePagination(swiper) {
      this.currentSlide = swiper.activeIndex;
    },
    goToSlide(index) {
      this.$refs.swiper.swiper.slideTo(index);
    },
    openLightbox(index) {
      this.lightboxOpen = true;
      this.lightboxIndex = index;
      this.currentSlide = index; 
    },
    closeLightbox() {
      this.lightboxOpen = false;
    }
  }
};
</script>

<style scoped>
.swiper-pagination-container {
  display: flex;
  justify-content: center;
  margin-top: 10px;
}

.swiper-pagination-item {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background-color: #888;
  margin: 0 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.swiper-pagination-item.active {
  background-color: #00f9ff;
}
</style>
