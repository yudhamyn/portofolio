<script>
export default {
  data() {
    return {
      activeTab: 1,
      tech: [
        {
          id: 1,
          name: 'Python',
          imageUrl: 'https://cdn.iconscout.com/icon/free/png-512/free-python-2-226051.png?f=webp&w=512',
          status: 'Advanced'
        },
        {
          id: 2,
          name: 'Machine Learn',
          imageUrl: 'https://cdn.iconscout.com/icon/premium/png-512-thumb/computational-intelligence-2040740-1721091.png?f=webp&w=512',
          status: 'Advanced'
        },
        {
          id: 3,
          name: 'MySQL',
          imageUrl: 'https://cdn.iconscout.com/icon/free/png-512/free-mysql-3628940-3030165.png?f=webp&w=512',
          status: 'Advanced'
        },
        {
          id: 4,
          name: 'HTML',
          imageUrl: 'https://cdn.iconscout.com/icon/free/png-256/html-2752158-2284975.png',
          status: 'Advance'
        },
        {
          id: 5,
          name: 'PHP',
          imageUrl: 'https://cdn.iconscout.com/icon/free/png-256/free-php-2038871-1720084.png',
          status: 'Advanced'
        },
        {
          id: 6,
          name: 'django',
          imageUrl: 'https://cdn.iconscout.com/icon/free/png-256/django-1-282754.png',
          status: 'Intermediate'
        },
        {
          id: 7,
          name: 'Laravel',
          imageUrl: 'https://cdn.worldvectorlogo.com/logos/laravel-2.svg',
          status: 'Intermediate'
        },
        {
          id: 8,
          name: 'Codeigniter',
          imageUrl: 'https://cdn-peanutsquare.b-cdn.net/wp-content/uploads/2022/11/codeigniter-logo.png',
          status: 'Intermediate'
        },
        {
          id: 9,
          name: 'Bootstrap',
          imageUrl: 'https://getbootstrap.com/docs/5.2/assets/brand/bootstrap-logo-shadow.png',
          status: 'Intermediate'
        },
        {
          id: 10,
          name: 'css',
          imageUrl: 'https://cdn.iconscout.com/icon/free/png-256/css-131-722685.png',
          status: 'Intermediate'
        },
        {
          id: 11,
          name: 'tailwind',
          imageUrl: 'https://upload.wikimedia.org/wikipedia/commons/thumb/d/d5/Tailwind_CSS_Logo.svg/1024px-Tailwind_CSS_Logo.svg.png',
          status: 'Intermediate'
        },
        {
          id: 10,
          name: 'sass',
          imageUrl: 'https://cdn.iconscout.com/icon/free/png-256/sass-226054.png',
          status: 'Intermediate'
        },

      ],
      tools: [
        {
          id: 1,
          name: 'Git',
          imageUrl: 'https://git-scm.com/images/logos/downloads/Git-Icon-1788C.png',
          status: 'Version Control'
        },
        {
          id: 2,
          name: 'GitHub',
          imageUrl: 'https://cdn-icons-png.flaticon.com/512/25/25231.png',
          status: 'Git Hosting'
        },
        {
          id: 3,
          name: 'pip',
          imageUrl: 'https://cdn-icons-png.flaticon.com/512/1822/1822899.png',
          status: 'Package Manager'
        },
        {
          id: 4,
          name: 'jupyter notebook',
          imageUrl: 'https://raw.githubusercontent.com/github/explore/a4691f04ff219c1c2aa02fc61fda41aa43f1459a/topics/jupyter-notebook/jupyter-notebook.png',
          status: 'IDE'
        },
        {
          id: 5,
          name: 'VS Code',
          imageUrl: 'https://cdn.iconscout.com/icon/free/png-256/visual-studio-code-1868941-1583105.png',
          status: 'IDE'
        },
        {
          id: 6,
          name: 'Colab',
          imageUrl: 'https://avatars.githubusercontent.com/u/38081706?v=4',
          status: 'IDE'
        },
        {
          id: 7,
          name: 'Google Looker',
          imageUrl: 'https://avatars.githubusercontent.com/u/46035403?s=280&v=4',
          status: 'BI Tool'
        },
        {
          id: 8,
          name: 'Tableau',
          imageUrl: 'https://cdn.filepicker.io/api/file/jZDILlufSOSDOkuJTZ7J',
          status: 'BI Tool'
        },
      ]
    };
  }
}
</script>
<template>
  <div
    class="bg-[#1e1e1f] px-5 py-5 md:px-12 md:py-10 text-left border border-[#383838] rounded-3xl text-amber-50 mx-3 mb-5">
    <article data-page="about">

      <header>
        <div class="text-2xl font-bold text-white mb-5 fadein-bot title-section flex items-center">
          About Me &nbsp;
          <div class="h-[1px] w-32 bg-blue-200 md:w-96 aos-init aos-animate" data-aos="zoom-in-left"
            data-aos-duration="600"></div>
        </div>
      </header>

      <section
        class="text-sm md:text-lg text-justify flex flex-col gap-4 md:flex-row md:gap-8 md:justify-left md:items-center">
        <div class="flex justify-center">
          <img class="w-9/12 rounded-full mb-3 fadein-up"
            src="/portofolio/img/yudhaformal.jpg" alt="Foto">
        </div>
        <div class="md:w-7/12">
          <p class="mb-3 md:mb-7 fadein-left fadeins-1">
            &nbsp; &nbsp; &nbsp; Hi everyone! My name is Yudha Mulyana. I'm a Data enthusiast with a background in technology information system, specializing in research and spatial data analysis. Transitioned from 2 years in course program management and project based to pursue a career in data analytics. 
