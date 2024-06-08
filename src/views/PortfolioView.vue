<template>
  <div class="px-5 py-5 md:px-12 md:py-10 text-left text-amber-50 mx-3">
    <article data-page="about">
      <header>
        <div class="text-2xl font-bold text-white mb-10 fadein-bot title-section flex items-center justify-center flex-col">
          <h4>Past Project Experience</h4>
          <h4 class="text-base font-normal text-transparent bg-clip-text bg-gradient-to-r from-slate-100 to-blue-300">
            Explore the projects I've worked on so far</h4>
        </div>
        <div class="tabs flex justify-center gap-4 mb-8">
          <button 
            @click="activeTab = 1"
            :class="{'active-tab': activeTab === 1}">
            Projects
          </button>
          <button 
            @click="activeTab = 2"
            :class="{'active-tab': activeTab === 2}">
            Certificates
          </button>
        </div>

      </header>
      <section>
        <div v-if="activeTab === 1">
          <div class="grid grid-cols-1 gap-4 pb-32 md:grid-cols-3 md:gap-3 xl:grid-cols-3 xl:gap-3 2xl:gap-5 fade-zoom-in">
            <div v-for="item in items" :key="item.id">
              <div class="item-card flex flex-col items-center gap-2 rounded bg-[#1e1e1f] hover:bg-[#282828] border border-[#383838] rounded-xl text-amber-50 md:gap-3 px-5 py-5 lg:px-5 ">
                <div class="flex h-12 w-12 items-center justify-center p-0 h-full w-full lg:p-0 zoom-in">
                  <img alt="HTML" loading="lazy" decoding="async" data-nimg="1" class="drop-shadow-xl rounded rounded-xl"
                    :src="getImageUrl(item.imageUrl)">
                </div>
                <div class="w-full flex flex-col gap-2 items-center text-sm md:text-base lg:text-lg">
                  <div class="title-text font-medium text-secondary">{{ item.name }}</div>
                  <div class="w-full text-left text-[10px] text-[#c1c1c1] md:text-xs lg:text-sm">{{ item.status }}</div>
                  <div class="w-full mt-4 text-normal text-sm text-left text-blue-200">{{ item.tech }}</div>
                  <div class="w-full flex justify-end">
                    <div class="flex cursor-pointer items-end gap-2 text-primary">
                      <a v-if="item.github !== 'null'" :href="item.github" target="_blank" rel="noreferrer" title="View github repository" class="transition-all hover:text-accent">
                        <svg stroke="currentColor" fill="none" stroke-width="2" viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round" height="16" width="16" xmlns="http://www.w3.org/2000/svg">
                          <path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"></path>
                        </svg>
                      </a>
                      <a v-if="item.demo !== 'null'" :href="item.demo" target="_blank" rel="noreferrer" title="View finished project" class="transition-all hover:text-accent">
                        <svg stroke="currentColor" fill="none" stroke-width="2" viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round" height="18" width="18" xmlns="http://www.w3.org/2000/svg">
                          <path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"></path>
                          <polyline points="15 3 21 3 21 9"></polyline>
                          <line x1="10" y1="14" x2="21" y2="3"></line>
                        </svg>
                      </a>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div v-if="activeTab === 2">
          <div class="grid grid-cols-1 gap-4 pb-32 md:grid-cols-3 md:gap-3 xl:grid-cols-3 xl:gap-3 2xl:gap-5 fade-zoom-in">
            <div v-for="certificate in certificates" :key="certificate.id">
              <div class="item-card flex flex-col items-center gap-2 rounded bg-[#1e1e1f] hover:bg-[#282828] border border-[#383838] rounded-xl text-amber-50 md:gap-3 px-5 py-5 lg:px-5 ">
                <div class="flex h-12 w-12 items-center justify-center p-0 h-full w-full lg:p-0 zoom-in">
                  <img alt="HTML" loading="lazy" decoding="async" data-nimg="1" class="drop-shadow-xl rounded rounded-xl"
                    :src="getImageUrl(certificate.imageUrl)">
                </div>
                <div class="w-full flex flex-col gap-2 items-center text-sm md:text-base lg:text-lg">
                  <div class="title-text font-medium text-secondary">{{ certificate.name }}</div>
                  <div class="w-full text-left text-[10px] text-[#c1c1c1] md:text-xs lg:text-sm">{{ certificate.date }}</div>
                  <div class="w-full flex justify-end">
                    <div class="flex cursor-pointer items-end gap-2 text-primary">
                      <a v-if="certificate.link !== 'null'" :href="certificate.link" target="_blank" rel="noreferrer" title="View certificate" class="transition-all hover:text-accent">
                        <svg data-v-454f6c7a="" stroke="currentColor" fill="none" stroke-width="2" viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round" height="18" width="18" xmlns="http://www.w3.org/2000/svg">
                          <path data-v-454f6c7a="" d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"></path><polyline data-v-454f6c7a="" points="15 3 21 3 21 9"></polyline><line data-v-454f6c7a="" x1="10" y1="14" x2="21" y2="3"></line></svg>
                      </a>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
    </article>
  </div>
