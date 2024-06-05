<template>
  <div class="container mx-auto p-3 md:p-8">
    <div class="flex flex-col-reverse md:flex-row relative">
      <div class="w-full">
        <div class="flex flex-col gap-4 md:px-20 fade-zoom-up">
          <article v-for="article in articles" :key="article.id" class="article-card">
            <router-link :to="`/read/${article.slug}/${article.id}`" class="article-link">
              <div class="w-full pr-4">
                <div class="article-date">
                  <div class="date-line"></div>
                  {{ article.date }}
                </div>
                <h1 class="article-title">{{ article.title }}</h1>
                <ul class="article-desc">
                  <li v-for="(point, index) in article.desc" :key="index">{{ point }}</li>
                </ul>
              </div>
              <div class="article-image-container">
                <img :src="article.image" class="article-image" alt="Article Image">
              </div>
            </router-link>
          </article>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      articles: [
        {
          id: 1,
          slug: 'Bengkel Koding (Dian Nuswantoro Foundation) – Semarang',
          date: 'Feb 2024 – Present',
          title: 'Mentor Data Science',
          desc: [
            'Guided 5 senior students through Thesis 1 (TA1) and Thesis 2 (TA2) stages, focusing on Data Science',
            'Improved the data science course module for Bengkel Koding',
            'Developed mid-semester and final exams in project format for 30+ students.',
            'Conducted comprehensive assessments of student assignments per guidelines',
            'Utilized Python and Google Colab for instruction and project development.'
          ],
          image: 'https://via.placeholder.com/150'
        },
        {
          id: 2,
          slug: 'Home Credit - Data Scientist Intern (Project Based)',
          date: 'Dec 2023 – Jan 2024',
          title: 'Home Credit - Data Scientist Intern (Project Based) ',
          desc: [
            'Developed a credit risk prediction model using Random Forest, analyzing data for 10,000+ customers.',
            'Provided insights into variable relationships and credit risk, enhancing decision-making.',
            'Identified 5 potential customer segments for targeted promotions',
            'Utilized Python, Pandas, and Scikit-learn for data analysis and model development.',
            'Recommended 3 promotional strategies based on model analysis.'
          ],
          image: 'https://via.placeholder.com/150'
        },
        {
          id: 3,
          slug: 'Kalbe Nutritionals - Data Scientist Intern (Project Based)',
          date: 'Sep 2023 – Oct 2023',
          title: 'Kalbe Nutritionals - Data Scientist Intern (Project Based)',
          desc: [
            'Finishing various task relate with the activity of Data Scientist from Kalbe Nutritionals, such as Data Analysis, Machine Learning Implementation, and Business Acumen.',
            'Analyzed inventory demand with ARIMA, optimizing daily inventory for 100+ products.',
            'Segmented market using KMeans clustering, improving personalized promotions.',
            'Developed 4 Tableau visualizations and a dashboard to track sales and inventory.',
            'Utilized Python, Jupyter Notebook, Tableau, Dbeaver, and PostgreSQL for data analysis.',
          ],
          image: 'https://via.placeholder.com/150'
        },
        {
          id: 4,
          slug: 'reactjs-advanced',
          date: 'May 2023 – Dec 2023 ',
          title: 'Head of Team Development PPK ORMAWA',
          desc: [
            'Led a 4-member team, achieving a 20% enhancement in the functionality of the jarictku.com.',
            'Conducted bi-weekly progress meetings, maintaining 100% adherence to project timelines.',
            'Innovated and implemented ideas, resulting in a 15% improvement in the jarictku.com features.',
            'Provided 5 training sessions, leading to a 25% increase in team efficiency in using and maintaining the website.',
            'Collaborated with the design team to improve the user experience and interface of the jarictku.com.',

          ],
          image: 'https://via.placeholder.com/150'
        },
        {
          id: 5,
          slug: 'css-tricks-and-tips',
          date: 'Aug 2022 – Aug 2023 ',
          title: 'Head of Hardware Division ',
          desc: [
            'Led and managed 14 team members, achieving a 20% increase in hardware maintenance efficiency.',
            'Implemented task division for maintaining HM-TI camp hardware, including printers, computers, hard disks, etc.',
            'Successfully maintained and repaired damaged hardware to reduces downtime.',
            'Conducted bi-monthly equipment inspections, ensuring a 100% compliance rate for HM-TI hardware.',
            'Collaborated with the head of the software division, providing training that resulted in a 25% improvement in members proficiency in software and hardware.'
          ],
          image: 'https://via.placeholder.com/150'
        },
        {
          id: 6,
          slug: 'javascript-best-practices',
          date: 'Dec 2022 – Mar 2023 ',
          title: 'Head of HI-Technology 2023 ',
          desc: [
            'Led 48 team members, achieving a 50% funding increase and attracting 15 software hardware fair teams.',
            'Successfully got sponsorship IDR 14,820,000. Increased 120% compared to 2022 funding.',
            'Generated a 300% increase in visitor votes compared to the previous year (online).',
            '●	Motivated and guided team members to achieve vision, mission, and activity goals, resulting in successful events and budget realization.'
          ],
          image: 'https://avatars.githubusercontent.com/u/46035403?s=280&v=4'
        },
        {
          id: 7,
          slug: 'html-semantics',
          date: 'Jan 2023 – Feb 2023 ',
          title: 'Head of Code Jam Academy ',
          desc: [
            'Led and managed 4 team members, achieving successful Code Jam Academy training.',
            'Prepared proposals and activity plans, focusing on Laravel as the training theme.',
            'Created material for the training, ensuring effective knowledge transfer.',
            'Generated accountability reports detailing event realization and budget for all activities.'
          ],
          image: 'https://via.placeholder.com/150'
        },
        {
          id: 8,
          slug: 'html-semantics',
          date: 'Sep 2022 – Oct 2022',
          title: 'Coordinator of the Laravel Workshop Event Division ',
          desc: [
            'Led and managed 9 team members, ensuring successful workshop events.',
            'Conducted a deep meeting for event members to discuss and plan the workshop.',
            'Orchestrated all event preparations, including rehearsals and speaker arrangements.',
            'Coordinated the entire event on the day, following a detailed rundown.'
          ],
          image: 'https://via.placeholder.com/150'
        }
      ]
    }
  }
}
</script>

