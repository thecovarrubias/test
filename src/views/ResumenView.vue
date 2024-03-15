<script setup>
import Profile from "../assets/Profile.svg";

import jsPDF from "jspdf";
import html2canvas from "html2canvas";

const downloadPDF = () => {
  const resumenElement = document.querySelector(".resumen");

  html2canvas(resumenElement).then((canvas) => {
    const pdf = new jsPDF("p", "mm", "a4");
    const imgData = canvas.toDataURL("image/png");
    const imgWidth = 210;
    const imgHeight = (canvas.height * imgWidth) / canvas.width;
    pdf.addImage(imgData, "PNG", 0, 0, imgWidth, imgHeight);
    pdf.save("resumen.pdf");
  });
};

const infoData = [
  {
    name: "Contact",
    items: [
      "thcovarrubias@gmail.com",
      "+52 221 222 8347",
      "thecovarrubias.me",
      "Puebla, Mexico",
    ],
  },
  {
    name: "Languages",
    items: ["English B1", "Native Spanish"],
  },
];

const expData = [
  {
    name: "SIGSA",
    time: "JUN 2021 - Present",
    desc: "Software Developer. Collaborated in the implementation of diverse frontend application modules, achieving tangible improvements in process efficiency, such as a reduction in the execution time of automated tasks.",
    items: [
      "Worked collaboratively with other developers, contributing to a smooth development workflow.",
      "Developed designs focused on consistency and data presentation, receiving praise for improved usability and information comprehension.",
      "Managed application state using strategies such as Events, Props, Event Bus, Mixins, and Vuex, addressing complex challenges and enhancing system stability.",
      "Developed user-oriented features using Vue JS and leveraging the specific features of Vuetify (Version 2) for an enhanced user experience.",
    ],
  },
  {
    name: "Freelancer",
    time: "AUG 2023 - JAN 2024",
    desc: "Frontend Developer. Collaborated in the implementation of diverse modules in responsive frontend applications, achieving significant improvements in process efficiency.",
    items: [
      "Successfully integrated Tailwind CSS to optimize design and enhance code efficiency, resulting in improved website loading speed.",
      "Led the integration of Figma prototypes into development, facilitating visualization and approval of the platform by the team.",
      "Managed application state using strategies such as Events, Props, Provide/Inject, Composables, and Pinia, addressing complex challenges and enhancing user experience.",
      "Developed user-oriented features using Vue JS (Version 3) and reusable components, receiving positive feedback from users for improved usability.",
    ],
  },
  {
    name: "Hackademy MX ",
    time: "APR 2021 - SEP 2021",
    desc: "Frontend Developer. Collaborated in the implementation of a platform dedicated to remote interviews.",
    items: [
      "Contributed to the design and prototyping in Figma, facilitating the visualization and approval of the platform by the team.",
      "Demonstrated proficiency in the design and development of responsive websites, ensuring a consistent user experience across various devices.",
      "Developed user-oriented features using React JS, React Bootstrap, and reusable components, enhancing usability and interaction in remote interviews.",
    ],
  },
];
</script>

<template>
  <div class="resumen">
    <div class="info">
      <div>
        <img :src="Profile" alt="José G. Covarrubias" height="200" />
        <h1 class="title">Jose Guadalupe Covarrubias Pulido</h1>
        <h2 class="subtitle">Information Technology Engineer</h2>
        <p>
          Engineer focused on the development of solutions based on frontend
          applications with the ability to work independently and
          collaboratively in a remote environment.
        </p>
      </div>

      <div v-for="({ name, items }, index) in infoData" :key="index">
        <h3 class="subtitle">{{ name }}</h3>
        <ul class="list" v-for="(item, i) in items" :key="i">
          <li>{{ item }}</li>
        </ul>
      </div>
    </div>

    <div class="experience">
      <button class="button" @click="downloadPDF()">Download PDF</button>

      <h2 class="subtitle">Work Experience</h2>
      <div
        class="experience__item"
        v-for="({ name, time, desc, items }, index) in expData"
        :key="index"
      >
        <div class="experience__item__header">
          <div>{{ name }}</div>
          <div>{{ time }}</div>
        </div>
        <div>{{ desc }}</div>
        <ul class="list" v-for="(item, i) in items" :key="i">
          <li>{{ item }}</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.resumen {
  margin-top: 10px;
  display: flex;
}

.title {
  font-size: 1.5rem;
}

.subtitle {
  font-size: 1.15rem;
}

.info {
  align-items: center;
  border-right: 1px solid #2e2e2e;
  display: flex;
  flex-direction: column;
  height: 850px;
  justify-content: space-around;
  padding: 15px;
  text-align: center;
  width: 20%;

  .list {
    list-style: none;
    margin: 0 0 10px;
    padding: 0;
  }
}

.experience {
  width: 80%;
  height: 850px;
  padding: 15px;
  position: relative;
}

.experience__item {
  padding: 15px;

  .experience__item__header {
    display: flex;
    font-weight: bold;
    justify-content: space-between;
    margin-bottom: 15px;
  }
}

.button {
  background: #2e2e2e;
  color: white;
  cursor: pointer;
  font-weight: bold;
  padding: 5px 25px;
  position: absolute;
  right: 0;
  top: 0;
  transition: 750ms all;
}

.button:hover {
  background: white;
  color: #2e2e2e;
}
</style>