</template>

<script>
export default {
  data() {
    return {
      activeTab: 1,
      items: [
        {
          id: 1,
          name: 'Clustering Global Air Pollution Data',
          imageUrl: 'clustering',
          status: 'Project ini bertujuan untuk menganalisis data polusi udara global dan mengelompokkannya ke dalam klaster berdasarkan karakteristik polusi udara menggunakan metode klasterisasi. Data yang digunakan mencakup berbagai parameter polusi udara seperti AQI, konsentrasi CO, ozon, NO2, dan PM2.5. Setelah melakukan eksplorasi data, analisis korelasi, dan pemrosesan data, klasterisasi dilakukan dengan menggunakan metode KMeans dan memanfaatkan reduksi dimensi dengan PCA. Hasilnya, ditemukan bahwa sebagian besar kota memiliki kualitas udara yang baik, namun ada variasi yang signifikan antar negara dan kota. Dengan melakukan klasterisasi dan membuat dashboard visualisasinya.',
          tech: 'ipynb, Google Looker Studio',
          github: 'https://github.com/yudhamyn/Global-Air-Pollution-Clustering',
          demo: 'https://lookerstudio.google.com/reporting/d33e3fa1-4b6b-408c-8e57-624eaf4f93ef'
        },
        {
          id: 2,
          name: 'Diabets Clasification',
          imageUrl: 'diabets',
          status: 'Saya membangun model prediksi diabetes menggunakan dataset dari National Institute of Diabetes and Digestive and Kidney Diseases, dengan tujuan memprediksi apakah seorang pasien memiliki diabetes berdasarkan beberapa pengukuran diagnostik. Setelah menangani nilai hilang, outlier, dan rekayasa fitur, saya menguji beberapa model (termasuk Logistic Regression, KNN, Decision Tree, Random Forest, SVC, XGBoost, Gradient Boosting, dan LightGBM) menggunakan cross-validation. Model terbaik berdasarkan grafik evaluasi adalah LightGBM, yang mencapai akurasi, presisi, recall, dan F1 score yang tinggi pada data uji, dengan akurasi sebesar 90.90%, presisi 83.13%, recall 92.59%, dan F1 score 87.71% pada data uji. Model LightGBM ini memiliki performa yang baik dalam memprediksi diabetes berdasarkan beberapa pengukuran diagnostik pada pasien.',
          tech: 'ipynb',
          github: 'https://github.com/yudhamyn/Diabetes-Prediction-Classification--Data-Science-Project-6-GreatEdu',
          demo: 'null'
        },
        {
          id: 3,
          name: 'RFM Online Retail',
          imageUrl: 'RFMonlineretail',
          status: 'Projek ini bertujuan untuk melakukan segmentasi pelanggan berdasarkan perilaku pembelian menggunakan metode RFM (Recency, Frequency, Monetary) analysis. Melalui eksplorasi data dan analisis clustering, ditemukan bahwa terdapat variasi dalam pola pembelian dan preferensi pelanggan. Segmentasi ini memungkinkan perusahaan untuk memahami lebih dalam tentang perilaku pelanggan dan menyusun strategi pemasaran yang lebih efektif, seperti program loyalitas yang disesuaikan dan penawaran produk yang lebih tepat sasaran. Selain itu, analisis segmentasi juga memberikan wawasan tentang karakteristik demografis pelanggan, seperti perbedaan preferensi produk berdasarkan faktor demografis. Dengan demikian, proyek ini memberikan kontribusi dalam meningkatkan pemahaman tentang pelanggan dan mengoptimalkan strategi pemasaran untuk mencapai keberhasilan bisnis yang lebih baik.',
          tech: 'ipynb',
          github: 'https://github.com/yudhamyn/Clustering-Online-Retail-RFM-Data-Science-Project-V-GreatEdu',
          demo: 'null'
        },
        {
          id: 4,
          name: 'Project Data Scientist Home Credit Indonesia',
          imageUrl: 'HomeCredit',
          status: 'Projek ini bertujuan untuk memprediksi kemampuan pembayaran klien pada data aplikasi pinjaman dengan menggunakan berbagai model machine learning seperti Logistic Regression, Gaussian Naive Bayes, Decision Tree, Random Forest, K-Nearest Neighbors, dan Neural Network. Proses dimulai dengan mempersiapkan data, termasuk menangani nilai yang hilang, mengkodekan fitur kategorikal, dan mengonversi nilai negatif menjadi nilai positif. Setelah itu, berbagai model ML dilatih dan dievaluasi menggunakan metrik akurasi, serta dianalisis fitur pentingnya. Hasilnya menunjukkan bahwa model Random Forest memberikan kinerja terbaik dengan akurasi prediksi yang tinggi. Dengan menggunakan model ini, proyek ini dapat memberikan rekomendasi kepada penyedia pinjaman untuk menentukan strategi pemasaran yang lebih efektif dan memberikan wawasan tentang faktor-faktor yang mempengaruhi kemampuan pembayaran klien.',
          tech: 'ipynb, PowerPoint',
          github: 'https://github.com/yudhamyn/HOME-CREDIT-Final-Task-Data-Scientist',
          demo: 'https://github.com/yudhamyn/HOME-CREDIT-Final-Task-Data-Scientist/blob/main/Final%20Task%20Yudha%20mulyana%20Home%20Credit%20Data%20Science.pdf'
        },
        {
          id: 5,
          name: 'Project Data Scientist Kalbe Nutritionals',
          imageUrl: 'kalbe',
          status: 'Project ini merupakan sebuah analisis data yang bertujuan untuk mengoptimalkan strategi pemasaran dan meningkatkan pengalaman pelanggan pada sebuah perusahaan ritel. Proses dimulai dengan penggabungan beberapa dataset yang mencakup informasi transaksi pelanggan, produk, dan toko. Selanjutnya, dilakukan berbagai tahap preprocessing data, seperti pembersihan data, penyesuaian tipe data, dan pengecekan stasioneritas data menggunakan uji Augmented Dickey-Fuller. Selain itu, dilakukan analisis regresi time series untuk meramalkan jumlah penjualan. Hasilnya menunjukkan bahwa model ARIMA dengan parameter manual (40,2,2) memberikan performa terbaik. Selain itu, dilakukan analisis clustering menggunakan algoritma K-Means untuk mengidentifikasi pola perilaku pelanggan. Dari hasil clustering tersebut, ditemukan empat kelompok pelanggan dengan karakteristik yang berbeda, yang kemudian diikuti dengan rekomendasi strategi pemasaran yang sesuai untuk setiap kelompok pelanggan guna meningkatkan retensi pelanggan dan penjualan erta membuat dashboard visualisasi penjualan menggunakan Tableau.',
          tech: 'ipynb, Tableau',
          github: 'https://github.com/rakha-elctrnx/muslim-companion',
          demo: 'https://github.com/yudhamyn/FinalTask-Kalbe-DataScientist-YudhaMulyana/blob/main/Kalbe%20Data%20Scientist.twbx'
        },
        {
          id: 6,
          name: 'NLP | Deteksi Sentimen Positif Negatif Bahasa Indonesia',
          imageUrl: 'deteksipositifnegatif',
          status: 'Proyek ini bertujuan untuk melakukan analisis sentimen pada teks dalam bahasa Indonesia menggunakan model BERT. Pertama, model BERT untuk klasifikasi urutan teks dipersiapkan dengan tokenisasi menggunakan tokenizer Bahasa Indonesia dan konfigurasi yang sesuai. Model ini kemudian dilatih menggunakan dataset SMSA Doc Sentiment Prosa yang telah diproses sebelumnya. Setelah melatih model, dilakukan evaluasi menggunakan dataset validasi dan testing. Hasilnya menunjukkan bahwa model yang dilatih mampu mencapai akurasi yang baik dalam mengklasifikasikan sentimen pada teks Bahasa Indonesia apakah positif atau negatif.',
          tech: 'ipynb, pytorch, transformers',
          github: 'https://github.com/rakha-elctrnx/muslim-companion',
          demo: 'null'
        },
        {
          id: 7,
          name: 'Clustering Alasan Resign Karyawan',
          imageUrl: 'clusterkryawan',
          status: 'Project ini merupakan analisis data terhadap pola-pola yang mungkin terjadi pada karyawan yang mengundurkan diri dari perusahaan. Proses dimulai dengan melakukan preprocessing data, termasuk mengelompokkan alasan resign menjadi kategori-kategori tertentu, mengisi nilai yang hilang, dan mengubah variabel kategorikal menjadi representasi numerik. Selanjutnya, dilakukan analisis clustering menggunakan algoritma K-Means untuk mengelompokkan karyawan berdasarkan pola-pola yang teridentifikasi. Evaluasi dilakukan menggunakan metode Elbow untuk menentukan jumlah klaster yang optimal, serta pengukuran inertia dan silhouette score untuk mengevaluasi performa klasterisasi. Hasil klasterisasi divisualisasikan menggunakan scatter plot dua dimensi untuk memudahkan interpretasi.',
          tech: 'ipynb, PowerPoint',
          github: 'https://github.com/rakha-elctrnx/muslim-companion',
          demo: 'https://github.com/yudhamyn/TugasAkhirDataMining_Clustering_Alasan-Resign-Karyawan-Menggunakan-DataPrivate/blob/main/GUI%20STREAMLIT_PPT%20CRISP-DM_TUGAS%20AKHIR_YUDHA%20MULYANA_A11.2021.13857_442U/PPT%20Resign.pdf'
        },
        {
          id: 7,
          name: 'Prediksi Kelulusan Mahasiswa',
          imageUrl: 'prediksikelulusan',
          status: 'Proyek ini merupakan penggunaan algoritma K-Nearest Neighbors (KNN) untuk memprediksi apakah seorang mahasiswa akan lulus tepat waktu berdasarkan nilai indeks prestasi (IP) mereka. Data tersebut telah disiapkan dan dibersihkan dengan mengubah label "Ya" dan "Tidak" pada kolom "tepat" menjadi nilai biner (-1 untuk "Tidak" dan 1 untuk "Ya"). Setelah membagi data menjadi data latih dan data uji, model KNN dilatih dengan menggunakan data latih dan kemudian diuji dengan data uji. Hasil akurasi model mencapai sekitar 87.32%. Pengguna juga dapat memasukkan nilai IP baru untuk melakukan prediksi apakah mahasiswa tersebut akan lulus tepat waktu.',
          tech: 'ipynb',
          github: 'https://github.com/yudhamyn/DataMining_klasifikasi-kelulusan_tepat-atau-tidak/blob/main/Yudha_Prediksi_lulus_tepat_waktu.ipynb',
          demo: 'null'
        },
        {
          id: 8,
          name: 'Bank Churn Prediction',
          imageUrl: 'Bankchurn',
          status: 'Setelah melakukan feature engineering dan encoding data untuk meningkatkan kualitas dan representasi fitur dalam prediksi churn pelanggan bank, berbagai model machine learning diuji untuk kinerja terbaik. Model-model yang diuji meliputi Logistic Regression, Random Forest, Gradient Boosting, XGBoost, dan LightGBM. Setelah menerapkan teknik tuning hyperparameter yang komprehensif, model XGBoost menunjukkan performa terbaik dengan akurasi mencapai 87% dan recall 52% untuk kelas positif, menunjukkan kemampuannya dalam mengidentifikasi pelanggan yang mungkin churn. Model Random Forest dan LightGBM juga memberikan hasil kompetitif dengan akurasi masing-masing sekitar 86% dan 87%, meskipun kombinasi precision dan recall tidak seoptimal XGBoost. Model Gradient Boosting dan Logistic Regression memiliki performa sedikit lebih rendah dibandingkan yang lainnya. Dalam hal keseimbangan antara precision dan recall, tuned XGBoost diidentifikasi sebagai model paling efektif untuk memprediksi churn dalam dataset ini, karena mampu memberikan prediksi yang lebih akurat dan andal, menjadikannya pilihan terbaik untuk diimplementasikan dalam strategi mitigasi churn di bank.',
          tech: 'ipynb',
          github: 'https://github.com/yudhamyn/Banking-Churn-Prediction-Data-Science-Project-IV-GreatEdu/blob/main/Tugas_Mandiri_Data_Science_Project_4_Yudha_Mulyana.ipynb',
          demo: 'null'
        }
	],
      certificates: [
        { id: 1,
          name: 'GOOGLE DATA ANALYTICS', 
          date: 'Issued May 2024', 
          imageUrl: 'GOOGLEDATAANALYTICS', 
          link: 'https://coursera.org/share/fca6c4f5bd51f9ead1708b545ed5f121',
        },
        { id: 2,
          name: 'Data Visualization with Python', 
          date: 'Issued Jun 2024', 
          imageUrl: 'Data Visualization with Python', 
          link: 'https://coursera.org/share/c411a217e2eef8c39e2ecd4b396f24ca',
        },
        { id: 3,
          name: 'Data Analysis with Python', 
          date: 'Issued Jun 2024', 
          imageUrl: 'Data Analysis with Python', 
          link: 'https://coursera.org/share/68f58cc7f865229a08c15641250d5080',
        },
        { id: 4,
          name: 'Basic Proficiency in KNIME Analytics', 
          date: 'Issued May 2024', 
          imageUrl: 'sertifikatknime', 
          link: 'https://www.credly.com/badges/8a43c57c-1805-4202-88ae-80139a69253a',
        },
        { id: 5,
          name: 'Database and SQL for Data Science with Python', 
          date: 'Issued Mar 2024', 
          imageUrl: 'Database and SQL for Data Science with Python', 
          link: 'https://coursera.org/share/57edc80cdeb4a52ddb140a3389d34a81',
        },
        { id: 6,
          name: ' Python Project for Data Science', 
          date: 'Issued Feb 2024', 
          imageUrl: 'Python Project for Data Science', 
          link: 'https://coursera.org/share/6ba3030419ec4e3455c0aa8ce628dfa5',
        },
        { id: 7,
          name: 'Python for Data Science, AI & Development', 
          date: 'Issued Dec 2024', 
          imageUrl: 'Python for Data Science, AI & Development', 
          link: 'https://coursera.org/share/35482df6bb12575ee70f4af2d19cc174',
        },
        { id: 8,
          name: 'Bootcamp Microsoft Office Excel Specialist', 
          date: 'Issued Dec 2024', 
          imageUrl: 'Bootcamp Microsoft Office Excel Specialist', 
          link: 'https://drive.google.com/file/d/1nibDgatK5UXSDPjGlG785g2mTJGyWON4/view',
        },
        { id: 9,
          name: 'Data Science Methodology', 
          date: 'Issued Nov 2024', 
          imageUrl: 'Data Science Methodology', 
          link: 'https://coursera.org/share/099622ceca3bb01c1a8c195043f2529a',
        },
        { id: 10,
          name: 'Tools for Data Science', 
          date: 'Issued Oct 2024',
          imageUrl: 'Tools for Data Science',
          link: 'https://coursera.org/share/0cbf91a20b08eedbb1f90012b1e0e601',
        },
        { id: 11,
          name: 'Certificate of Competencies - Kalbe Nutritionals Data Science Virtual Internship Experience Program', 
          date: 'Issued Sep 2024', 
          imageUrl: 'sertifikatkalbe', 
          link: 'https://www.linkedin.com/in/yudha-mulyana/details/certifications/1635542870676/single-media-viewer/?profileId=ACoAADdWofsBjo-DHKqqULGPXCfoeMs0t4im0vw',
        },
        { id: 12,
          name: 'What is Data Science?', 
          date: 'Issued Aug 2024', 
          imageUrl: 'What is Data Science', 
          link: 'https://coursera.org/share/e29d8d2f79fc4f958ca47521c8af1307',
        }
      ],
    };
  },
   methods: {
    getImageUrl(imageUrl) {
      const supportedFormats = ['jpg', 'png', 'gif'];
      for (let format of supportedFormats) {
        let fullPath = `/portofolio/img/${imageUrl}.${format}`;
        if (this.imageExists(fullPath)) {
          return fullPath;
        }
      }
      return ''; // or a default image path if no image is found
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
.tabs button {
  padding: 0.5rem 1rem;
  background: #1e1e1f;
  border: 1px solid #383838;
  border-radius: 0.375rem;
  color: #c1c1c1;
  cursor: pointer;
  transition: background 0.3s, color 0.3s;
}

.tabs button:hover {
  background: #282828;
  color: #ffffff;
}

.tabs .active-tab {
  background: #00f9ff;
  color: #1e1e1f;
  font-weight: bold;
}

.item-card {
  transition: transform 0.3s, box-shadow 0.3s;
}

.item-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
}

.item-card:hover {
  transition: transform 0.3s ease;
  transform: translateY(-8px);
}
svg:hover{
  stroke: #00f9ff;
}
@keyframes fadeZoomIn {
  0% {
    opacity: 0;
    transform: scale(0.5);
  }
   100% {
    opacity: 1;
    transform: scale(1);
  }
}
.fade-zoom-in {
  animation: fadeZoomIn 1s ease-in-out;
}
.tabs button {
  background: none;
  border: none;
  padding: 10px 20px;
  cursor: pointer;
  transition: color 0.3s ease;
}

.tabs button:hover {
  color: #00aaff;
}

.tabs button.text-white.border-b-2.border-blue-300 {
  color: #00aaff;
}
</style>
