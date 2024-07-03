<template>
  <div class="w-full md:w-3/5 h-20 mx-auto md:mt-5">
    <div class="bg-white rounded-xl mx-3 p-5 md:p-10 md:mx-0">
      <div>
        <h1 class="text-xl md:text-4xl text-black text-left font-bold leading-relaxed">{{ article.title }}</h1>
        <div class="mt-3 text-left text-gray-800 text-sm">Published at <span>{{ article.date }}</span></div>
        <div class="h-[2px] w-20 my-5 md:my-10 bg-[#00f9ff] md:w-1/3 aos-init aos-animate mr-2"></div>
        <div>
          <div class="relative w-full" style="padding-top: 50%;">
            <img :src="getImageUrl(article.image)" class="absolute top-0 left-0 rounded-lg w-full h-full object-cover" alt="Thumbnail">
          </div>
        </div>
        <div class="text-left text-black mt-8">
          <ul>
            <li v-for="(point, index) in article.desc" :key="index">{{ point }}</li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { useRoute } from 'vue-router';

export default {
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
          image: 'comingsoon'
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
          image: 'https://via.placeholder.com/600x300'
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
          image: 'https://via.placeholder.com/600x300'
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
          image: 'https://via.placeholder.com/600x300'
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
          image: 'https://via.placeholder.com/600x300'
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
          image: 'https://via.placeholder.com/600x300'
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
          image: 'https://via.placeholder.com/600x300'
        }
      ],
      article: {}
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
    }
  }
};
</script>

<style scoped>
img {
  display: block;
  max-width: 100%;
  height: auto;
}
</style>