Skilled in research, analytical thinking, and project management, providing a solid foundation for work as a data scientist and analyst. Proficient in spreadsheets, Python, SQL, BI, and GIS for extracting insights from complex datasets. Dedicated to continuous learning and eager to stay updated with the latest trends and techniques in data analysis. Committed to leveraging data to drive informed decision-making processes.
          </p>
        </div>

      </section>

    </article>
  </div>

  <div class="px-5 py-5 md:px-12 md:py-10 text-left text-amber-50 mx-3">
    <article data-page="about">
      <header>
        <div class="text-2xl font-bold text-white mb-5 fadein-bot title-section flex items-center">
          <div class="h-[1px] w-10 bg-blue-200 md:w-20 aos-init aos-animate" data-aos="zoom-in-left"
            data-aos-duration="600"></div>
          &nbsp; Skills
        </div>
      </header>
      <section>
        <div>
          <ul class="flex flex-wrap text-sm font-medium text-center text-gray-500 dark:text-gray-400 mb-5">
            <li class="mr-2">
              <button class="inline-block px-4 py-3 rounded-lg hover:text-white"
                :class="{ 'text-blue-200 bg-blue-200 bg-opacity-10': activeTab === 1 }" @click="activeTab = 1">Tech Stack</button>
            </li>
            <li class="mr-2">
              <button class="inline-block px-4 py-3 rounded-lg hover:text-white"
                :class="{ 'text-blue-200 bg-blue-200 bg-opacity-10': activeTab === 2 }" @click="activeTab = 2">Tools</button>
            </li>
          </ul>
        </div>
        <div v-show="activeTab === 1">
          <div class="grid grid-cols-2 gap-4 pb-32 md:grid-cols-3 md:gap-8 xl:grid-cols-4 xl:gap-10 2xl:gap-12">
            <div v-for="item in tech" :key="item.id">
              <div
                class="item-tech flex cursor-pointer items-center gap-2 rounded border border-blue-200 px-2 py-2 hover:bg-blue-200 hover:bg-opacity-10 md:gap-3 lg:px-3">
                <div class="flex h-12 w-12 items-center justify-center p-0 lg:h-16 lg:w-16 lg:p-2 zoom-in">
                  <img alt="HTML" loading="lazy" width="32" height="32" decoding="async" data-nimg="1"
                    class="img-tech drop-shadow-xl transition-all duration-300 h-[65%] w-[65%] lg:h-[85%] lg:w-[85%]  "
                    :src="item.imageUrl" style="color: transparent;">
                </div>
                <div class="flex items-center text-sm md:text-base lg:text-lg">
                  <div class="tech font-medium text-secondary transition-all duration-300 translate-y-0 ">{{ item.name }}
                  </div>
                  <div
                    class="status-tech opacity-0 absolute mt-5 text-[10px] text-blue-200 transition-all duration-300 md:text-xs lg:text-sm">
                    {{ item.status }}</div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div v-show="activeTab === 2">
          <div class="grid grid-cols-2 gap-4 pb-32 md:grid-cols-3 md:gap-8 xl:grid-cols-4 xl:gap-10 2xl:gap-12">
            <div v-for="item in tools" :key="item.id">
              <div
                class="item-tech flex cursor-pointer items-center gap-2 rounded border border-blue-200 px-2 py-2 hover:bg-blue-200 hover:bg-opacity-10 md:gap-3 lg:px-3">
                <div class="flex h-12 w-12 items-center justify-center p-0 lg:h-16 lg:w-16 lg:p-2 zoom-in">
                  <img alt="HTML" loading="lazy" width="32" height="32" decoding="async" data-nimg="1"
                    class="img-tech drop-shadow-xl transition-all duration-300 h-[65%] w-[65%] lg:h-[85%] lg:w-[85%]  "
                    :src="item.imageUrl" style="color: transparent;">
                </div>
                <div class="flex items-center text-sm md:text-base lg:text-lg">
                  <div class="tech font-medium text-secondary transition-all duration-300 translate-y-0 ">{{ item.name }}
                  </div>
                  <div
                    class="status-tech opacity-0 absolute mt-5 text-[10px] text-blue-200 transition-all duration-300 md:text-xs lg:text-sm">
                    {{ item.status }}</div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
    </article>
  </div>
</template>

<style>
.fadein-left {
  opacity: 0;
  animation: fadeInLeft 0.5s ease-out forwards;
}

@keyframes fadeInLeft {
  0% {
    opacity: 0;
    transform: translateX(100%);
  }

  100% {
    opacity: 1;
    transform: translateX(0);
  }
}

.fadeins-1 {
  animation-delay: 500ms;
}

.fadeins-2 {
  animation-delay: 800ms;
}

.img-tech,
.tech {
  transition: transform 0.3s ease;
}

.item-tech:hover .img-tech {
  transform: scale(1.3);
}

.item-tech:hover .tech {
  transform: translateY(-12px);
}

.item-tech:hover .status-tech {
  opacity: 1;
}
</style>
