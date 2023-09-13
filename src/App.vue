<template>
  <div class="resume-header text-light mb-4">
    <div class="container py-5">
      <div class="row gap-3">
        <div class="col-sm-auto col-lg-auto col-12 col-md-12 text-center" v-if="toggleImage">
          <img :src="resumeImage" alt="Resume image" class="resume-image" />
        </div>
        <div class="col-sm col-lg my-auto col-12 col-md-12">
          <div class="row">
            <div class="col-6 col-md-3 text-start main-content">
              <p class="m-0">
                <a class="text-white" :href="'mailto:' + currentTranslations.email[0]">{{
                  currentTranslations.email[0]
                }}</a>
              </p>
              <p class="m-0">
                <a class="text-white" :href="'mailto:' + currentTranslations.email[1]">{{
                  currentTranslations.email[1]
                }}</a>
              </p>
              <p class="m-0">{{ currentTranslations.email[2] }}</p>
            </div>
            <div class="col-12 col-md-6 text-center order-md-0 order-first">
              <h1>{{ currentTranslations.name }}</h1>
              <h4 style="color: lightgrey">({{ currentTranslations.nickname }})</h4>
            </div>
            <div class="col-6 col-md-3 text-end text-white main-content">
              <a target="_blank" class="d-block text-white" :href="'//' + currentTranslations.github">{{
                currentTranslations.github
              }}</a>
              <a target="_blank" class="d-block text-white" :href="'//' + currentTranslations.website">{{
                currentTranslations.website
              }}</a>
              <a target="_blank" class="d-block text-white" :href="'//' + currentTranslations.linkedin">Linkedin</a>
            </div>
            <div class="col-12 no-print text-center pt-4">
              [
              <a href="javascript:window.print()" class="no-print text-white">{{
                currentTranslations.printableVersion
              }}</a>
              ] [
              <a @click="toggleLanguage" href="javascript:void(0)" class="no-print text-white"
                >{{ currentTranslations.switchTo }}
                {{ "en" === currentLanguage ? "Thai" : "English" }}</a
              >
              ] [
              <a
                href="javascript: void(0)"
                @click="toggleImage = !toggleImage"
                class="no-print text-white"
                >{{ currentTranslations.toggleImage }}</a
              >
              ] [
              <a target="_blank"
                :href="'//' + currentTranslations.github + '/resume'"
                class="no-print text-white"
                >{{ currentTranslations.source }}</a
              >
              ]
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="container py-0 main-content">
    <div class="row">
      <div class="col-12">
        <p>
          {{ currentTranslations.introduction[0] }}
        </p>

        <p>
          {{ currentTranslations.introduction[1] }}
        </p>
      </div>
      <div class="col-12 no-print">
        <div class="row">
          <div class="col-12 col-md-7 mt-3">
            <div class="col-12">
              <h4>{{ currentTranslations.education[0].title }}</h4>
              <hr />
              <ul>
                <li
                  v-html="education"
                  v-for="(education, index) in currentTranslations.education[0].items"
                  :key="index"
                ></li>
              </ul>
            </div>
            <div class="col-12">
              <h4>{{ currentTranslations.technologies[0].title }}</h4>
              <hr />
              <ul>
                <li
                  v-html="technologies"
                  v-for="(technologies, index) in currentTranslations.technologies[0].items"
                  :key="index"
                ></li>
              </ul>
            </div>
          </div>
          <div class="col-12 col-md-5 mt-3">
            <h4>CERTIFICATIONS</h4>
            <hr />

            <div class="mt-1">
              <ul>
                <li
                  v-for="(item, index) in currentTranslations.certificates"
                  :key="index"
                  v-html="item"
                ></li>
              </ul>
            </div>
          </div>
        </div>
      </div>
      <div class="col-12 print-only">
        <div class="row">
          <div class="col-7 mt-3">
            <div class="col-12">
              <h4>{{ currentTranslations.education[0].title }}</h4>
              <hr />
              <ul>
                <li
                  v-html="education"
                  v-for="(education, index) in currentTranslations.education[0].items"
                  :key="index"
                ></li>
              </ul>
            </div>
            <div class="col-12">
              <h4>{{ currentTranslations.technologies[0].title }}</h4>
              <hr />
              <ul>
                <li
                  v-html="technologies"
                  v-for="(technologies, index) in currentTranslations.technologies[0].items"
                  :key="index"
                ></li>
              </ul>
            </div>
          </div>
          <div class="col-5 mt-3">
            <h4>CERTIFICATES</h4>
            <hr />

            <div class="mt-1">
              <ul>
                <li
                  v-for="(item, index) in currentTranslations.certificates"
                  :key="index"
                  v-html="item"
                ></li>
              </ul>
            </div>
          </div>
        </div>
      </div>
      <div class="col-12 mt-3">
        <h4>{{ currentTranslations.projects_title }}</h4>
        <hr />
        <ul>
          <li v-html="item" v-for="(item, index) in currentTranslations.projects" :key="index"></li>
        </ul>
      </div>
      <div class="col-12 mt-3">
        <h4>{{ currentTranslations.interests_title }}</h4>
        <hr />
        <ul>
          <li
            v-html="item"
            v-for="(item, index) in currentTranslations.interests"
            :key="index"
          ></li>
        </ul>
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import resumeImage from "@/assets/resume-image.jpg";
import unity_cert from "@/assets/unity_cert.png";
export default {
  data() {
    return {
      unity_cert,
      resumeImage,
      toggleImage: true,
      translations: {
        en: {
          email: ["mju6404101332@mju.ac.th", "tawan.csmju@gmail.com", "Chaing Mai, Thailand"],
          name: "Maythawat Mahawan",
          nickname: "Tawan",
          github: "github.com/moking55",
          website: "codename-t.com",
          linkedin: "www.linkedin.com/in/maythawat-mahawan-011ba91ba/",
          printableVersion: "Printable version",
          switchTo: "Switch to",
          toggleImage: "Toggle image",
          source: "Source",
          introduction: [
            "I am Maythawat Mahawan, also known as Tawan a Computer Science student at Maejo University with a passion for learning, I have had some experience in programming. This made me understand the basic workings of OOP and MVC systems. I am always eager to take on new challenges. I am also help to organize events and promote computer science to other students, include 20th and 21th Youth Computer Camp Project and 2022 Science Week events.",
            "I am a highly motivated and organized individual with strong communication and teamwork skills. I am confident that I have the skills and experience necessary to succeed in a computer science career."
          ],
          education: [
            {
              title: "EDUCATION",
              items: [
                "<b>VC. Technical Computer,</b> Lamphun Technical Collage, TH 2018 - 2021 [ GPAX 3.34 ]",
                "<b>B. Computer Science,</b> Maejo University, TH 2021 - present [ GPAX 3.43 ]"
              ]
            }
          ],
          technologies: [
            {
              title: "TECHNOLOGIES AND LANGUAGES",
              items: [
                "<b>Languages:</b> Node.js (intermediate), Javascript, TypeScript, SQL, Python, PHP (strong), HTML, CSS.",
                "<b>Frameworks:</b> Codeigniter 4, VueJS, Vuetify, Bootstrap, Bulma.",
                "<b>Databases:</b> Firebase (Firestore & Authentication), MySQL.",
                "<b>IaaS, PaaS:</b> Vercel, GitHub Pages, CloudFlare, Netlify",
                "<b>Other:</b> Github, Github Actions, StackBlitz, AWS SageMaker Studio."
              ]
            }
          ],
          certificates: [
            "<b>CSCMU Coding Challenge 2023 Participant</b> (30/8/2023)",
            `<img src="${unity_cert}" alt="Unity Certified Programmer" style="width: 44px" class="mt-1 no-print" /> </a ><b>Unity Certified User: Programmer</b> (9/3/2022)`,
            "<b>1st Prize New Generation Invention Contest Vocational education level</b> (9/12/2020)"
          ],
          projects_title: "PROJECTS",
          projects: [
            `<b>BCITSVC -</b> A modern faculty website for an educational institution, designed for user-friendly information and resources. <a target="_blank" href="//bcitsvc.com">bcitsvc.com</a>`,
            `<b>Blockify -</b> A straightforward webshop platform designed specifically for Minecraft enthusiasts.`,
            `<b>Lanna Words -</b> An engaging simple word guessing game with a user-friendly interface. <a target="_blank" href="//lannawords.codename-t.com">lannawords.codename-t.com</a>`,
            `<b>VTuber.in.th -</b> A Thai vtuber tracking website that provides information and updates on popular virtual YouTubers. <a target="_blank" href="//vtuber.in.th">vtuber.in.th</a>`,
            `<b>MC Mart -</b> A standalone Minecraft webshop developed using CodeIgniter 4 framework. <a target="_blank" href="//github.com/moking55/mc-mart">github.com/moking55/mc-mart</a>`,
            `<b>ClassX -</b> An efficient online classroom platform for seamless virtual learning experiences. <a target="_blank" href="//github.com/moking55/ClassX-simple-classroom"
              >github.com/moking55/ClassX-simple-classroom</a
            >`,
            `<b>LTC Guide -</b> A handy student handbook application created using the Flutter framework. <a target="_blank"
              href="//thaiinvention.net/bb_projectdetail.php?p=cHJvamVjdF9pZD01Mjc2NiZjZmdfaWQ9MzYmY29tcGV0X2lkPTI="
              >thaiinvention.net</a
            >`
          ],
          interests_title: "INTERESTS",
          interests: [
            "Areas : Coding, Productivity & Life-hacks",
            "Beverage : Americano, Iced Espresso, Matcha tea",
            "Games : Arcade, Indie, FPS",
            "Pet : I have a cat name Khaijeaw"
          ]
        },
        th: {
          email: ["mju6404101332@mju.ac.th", "tawan.csmju@gmail.com", "เชียงใหม่, ประเทศไทย"],
          name: "เมธาวัฒน์ มหาวัน",
          nickname: "ตะวัน",
          github: "github.com/moking55",
          website: "codename-t.com",
          linkedin: "www.linkedin.com/in/maythawat-mahawan-011ba91ba/",
          printableVersion: "พิมพ์หน้านี้",
          switchTo: "เปลี่ยนภาษาเป็น",
          toggleImage: "แสดงรูปภาพ",
          source: "Source",
          introduction: [
            `ผมชื่อ เมธาวัฒน์ มหาวัน หรือที่รู้จักในชื่อ ตะวัน นักศึกษาสาขาวิทยาการคอมพิวเตอร์ มหาวิทยาลัยแม่โจ้ ส่วนตัวมีความชอบและค้นคว้าและเคยมีประสบการณ์ในการเขียนโปรแกรมมาบ้างแล้ว ซึ่งทำให้เข้าใจการทำงานของระบบ OOP และ MVC พื้นฐาน กระผมพร้อมที่จะเผชิญกับความท้าทายใหม่ๆอยู่เสมอ อีกทั้งยังมีส่วนร่วมจัดกิจกรรมและส่งเสริมวิทยาการคอมพิวเตอร์ให้กับนักเรียนคนอื่นๆ อาทิเช่น โครงการค่ายยุวชนคอมพิวเตอร์ครั้งที่ 20 และ 21 และกิจกรรมสัปดาห์วิทยาศาสตร์ปี 2022 มหาวิทยาลัยแม่โจ้`,
            `ผมเชื่อว่าผมมีทักษะในการสื่อสารและความสามารถในการทำงานเป็นทีมที่ดี และประสบการณ์ที่จำเป็นต่อการประสบความสำเร็จในสาขาอาชีพวิทยาการคอมพิวเตอร์`
          ],
          education: [
            {
              title: "การศึกษา",
              items: [
                "<b>ปวช. เทคนิคคอมพิวเตอร์,</b> วิทยาลัยเทคนิคลำพูน, 2018 - 2021 [ GPAX 3.34 ]",
                "<b>ปริญญาตรี. วิทยาการคอมพิวเตอร์,</b> มหาวิทยาลัยแม่โจ้, 2021 - ปัจจุบัน [ GPAX 3.43 ]"
              ]
            }
          ],
          technologies: [
            {
              title: "เทคโนโลยีและภาษาที่ใช้",
              items: [
                "<b>Languages:</b> Node.js (intermediate), Javascript, TypeScript, SQL, Python, PHP (strong), HTML, CSS.",
                "<b>Frameworks:</b> Codeigniter 4, VueJS, Vuetify, Bootstrap, Bulma.",
                "<b>Databases:</b> Firebase (Firestore & Authentication), MySQL.",
                "<b>IaaS, PaaS:</b> Vercel, GitHub Pages, CloudFlare, Netlify",
                "<b>Other:</b> Github, Github Actions, StackBlitz, AWS SageMaker Studio."
              ]
            }
          ],
          certificates: [
            "<b>CSCMU Coding Challenge 2023 Participant</b> (30/8/2023)",
            `<img src="${unity_cert}" alt="Unity Certified Programmer" style="width: 44px" class="mt-1 no-print" /> </a ><b>Unity Certified User: Programmer</b> (9/3/2022)`,
            "<b>รางวัลชนะเลิศ ระดับเหรียญทอง การประกวดสิ่งประดิษฐ์ของคนรุ่นใหม่</b> (9/12/2020)"
          ],
          projects_title: "ผลงาน",
          projects: [
            `<b>BCITSVC -</b> เว็บไซต์แผนกวิชาคอมพิวเตอร์ธุรกิจวิทยาลัยอาชีวศึกษาสุราษร์ธานี <a target="_blank" href="//bcitsvc.com">bcitsvc.com</a>`,
            `<b>Blockify -</b> แพลตฟอร์มอีคอมเมอร์ชสำหรับซื้อขายสินค้าภายในเกม Minecraft ผ่านระบบเว็บไซต์`,
            `<b>Lanna Words -</b> เกมทายคำภาษาล้านนาที่มีอินเตอร์เฟซใช้งานง่าย <a target="_blank" href="//lannawords.codename-t.com">lannawords.codename-t.com</a>`,
            `<b>VTuber.in.th -</b> เว็บไซต์ติดตามวีทูเบอร์ไทยที่ให้ข้อมูลและอัพเดทข่าวสารวีทูเบอร์ไทย <a target="_blank" href="//vtuber.in.th">vtuber.in.th</a>`,
            `<b>MC Mart -</b> เว็บไซต์สำหรับบริหารจัดการร้านค้าออนไลน์สำหรับเกม Minecraft ที่พัฒนาด้วย CodeIgniter 4 framework.  <a target="_blank" href="//github.com/moking55/mc-mart">github.com/moking55/mc-mart</a>`,
            `<b>ClassX -</b> แพลตฟอร์มห้องเรียนออนไลน์ที่มีประสิทธิภาพสำหรับการเรียนการสอนแบบเสมือนจริง <a target="_blank" href="//github.com/moking55/ClassX-simple-classroom"
              >github.com/moking55/ClassX-simple-classroom</a>`,
            `
            <b>LTC Guide -</b> แอพพลิเคชั่นคู่มือนักเรียนออนไลน์วิทยาลัยเทคนิคลำพูนสร้างโดย Flutter framework
            <a target="_blank"
              href="//thaiinvention.net/bb_projectdetail.php?p=cHJvamVjdF9pZD01Mjc2NiZjZmdfaWQ9MzYmY29tcGV0X2lkPTI="
              >thaiinvention.net</a
            >`
          ],
          interests_title: "ความสนใจ",
          interests: [
            "สนใจเป็นพิเศษ : การเขียนโปรแกรม, การสร้างผลงาน & เทคนิคการใช้ชีวิต",
            "เครื่องดื่ม : อเมริกาโน่, เอสเปรสโซ่, ชาเขียวมัจฉะ",
            "แนวเกม : อาเขต, อินดี้, FPS",
            "สัตว์เลี้ยง : ผมมีแมวชื่อไข่เจียว"
          ]
        }
      },
      currentLanguage: "en" // Default language is English
    };
  },
  computed: {
    // Get the translations for the current language
    currentTranslations() {
      // @ts-ignore
      return this.translations[this.currentLanguage];
    }
  },
  methods: {
    // Function to toggle the language
    toggleLanguage() {
      this.currentLanguage = this.currentLanguage === "en" ? "th" : "en";
    }
  }
};
</script>
<style>
.resume-header {
  background-color: #3f2e3e;
}
.resume-image {
  height: 240px;
  border-radius: 5px;
}
hr {
  margin-top: 4px;
  margin-bottom: 4px;
}
.print-only {
  display: none;
}

@media print {
  .no-print {
    display: none !important;
  }

  .print-only {
    display: block !important;
  }

  .text-white {
    color: black !important;
  }

  /* fitting font size to A4 paper */
  .main-content {
    font-size: 12px !important;
  }
  hr {
    margin-top: -2px !important;
    margin-bottom: 4px !important;
  }

  a {
    color: black !important;
  }

  /* decrase all header tags size */
  h1,
  h2,
  h3,
  h4,
  h5,
  h6 {
    font-size: 18px !important;
    margin: 0 !important;
  }

  /* fiting heading size */
  .resume-header {
    margin-top: -2em !important;
    margin-bottom: -2em !important;
    color: black !important;
  }

  div.col-12.mt-3 {
    margin-top: 0.2em !important;
  }

  .resume-image {
    height: 140px !important;
  }
}
</style>
