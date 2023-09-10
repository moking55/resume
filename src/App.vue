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
              <a class="d-block text-light" :href="'//' + currentTranslations.github">{{
                currentTranslations.github
              }}</a>
              <a class="d-block text-light" :href="'//' + currentTranslations.website">{{
                currentTranslations.website
              }}</a>
              <a class="d-block text-light" :href="'//' + currentTranslations.linkedin">Linkedin</a>
            </div>
            <div class="col-12 no-print text-center">
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
              <a
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
  <div class="container py-2 main-content">
    <div class="row">
      <div class="col-12">
        <p>
          {{ currentTranslations.introduction[0] }}
        </p>

        <p>
          {{ currentTranslations.introduction[1] }}
        </p>
      </div>
      <div class="col-12">
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
                <li>
                  <a href="" class="no-print">
                    <img
                      :src="unity_cert"
                      alt="Unity Certified Programmer"
                      style="width: 44px"
                      class="mt-1"
                    /> </a
                  ><b>Unity Certified User: Programmer</b> (9/3/2022)
                </li>
                <li><b>CSCMU Coding Challenge 2023</b> (30/8/2023)</li>
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
            "My name is Maythawat Mahawan, I am a computer science student at Maejo University with a passion for learning and sharing knowledge. I am a quick learner and I am always eager to take on new challenges. I am also a secretary in the computer club, where I help to organize events and promote computer science to other students.",
            "I am confident that I have the skills and knowledge necessary to be a successful programming intern. I am a hard worker and I am always willing to go the extra mile. I am also a team player and I am able to work well with others. I am eager to learn more about the programming industry and I am confident that I can make a significant contribution to your team."
          ],
          education: [
            {
              title: "EDUCATION",
              items: [
                "<b>VC. Technical Computer,</b> Lamphun Technical Collage, TH 2018 - 2021 [ GPA 3.48 ]",
                "<b>B. Computer Science,</b> Maejo University, TH 2021 - now [ GPAX 3.43 ]"
              ]
            }
          ],
          technologies: [
            {
              title: "TECHNOLOGIES AND LANGUAGES",
              items: [
                "<b>Languages:</b> Node.js (intermediate), Javascript, TypeScript, SQL, Python, PHP (strong), HTML, CSS.",
                "<b>Frameworks:</b> Codeigniter 4, VueJS, Vuetify, Bootstrap, Bulma.",
                "<b>Databases:</b> Firebase, MySQL.",
                "<b>Other:</b> Vercel, Github, CloudFlare, Netlify."
              ]
            }
          ],
          certificates: [
            "<b>Unity Certified User: Programmer</b> (9/3/2022)",
            "<b>CSCMU Coding Challenge 2023</b> (30/8/2023)"
          ],
          projects_title: "PROJECTS",
          projects: [
            `<b>BCITSVC -</b> A modern faculty website for an educational institution, designed for user-friendly information and resources. <a href="//bcitsvc.com">bcitsvc.com</a>`,
            `<b>Blockify -</b> A straightforward webshop platform designed specifically for Minecraft enthusiasts.`,
            `<b>Lanna Words -</b> An engaging simple word guessing game with a user-friendly interface. <a href="//lannawords.codename-t.com">lannawords.codename-t.com</a>`,
            `<b>VTuber.in.th -</b> A Thai vtuber tracking website that provides information and updates on popular virtual YouTubers. <a href="//vtuber.in.th">vtuber.in.th</a>`,
            `<b>MC Mart -</b> A standalone Minecraft webshop developed using CodeIgniter 4 framework.`,
            `<b>ClassX -</b> An efficient online classroom platform for seamless virtual learning experiences. <a href="//github.com/moking55/ClassX-simple-classroom"
              >github.com/moking55/ClassX-simple-classroom</a
            >`,
            `<b>LTC Guide -</b> A handy student handbook application created using the Flutter framework. <a
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
            `กระผม นายเมธาวัฒน์ มหาวัน นักศึกษาชั้นปีที่ ${new Date().getFullYear() - 2020} สาขาวิทยาการคอมพิวเตอร์ คณะวิทยาศาสตร์ มหาวิทยาลัยแม่โจ้ มีความสนใจในการเขียนโปรแกรม และการแบ่งปันความรู้ กระผมเป็นคนที่เรียนรู้ได้เร็วและมีความกระตือรือร้นในการทำงาน กระผมเป็นเลขาธิการในชมรมคอมพิวเตอร์ ที่ช่วยในการจัดงานและส่งเสริมให้นักศึกษาคณะวิทยาศาสตร์ได้รู้จักกับวิชาการคอมพิวเตอร์มากขึ้น`,
            `กระผมมั่นใจว่า กระผมมีทักษะและความรู้ที่จำเป็นต่อการเป็นนักฝึกงานที่ประสบความสำเร็จ กระผมยังสามารถทำงานร่วมกับผู้อื่นได้ดีและต้องการศึกษาความรู้ในอุตสาหกรรมคอมพิวเตอร์ กระผมมั่นใจว่า ผมสามารถมีส่วนร่วมในทีมของคุณได้เป็นอย่างมาก`
          ],
          education: [
            {
              title: "การศึกษา",
              items: [
                "<b>ปวช. เทคนิคคอมพิวเตอร์,</b> วิทยาลัยเทคนิคลำพูน, 2018 - 2021 [ GPA 3.48 ]",
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
                "<b>Databases:</b> Firebase, MySQL.",
                "<b>Other:</b> Vercel, Github, CloudFlare, Netlify."
              ]
            }
          ],
          certificates: [
            "<b>Unity Certified User: Programmer</b> (9/3/2022)",
            "<b>CSCMU Coding Challenge 2023</b> (30/8/2023)"
          ],
          projects_title: "ผลงาน",
          projects: [
            `<b>BCITSVC -</b> เว็บไซต์แผนกวิชาคอมพิวเตอร์ธุรกิจวิทยาลัยอาชีวศึกษาสุราษร์ธานี <a href="//bcitsvc.com">bcitsvc.com</a>`,
            `<b>Blockify -</b> แพลตฟอร์มอีคอมเมอร์ชสำหรับซื้อขายสินค้าภายในเกม Minecraft ผ่านระบบเว็บไซต์ <a href="//blockify.codename-t.com">blockify.codename-t.com</a>`,
            `<b>Lanna Words -</b> เกมทายคำภาษาล้านนาที่มีอินเตอร์เฟซใช้งานง่าย <a href="//lannawords.codename-t.com">lannawords.codename-t.com</a>`,
            `<b>VTuber.in.th -</b> เว็บไซต์ติดตามวีทูเบอร์ไทยที่ให้ข้อมูลและอัพเดทข่าวสารวีทูเบอร์ไทย <a href="//vtuber.in.th">vtuber.in.th</a>`,
            `<b>MC Mart -</b> เว็บไซต์สำหรับบริหารจัดการร้านค้าออนไลน์สำหรับเกม Minecraft ที่พัฒนาด้วย CodeIgniter 4 framework.`,
            `<b>ClassX -</b> แพลตฟอร์มห้องเรียนออนไลน์ที่มีประสิทธิภาพสำหรับการเรียนการสอนแบบเสมือนจริง <a href="//github.com/moking55/ClassX-simple-classroom"
              >github.com/moking55/ClassX-simple-classroom</a>`,
            `
            <b>LTC Guide -</b> แอพพลิเคชั่นคู่มือนักเรียนออนไลน์วิทยาลัยเทคนิคลำพูนสร้างโดย Flutter framework
            <a
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
      currentLanguage: "th" // Default language is English
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

  /* fitting font size to A4 paper */
  .main-content {
    font-size: 12px !important;
  }
  hr {
    margin-top: 0px !important;
    margin-bottom: 4px !important;
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
