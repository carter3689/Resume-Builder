
<template>
  <main class="container">
    <div id="resume" class="d-flex">
      <div class="left-col">
        <div class="resume-section">
          <!--v-bind can be shorthanded with :src-->
          <img
            v-bind:src="imageUrl"
            class="profile-pic"
            alt="Profile Picture for Resume"
          />
          <h4 class="section-headline">
            {{ headlines[0] }}
          </h4>
          <div>
            {{ introText }}
          </div>
          <h4 class="section-headline">
            {{ headlines[1] }}
          </h4>

          <!-- <input type="text" v-model="headlines[0]"> this won't work because an input can not wrap text
            Instead we can use contenteditable="true"
          --> 

          <ul>
            <!--Read up more about v-bind and maintaining state with key:
            https://vuejs.org/guide/essentials/list.html#maintaining-state-with-key
           -->
            <li v-for="(contact, key) in contact" :key="key">
              {{ contact }}
            </li>
          </ul>

          <h4 class="section-headline">
            {{ headlines[2] }}
          </h4>
          <ul>
            <!--Don't add v-for to parent node JUST to child node(s) or the in other words
            The place you want to repeat
          -->
            <li v-for="skill in skills" :key="skill.id">{{ skill }}</li>
          </ul>

          <h4 class="section-headline">
            {{ headlines[3] }}
          </h4>
          <ul>
            <li>Natural Language Processing with Python(Coursera)</li>
            <li>Recommendation Systems with TensorFlow on GCP(Google)</li>
          </ul>
        </div>
      </div>

      <div class="right-col">
        <div class="resume-section">
          <div class="personal-name">
            {{ name }}
          </div>
          <div class="personal-title">
            {{ title }}
          </div>

          <h4 class="section-headline">
            {{ headlines[4] }}
          </h4>
          <div v-for="(item, index) in experience" :key="index" class="inner-section">
            <div>
              {{ item.title }}
            </div>
            <div class="d-flex justify-content-between">
              <div>{{ item.company }}, {{ item.location }}</div>
              <div>{{ item.date }}</div>
            </div>
            <ul>
              <li v-for="(desc, innerIndex) in item.description" :key="innerIndex">
                {{ desc }}
              </li>
            </ul>
          </div>

          <h4 class="section-headline">
            {{ headlines[5] }}
          </h4>
          <div v-for="(item, index) in education" :key="index">
            <div>
              {{ item.title }}
            </div>
            <div class="d-flex justify-content-between">
              <div> {{ item.university }}, {{ item.location }}</div>
              <div>{{  item.date }}</div>
            </div>
            <ul>
              <li v-for="(desc, innerIndex) in item.description" :key="innerIndex" >
                {{ desc }}
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
    </main>
</template>

<script>
  export default {
    data() {
      return {
        name: "Joel Carter",
        title: "Data Scientist",
        introText: "From data cleaning to data anaylsis to machine learning, I am passionate about everything data.",
        imageUrl: "./profileimage.jpg",
        headlines: ["About Me", "Contact", "Skills", "Certifications", "Experience", "Education"],
        contact: {
          phone: "708-555-4490",
          email: "carter3689@gmail.com",
          address: "Main St 100, 19777 NY"
        },
        skills: [
          "Python",
          "Pandas",
          "SQL",
          "R",
          "Machine Learning",
          "Natural Language Processing",
          "Recommendation Systems"
      ],
      experience: [
        {
          title:"Software Engineer",
          company: "ABC Company",
          location: "Chicago,IL",
          date: "2023-Present",
          description: ["Worked on a team of engineers to create XYZ product.", 
          "Designed and implemented a recommendation system that boosted cross-selling, leading to a 20% increase in revenue."],
        },
        {
          title: "Data Scientist",
          company: "XYZ Data Solutions",
          location: "London",
          date: "2017 - 2019",
          description: [
            "Developed and deployed machine learning models for fraud detection, reducing fraudulent transactions by 18%",
            "Conducted in-depth exploratory data analysis to identify key trends and insights",
            "Worked on data preprocessing, feature engineering, and model selection to improve model performance"
        ]
      },
          {
        title: "Data Scientist Trainee",
        company: "Data Insights Ltd.",
        location: "New York City",
        date: "2016-2017",
        description: [
          "Collaborated with external partners to integrate third-party data sources, expanding the company's data assets and enhancing predictive modeling capabilities.",
          "Presented data-driven insights and recommendations to executive leadership, influencing strategic decisions and driving revenue growth."
        ]
      }
      ],
      education: [
        {
          title: "Master of Science in Data Science",
          university: "StellarTech University",
          location: "Starville",
          date: "2020-2022",
          description: [
            "Coursework included advanced machine learning, statistical modeling, and data visualization techniques.",
            "Thesis: 'Predictive Modeling for Customer Churn in E-commerce using Random Forest.'"
          ]
        },
        {
          title: "Bachelor of Science in Computer Science",
          university: "Evergreen State University",
          location: "Springdale",
          date: "2012-2015",
          description: [
            "Relevant coursework in database management, algorithms, and programming languages.",
            "Senior project: 'Development of a Recommender System for Movie Ratings.'"
          ]
        }
      ]
    }
  }
}
</script>

<style scoped>

#resume {
  box-shadow: rgba(50, 50, 93, 0.25) 0px 13px 27px -5px, rgba(0, 0, 0, 0.3) 0px 8px 16px -8px;
  /* DIN A4 standard paper size. commonly used for resumes
  For North America letter size use width: 8.5in; height: 11in; */
  height: 297mm;
  width: 210mm;
}

.inner-section{
  margin-bottom: 20px;
}

.section-headline {
  font-size: 20px;
  font-weight: var(--headline-weight);
  margin-bottom: 15px;
  margin-top: 0;
}

.right-col .section-headline {
  color: var(--highlight-color-right);
}

.left-col .section-headline {
  border-bottom: 1px solid var(--highlight-color-left);
  padding-bottom: 5px;
  margin-right: -30px;
  padding-right: 10px;
  color: var(--highlight-color-left);
}

.personal-name {
  font-weight: 300;
  color: var(--highlight-color-right);
  font-size: 28px;
  border-bottom: 1px solid var(--highlight-color-right);
  margin: 0;
  margin-left: -30px;
  padding-left: 30px;
  padding-bottom: 15px;
}

.profile-pic {
  display: block;
  width: 160px;
  height: 160px;
  border: 5px solid var(--highlight-color-left);
  margin-bottom: 20px;
  object-fit: cover;
  margin-left: auto;
  margin-right: auto;
  border-radius: 50%;
}

.personal-title {
  border-bottom: 1px solid var(--highlight-color-right);
  margin: 0 0 20px -30px;
  padding: 15px 0 15px 30px;
  font-weight: 300;
  font-size: 20px;
}

#resume ul {
  padding-inline-start: 16px;
  margin-block-end: 0px;
  margin-block-start: 5px;
}
</style>
