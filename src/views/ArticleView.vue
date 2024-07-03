<template>
  <div class="w-full md:w-3/5 mx-auto md:mt-5">
    <div class="bg-white rounded-xl mx-3 p-5 md:p-10 md:mx-0">
      <div>
        <h1 class="text-xl md:text-4xl text-black text-left font-bold leading-relaxed">{{ article.title }}</h1>
        <div class="mt-1 text-left text-gray-800 text-sm">Published at <span>{{ article.date }}</span></div>
        <div class="h-[2px] w-20 my-5 md:my-5 bg-[#00f9ff] md:w-1/3 aos-init aos-animate mr-2"></div>
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
        <div class="text-left text-black mt-4">
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
            'I have extensive experience in guiding senior students through both Thesis 1 (TA1) and Thesis 2 (TA2) stages, with a specific focus on Data Science. I played a pivotal role in enhancing the data science course module for Bengkel Koding, incorporating advanced methodologies and current industry trends. Additionally, I developed project-based mid-semester and final exams tailored to over 30 students, aimed at fostering practical skills and real-world application. I conducted thorough assessments of student assignments in accordance with established guidelines, ensuring comprehensive feedback and evaluation. Throughout these endeavors, I utilized Python and Google Colab extensively for instructional purposes and project development, leveraging their capabilities to enrich the learning experience'
          ],
          images: ['comingsoon', 'comingsoon2', 'comingsoon3']
        },
        {
          id: 2,
          slug: 'latest-tech-trends',
          date: 'June 25, 2023',
          title: 'Latest Tech Trends',
          desc: [
            'I developed a credit risk prediction model using Random Forest, analyzing extensive data from over 10,000 customers. This project provided valuable insights into variable relationships and credit risk dynamics, significantly enhancing decision-making processes. Through meticulous analysis, I identified five distinct customer segments suitable for targeted promotional campaigns, aiming to optimize marketing strategies effectively. Leveraging Python, Pandas, and Scikit-learn, I employed advanced data analysis techniques and model development methodologies. Based on the models findings, I recommended three strategic promotional approaches tailored to different customer segments, ensuring alignment with business objectives and maximizing promotional effectiveness.'
          ],
          images: ['comingsoon', 'comingsoon2', 'comingsoon3']
        },
        {
          id: 3,
          slug: 'vuejs-for-beginners',
          date: 'Thursday',
          title: 'VueJS for Beginners',
          desc: [
            'I have completed various tasks related to the role of a Data Scientist at Kalbe Nutritionals, encompassing comprehensive activities such as Data Analysis, Machine Learning Implementation, and Business Acumen. Using ARIMA, I analyzed inventory demand across a diverse range of over 100 products, effectively optimizing daily inventory management strategies. Through KMeans clustering, I segmented the market, refining personalized promotional campaigns to enhance customer engagement and satisfaction. Additionally, I developed four Tableau visualizations and a user-friendly dashboard to monitor sales trends and inventory levels in real-time. Throughout these initiatives, I utilized a robust toolset including Python, Jupyter Notebook, Tableau, Dbeaver, and PostgreSQL for seamless data analysis and management.'
          ],
          images: ['comingsoon', 'comingsoon2', 'comingsoon3']
        },
        {
          id: 4,
          slug: 'reactjs-advanced',
          date: 'Thursday',
          title: 'ReactJS Advanced',
          desc: [
            'I successfully led a 4-member team, achieving a notable 20% enhancement in the functionality of jarictku.com. Throughout the project, I conducted bi-weekly progress meetings, ensuring 100% adherence to project timelines and milestones. By fostering innovation and implementing new ideas, I facilitated a 15% improvement in the websites features, enhancing its usability and performance. Additionally, I conducted 5 training sessions that resulted in a significant 25% increase in team efficiency in both using and maintaining the website. I collaborated closely with the design team to refine the user experience and interface of jarictku.com, aligning it closely with user needs and preferences.'
          ],
          images: ['comingsoon', 'comingsoon2', 'comingsoon3']
        },
        {
          id: 5,
          slug: 'css-tricks-and-tips',
          date: 'Friday',
          title: 'CSS Tricks and Tips',
          desc: [
            'I led and managed a team of 14 members, successfully achieving a 20% increase in hardware maintenance efficiency at the HM-TI camp. I implemented structured task divisions for the maintenance of various hardware components including printers, computers, and hard disks, optimizing workflows and reducing downtime through timely repairs. Conducting bi-monthly equipment inspections, I ensured a 100% compliance rate for HM-TI hardware standards. Collaborating closely with the software division head, I provided training sessions that resulted in a significant 25% improvement in team members proficiency in both software and hardware operations.'
          ],
          images: ['comingsoon', 'comingsoon2', 'comingsoon3']
        },
        {
          id: 6,
          slug: 'javascript-best-practices',
          date: 'Sunday',
          title: 'JavaScript Best Practices',
          desc: [
            'I led a team of 48 members, achieving remarkable results including a 50% increase in funding and attracting 15 teams to participate in the software hardware fair. Through strategic efforts, I secured sponsorships totaling IDR 14,820,000, marking a significant 120% increase compared to the previous years funding. We also generated a notable 300% increase in online visitor votes compared to the previous edition. By effectively motivating and guiding team members, I ensured alignment with our vision, mission, and activity goals, leading to the successful realization of events and budget objectives.'
          ],
          images: ['comingsoon', 'comingsoon2', 'comingsoon3']
        },
        {
          id: 7,
          slug: 'html-semantics',
          date: 'Tuesday',
          title: 'HTML Semantics',
          desc: [
            'I led and managed a team of 4 members, successfully organizing the Code Jam Academy training. I prepared detailed proposals and activity plans, with a focus on Laravel as the central theme for the training sessions. Additionally, I curated and created comprehensive training materials to facilitate effective knowledge transfer. Throughout the process, I generated accountability reports that meticulously outlined the realization of events and budgets for all activities, ensuring transparency and alignment with organizational goals.'
          ],
          images: ['comingsoon', 'comingsoon2', 'comingsoon3']
        },
        {
          id: 8,
          slug: 'css-animations',
          date: 'Wednesday',
          title: 'CSS Animations',
          desc: [
            'I led and managed a team of 9 members, overseeing the successful execution of workshop events. I initiated comprehensive planning meetings with event members to strategize and outline workshop objectives. I orchestrated all aspects of event preparation, including rehearsals and speaker arrangements, ensuring seamless coordination. On the day of the event, I meticulously coordinated the entire proceedings according to a detailed schedule, ensuring a smooth and successful execution'
          ],
          images: ['comingsoon', 'comingsoon2', 'comingsoon3']
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
