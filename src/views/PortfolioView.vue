<template>
  <div class="px-5 py-5 md:px-12 md:py-10 text-left text-amber-50 mx-3">
    <article data-page="about">
      <header>
        <!-- Title Section -->
        <div class="text-2xl font-bold text-white mb-10 fadein-bot title-section flex items-center justify-center flex-col">
          <h4>Past Project Experience</h4>
          <h4 class="text-base font-normal text-transparent bg-clip-text bg-gradient-to-r from-slate-100 to-blue-300">
            Explore the projects I've worked on so far</h4>
        </div>

        <!-- Tabs -->
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

      <!-- Main Section -->
      <section>
        <div v-if="activeTab === 1">
          <!-- Project Content -->
          <div class="grid grid-cols-1 gap-4 pb-32 md:grid-cols-3 md:gap-3 xl:grid-cols-3 xl:gap-3 2xl:gap-5 fade-zoom-in">
            <!-- Project Cards -->
            <div v-for="item in items" :key="item.id">
              <div class="item-card flex flex-col items-center gap-2 rounded bg-[#1e1e1f] hover:bg-[#282828] border border-[#383838] rounded-xl text-amber-50 md:gap-3 px-5 py-5 lg:px-5 ">
                <!-- Image Section -->
                <div class="flex h-12 w-12 items-center justify-center p-0 h-full w-full lg:p-0 zoom-in">
                  <img alt="HTML" loading="lazy" decoding="async" data-nimg="1" class="drop-shadow-xl rounded rounded-xl"
                    :src="getImageUrl(item.imageUrl)">
                </div>
                <!-- Details Section -->
                <div class="w-full flex flex-col gap-2 items-center text-sm md:text-base lg:text-lg">
                  <div class="title-text font-medium text-secondary">{{ item.name }}</div>
                  <div class="w-full text-left text-[10px] text-[#c1c1c1] md:text-xs lg:text-sm">{{ item.status }}</div>
                  <div class="w-full mt-4 text-normal text-sm text-left text-blue-200">{{ item.tech }}</div>
                  <div class="w-full flex justify-end">
                    <div class="flex cursor-pointer items-end gap-2 text-primary">
                      <!-- GitHub Link -->
                      <a v-if="item.github !== 'null'" :href="item.github" target="_blank" rel="noreferrer" title="View github repository" class="transition-all hover:text-accent">
                        <svg stroke="currentColor" fill="none" stroke-width="2" viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round" height="16" width="16" xmlns="http://www.w3.org/2000/svg">
                          <path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"></path>
                        </svg>
                      </a>
                      <!-- Demo Link -->
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

        <!-- Certificate Content -->
        <div v-if="activeTab === 2">
          <div class="grid grid-cols-1 gap-4 pb-32 md:grid-cols-3 md:gap-3 xl:grid-cols-3 xl:gap-3 2xl:gap-5 fade-zoom-in">
            <div v-for="certificate in certificates" :key="certificate.id">
              <div class="item-card flex flex-col items-center gap-2 rounded bg-[#1e1e1f] hover:bg-[#282828] border border-[#383838] rounded-xl text-amber-50 md:gap-3 px-5 py-5 lg:px-5 ">
                <!-- Image Section -->
                <div class="flex h-12 w-12 items-center justify-center p-0 h-full w-full lg:p-0 zoom-in">
                  <img alt="HTML" loading="lazy" decoding="async" data-nimg="1" class="drop-shadow-xl rounded rounded-xl"
                    :src="getImageUrl(certificate.imageUrl)">
                </div>
                <!-- Details Section -->
                <div class="w-full flex flex-col gap-2 items-center text-sm md:text-base lg:text-lg">
                  <div class="title-text font-medium text-secondary">{{ certificate.name }}</div>
                  <div class="w-full text-left text-[10px] text-[#c1c1c1] md:text-xs lg:text-sm">{{ certificate.date }}</div>
                  <div class="w-full flex justify-end">
                    <div class="flex cursor-pointer items-end gap-2 text-primary">
                      <!-- Certificate Link -->
                      <a v-if="certificate.link !== 'null'" :href="certificate.link" target="_blank" rel="noreferrer" title="View certificate" class="transition-all hover:text-accent">
                        <svg stroke="currentColor" fill="none" stroke-width="2" viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round" height="18" width="18" xmlns="http://www.w3.org/2000/svg">
                          <path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"></path><polyline points="15 3 21 3 21 9"></polyline><line x1="10" y1="14" x2="21" y2="3"></line></svg>
                      </a>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Preloader -->
        <div v-if="isLoading" class="flex justify-center items-center h-full">
          <div class="loader ease-linear rounded-full border-4 border-t-4 border-gray-200 h-12 w-12 mb-4"></div>
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
          status: 'This project aims to analyze global air pollution data and group them into clusters based on air pollution characteristics using clustering methods. The data used includes various air pollution parameters such as AQI, CO concentration, ozone, NO2, and PM2.5. After conducting data exploration, correlation analysis, and data processing, clustering was performed using the KMeans method and utilizing dimensionality reduction with PCA. As a result, it was found that most cities have good air quality, but there are significant variations between countries and cities. By performing clustering and creating a visualization dashboard.',
          tech: 'ipynb, Google Looker Studio',
          github: 'https://github.com/yudhamyn/Global-Air-Pollution-Clustering',
          demo: 'https://lookerstudio.google.com/reporting/d33e3fa1-4b6b-408c-8e57-624eaf4f93ef'
        },
        {
          id: 2,
          name: 'Diabets Clasification',
          imageUrl: 'diabets',
          status: 'I built a diabetes prediction model using a dataset from the National Institute of Diabetes and Digestive and Kidney Diseases, with the goal of predicting whether a patient has diabetes based on several diagnostic measurements. After handling missing values, outliers, and feature engineering, I tested several models (including Logistic Regression, KNN, Decision Tree, Random Forest, SVC, XGBoost, Gradient Boosting, and LightGBM) using cross-validation. The best model based on the evaluation graph is LightGBM, which achieved high accuracy, precision, recall, and F1 score on the test data, with accuracy of 90.90%, precision of 83.13%, recall of 92.59%, and F1 score of 87.71% on the test data. This LightGBM model performed well in predicting diabetes based on several diagnostic measurements in patients.',
          tech: 'ipynb',
          github: 'https://github.com/yudhamyn/Diabetes-Prediction-Classification--Data-Science-Project-6-GreatEdu',
          demo: 'null'
        },
        {
          id: 3,
          name: 'RFM Online Retail',
          imageUrl: 'RFMonlineretail',
          status: 'This project aims to segment customers based on purchasing behavior using RFM (Recency, Frequency, Monetary) analysis. Through data exploration and clustering analysis, it was found that there are variations in customer purchasing patterns and preferences. This segmentation allows companies to understand more about customer behavior and devise more effective marketing strategies, such as customized loyalty programs and more targeted product offerings. In addition, segmentation analysis also provides insights into the demographic characteristics of customers, such as differences in product preferences based on demographic factors. Thus, this project contributes to improving understanding of customers and optimizing marketing strategies to achieve better business success.',
          tech: 'ipynb',
          github: 'https://github.com/yudhamyn/Clustering-Online-Retail-RFM-Data-Science-Project-V-GreatEdu',
          demo: 'null'
        },
        {
          id: 4,
          name: 'Project Data Scientist Home Credit Indonesia',
          imageUrl: 'HomeCredit',
          status: 'This project aims to predict client repayment ability on loan application data using various machine learning models such as Logistic Regression, Gaussian Naive Bayes, Decision Tree, Random Forest, K-Nearest Neighbors, and Neural Network. The process starts with preparing the data, including handling missing values, encoding categorical features, and converting negative values to positive values. After that, various ML models were trained and evaluated using accuracy metrics, and their important features were analyzed.The results show that the Random Forest model provides the best performance with high prediction accuracy.Using this model, this project can provide recommendations to lenders to determine more effective marketing strategies and provide insights into the factors that affect clients repayment ability.',
          tech: 'ipynb, PowerPoint',
          github: 'https://github.com/yudhamyn/HOME-CREDIT-Final-Task-Data-Scientist',
          demo: 'https://github.com/yudhamyn/HOME-CREDIT-Final-Task-Data-Scientist/blob/main/Final%20Task%20Yudha%20mulyana%20Home%20Credit%20Data%20Science.pdf'
        },
        {
          id: 5,
          name: 'Project Data Scientist Kalbe Nutritionals',
          imageUrl: 'kalbe',
          status: 'PThis project is a data analysis that aims to optimize marketing strategies and improve customer experience at a retail company. The process starts with the merging of several datasets that include customer, product, and store transaction information. Next, various data preprocessing steps are performed, such as data cleaning, data type adjustment, and checking data stationarity using the Augmented Dickey-Fuller test.In addition, time series regression analysis was conducted to forecast the number of sales.The results show that the ARIMA model with manual parameters (40,2,2) provides the best performance. In addition, a clustering analysis using the K-Means algorithm was conducted to identify customer behavior patterns. From the clustering results, four customer groups with different characteristics were found, which were then followed by recommendations for appropriate marketing strategies for each customer group to increase customer retention and sales, as well as creating a sales visualization dashboard using Tableau.',
          tech: 'ipynb, Tableau',
          github: 'https://github.com/rakha-elctrnx/muslim-companion',
          demo: 'https://github.com/yudhamyn/FinalTask-Kalbe-DataScientist-YudhaMulyana/blob/main/Kalbe%20Data%20Scientist.twbx'
        },
        {
          id: 6,
          name: 'NLP | Deteksi Sentimen Positif Negatif Bahasa Indonesia',
          imageUrl: 'deteksipositifnegatif',
          status: 'This project aims to perform sentiment analysis on texts in Indonesian using the BERT model. First, a BERT model for text sequence classification is prepared by tokenization using an Indonesian tokenizer and appropriate configuration. The model is then trained using the pre-processed SMSA Doc Sentiment Prose dataset. After training the model, it was evaluated using validation and testing datasets.The results show that the trained model is able to achieve good accuracy in classifying the sentiment on Indonesian text as either positive or negative.',
          tech: 'ipynb, pytorch, transformers',
          github: 'https://github.com/rakha-elctrnx/muslim-companion',
          demo: 'null'
        },
        {
          id: 7,
          name: 'Clustering Alasan Resign Karyawan',
          imageUrl: 'clusterkryawan',
          status: 'This project is a data analysis of possible patterns in employees resigning from the company. The process begins by preprocessing the data, including grouping the reasons for resignation into specific categories, filling in missing values, and converting categorical variables into numerical representations. Next, a clustering analysis is performed using the K-Means algorithm to group employees based on the identified patterns. Evaluation was conducted using the Elbow method to determine the optimal number of clusters, as well as inertia and silhouette score measurements to evaluate clustering performance. The clustering results are visualized using a two-dimensional scatter plot for easy interpretation.',
          tech: 'ipynb, PowerPoint',
          github: 'https://github.com/rakha-elctrnx/muslim-companion',
          demo: 'https://github.com/yudhamyn/TugasAkhirDataMining_Clustering_Alasan-Resign-Karyawan-Menggunakan-DataPrivate/blob/main/GUI%20STREAMLIT_PPT%20CRISP-DM_TUGAS%20AKHIR_YUDHA%20MULYANA_A11.2021.13857_442U/PPT%20Resign.pdf'
        },
        {
          id: 7,
          name: 'Prediksi Kelulusan Mahasiswa',
          imageUrl: 'prediksikelulusan',
          status: 'This project is the use of the K-Nearest Neighbors (KNN) algorithm to predict whether a student will graduate on time based on their grade point average (GPA). The data has been prepared and cleaned by converting the "Yes" and "No" labels in the "exact" column into binary values (-1 for "No" and 1 for "Yes"). After dividing the data into training and test data, the KNN model was trained using the training data and then tested with the test data. The accuracy result of the model reached about 87.32%. Users can also input a new IP value to predict whether the student will graduate on time.',
          tech: 'ipynb',
          github: 'https://github.com/yudhamyn/DataMining_klasifikasi-kelulusan_tepat-atau-tidak/blob/main/Yudha_Prediksi_lulus_tepat_waktu.ipynb',
          demo: 'null'
        },
        {
          id: 8,
          name: 'Bank Churn Prediction',
          imageUrl: 'Bankchurn',
          status: 'After performing feature engineering and data encoding to improve the quality and representation of features in bank customer churn prediction, various machine learning models were tested for best performance. The tested models include Logistic Regression, Random Forest, Gradient Boosting, XGBoost, and LightGBM. After applying a comprehensive hyperparameter tuning technique, the XGBoost model performed best with an accuracy of 87% and a recall of 52% for the positive class, demonstrating its ability to identify customers who may churn. The Random Forest and LightGBM models also provided competitive results with accuracies of around 86% and 87% respectively, although the combination of precision and recall was not as optimal as XGBoost. The Gradient Boosting and Logistic Regression models performed slightly lower than the others. In terms of the balance between precision and recall, tuned XGBoost is identified as the most effective model for predicting churn in this dataset, as it is able to provide more accurate and reliable predictions, making it the best choice to be implemented in churn mitigation strategies in banks.',
          tech: 'ipynb',
          github: 'https://github.com/yudhamyn/Banking-Churn-Prediction-Data-Science-Project-IV-GreatEdu/blob/main/Tugas_Mandiri_Data_Science_Project_4_Yudha_Mulyana.ipynb',
          demo: 'null'
        }
	],
      certificates: [
      { id: 1,
          name: 'IBM Data Science Professional Certificate', 
          date: 'Issued Jul 2024', 
          imageUrl: 'IBMDataScience', 
          link: 'https://coursera.org/share/3c579561c9b4a6b5418d433864a05f3d',
        },
        { id: 2,
          name: 'Google Data Analytics Professional Certificate', 
          date: 'Issued May 2024', 
          imageUrl: 'GOOGLEDATAANALYTICS', 
          link: 'https://coursera.org/share/fca6c4f5bd51f9ead1708b545ed5f121',
        },
        { id: 3,
          name: 'Data Visualization with Python', 
          date: 'Issued Jun 2024', 
          imageUrl: 'Data Visualization with Python', 
          link: 'https://coursera.org/share/c411a217e2eef8c39e2ecd4b396f24ca',
        },
        { id: 4,
          name: 'Data Analysis with Python', 
          date: 'Issued Jun 2024', 
          imageUrl: 'Data Analysis with Python', 
          link: 'https://coursera.org/share/68f58cc7f865229a08c15641250d5080',
        },
        { id: 5,
          name: 'Basic Proficiency in KNIME Analytics', 
          date: 'Issued May 2024', 
          imageUrl: 'sertifikatknime', 
          link: 'https://www.credly.com/badges/8a43c57c-1805-4202-88ae-80139a69253a',
        },
        { id: 6,
          name: 'Database and SQL for Data Science with Python', 
          date: 'Issued Mar 2024', 
          imageUrl: 'Database and SQL for Data Science with Python', 
          link: 'https://coursera.org/share/57edc80cdeb4a52ddb140a3389d34a81',
        },
        { id: 7,
          name: ' Python Project for Data Science', 
          date: 'Issued Feb 2024', 
          imageUrl: 'Python Project for Data Science', 
          link: 'https://coursera.org/share/6ba3030419ec4e3455c0aa8ce628dfa5',
        },
        { id: 8,
          name: 'Python for Data Science, AI & Development', 
          date: 'Issued Dec 2024', 
          imageUrl: 'Python for Data Science, AI & Development', 
          link: 'https://coursera.org/share/35482df6bb12575ee70f4af2d19cc174',
        },
        { id: 9,
          name: 'Bootcamp Microsoft Office Excel Specialist', 
          date: 'Issued Dec 2024', 
          imageUrl: 'Bootcamp Microsoft Office Excel Specialist', 
          link: 'https://drive.google.com/file/d/1nibDgatK5UXSDPjGlG785g2mTJGyWON4/view',
        },
        { id: 10,
          name: 'Data Science Methodology', 
          date: 'Issued Nov 2024', 
          imageUrl: 'Data Science Methodology', 
          link: 'https://coursera.org/share/099622ceca3bb01c1a8c195043f2529a',
        },
        { id: 11,
          name: 'Tools for Data Science', 
          date: 'Issued Oct 2024',
          imageUrl: 'Tools for Data Science',
          link: 'https://coursera.org/share/0cbf91a20b08eedbb1f90012b1e0e601',
        },
        { id: 12,
          name: 'Certificate of Competencies - Kalbe Nutritionals Data Science Virtual Internship Experience Program', 
          date: 'Issued Sep 2024', 
          imageUrl: 'sertifikatkalbe', 
          link: 'https://www.linkedin.com/in/yudha-mulyana/details/certifications/1635542870676/single-media-viewer/?profileId=ACoAADdWofsBjo-DHKqqULGPXCfoeMs0t4im0vw',
        },
        { id: 13,
          name: 'What is Data Science?', 
          date: 'Issued Aug 2024', 
          imageUrl: 'What is Data Science', 
          link: 'https://coursera.org/share/e29d8d2f79fc4f958ca47521c8af1307',
        }
      ],
      isLoading: false
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
@media (max-width: 640px) {
  .tabs button.active-tab {
    background: #24c9fb;
    color: #1e1e1f;
    font-weight: bold;
  }

  .tabs button {
    color: #c1c1c1;
    background: #1e1e1f;
    border: 1px solid #383838;
  }

  .tabs button:hover {
    color: #ffffff;
    background: #282828;
  }
}

</style>