<style scoped>
.container {
  max-width: 1200px;
}
.article-card {
  background-color: #1e1e1f;
  border: 1px solid #383838;
  border-radius: 1rem;
  padding: 1.25rem;
  margin-bottom: 1rem;
  display: flex;
  transition: background-color 0.3s;
}
.article-card:hover {
  background-color: #282828;
}
.article-link {
  display: flex;
  width: 100%;
  text-decoration: none;
  color: white;
}
.article-date {
  font-size: 0.75rem;
  margin-bottom: 0.25rem;
  color: #94a3b8;
  display: flex;
  align-items: center;
  font-style: italic;
}
.date-line {
  height: 1px;
  width: 5rem;
  background-color: #bfdbfe;
  margin-right: 0.5rem;
}
.article-title {
  font-size: 1rem;
  color: #bfdbfe;
  font-weight: bold;
  margin-bottom: 0.5rem;
}
.article-desc {
  font-size: 0.875rem;
  overflow: hidden;
  text-overflow: ellipsis;
  text-align: left;
}
.article-desc li {
  list-style-type: disc;
  margin-left: 1.5rem;
}
.article-image-container {
  width: 5rem;
  height: 5rem;
  display: flex;
  align-items: center;
  justify-content: center;
}
.article-image {
  border-radius: 1rem;
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.fade-zoom-up {
  animation: fadeZoomUp 1s ease-in-out;
}
@keyframes fadeZoomUp {
  0% {
    opacity: 0;
    transform: scale(0.5);
  }
  100% {
    opacity: 1;
    transform: scale(1);
  }
}
</style>
