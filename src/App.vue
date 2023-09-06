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
              <p class="m-0"><a class="text-white" href="mailto:mju6404101332@mju.ac.th">mju6404101332@mju.ac.th</a></p>
              <p class="m-0"><a class="text-white" href="mailto:tawan.csmju@gmail.com">tawan.csmju@gmail.com</a></p>
              <p class="m-0">Chaing Mai, Thailand</p>
            </div>
            <div class="col-12 col-md-6 text-center order-md-0 order-first">
              <h1>Maythawat Mahawan</h1>
              <h4 style="color: lightgrey">(Tawan)</h4>
            </div>
            <div class="col-6 col-md-3 text-end text-white main-content">
              <a class="d-block text-light" href="//github.com/moking55">github.com/moking55</a>
              <a class="d-block text-light" href="//codename-t.com">codename-t.com</a>
              <a
                class="d-block text-light"
                href="//www.linkedin.com/in/maythawat-mahawan-011ba91ba/"
                >Linkedin</a
              >
            </div>
            <div class="col-12 no-print text-center">
              [ <a href="javascript:window.print()" class="no-print text-white">Printable version</a> ]
              [ <a href="javascript:window.print()" class="no-print text-white">Switch to</a> ]
              [ <a href="javascript: void(0)" @click="toggleImage = !toggleImage" class="no-print text-white">Toggle image</a> ]
              [ <a href="//github.com/moking55/resume" class="no-print text-white">Source</a> ]
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
          I am a computer science student at Maejo University with a passion for learning and
          sharing knowledge. I am a quick learner and I am always eager to take on new challenges. I
          am also a secretary in the computer club, where I help to organize events and promote
          computer science to other students.
        </p>

        <p>
          I am confident that I have the skills and knowledge necessary to be a successful
          programming intern. I am a hard worker and I am always willing to go the extra mile. I am
          also a team player and I am able to work well with others. I am eager to learn more about
          the programming industry and I am confident that I can make a significant contribution to
          your team.
        </p>
      </div>
      <div class="col-12 mt-3">
        <h4>EDUCATION</h4>
        <hr />
        <ul>
          <li>
            <b>VC. Technical Computer,</b> Lamphun Technical Collage, TH 2018 - 2021 [ GPA 3.48 ]
          </li>
          <li><b>B. Computer Science,</b> Maejo University, TH 2021 - now [ GPAX 3.43 ]</li>
        </ul>
      </div>
      <div class="col-12 mt-3">
        <h4>TECHNOLOGIES AND LANGUAGES</h4>
        <hr />
        <ul>
          <li>Languages: Node.js (intermediate), Javascript, TypeScript, SQL, Python, PHP (strong), HTML, CSS.</li>
          <li>Frameworks: Codeigniter 4, VueJS, Vuetify, Bootstrap, Bulma.</li>
          <li>Databases: Firebase, MySQL.</li>
          <li>Other: Vercel, Github, CloudFlare, Netlify.</li>
        </ul>
      </div>
      <div class="col-12 mt-3">
        <h4>PROJECTS</h4>
        <hr />
        <ul>
          <li>
            <b>BCITSVC -</b> A modern faculty website for an educational institution, designed for
            user-friendly information and resources. <a href="//bcitsvc.com">bcitsvc.com</a>
          </li>
          <li>
            <b>Blockify -</b> A straightforward webshop platform designed specifically for Minecraft
            enthusiasts.
          </li>
          <li>
            <b>Lanna Words -</b> An engaging simple word guessing game with a user-friendly
            interface. <a href="//lannawords.codename-t.com">lannawords.codename-t.com</a>
          </li>
          <li>
            <b>VTuber.in.th -</b> A Thai vtuber tracking website that provides information and
            updates on popular virtual YouTubers. <a href="//vtuber.in.th">vtuber.in.th</a>
          </li>
          <li>
            <b>MC Mart -</b> A standalone Minecraft webshop developed using CodeIgniter 4 framework.
          </li>
          <li>
            <b>ClassX -</b> An efficient online classroom platform for seamless virtual learning
            experiences.
            <a href="//github.com/moking55/ClassX-simple-classroom"
              >github.com/moking55/ClassX-simple-classroom</a
            >
          </li>
          <li>
            <b>LTC Guide -</b> A handy student handbook application created using the Flutter
            framework.
            <a
              href="//thaiinvention.net/bb_projectdetail.php?p=cHJvamVjdF9pZD01Mjc2NiZjZmdfaWQ9MzYmY29tcGV0X2lkPTI="
              >thaiinvention.net</a
            >
          </li>
        </ul>
      </div>
      <div class="col-12 mt-3">
        <h4>INTERESTS</h4>
        <hr />
        <ul>
          <li>Areas : Coding, Productivity & Life-hacks</li>
          <li>Beverage : Americano, Iced Espresso, Matcha tea</li>
          <li>Games : Arcade, Indie, FPS</li>
          <li>Pet : I have a cat name Khaijeaw</li>
        </ul>
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import resumeImage from "@/assets/resume-image.jpg";
export default {
  data() {
    return {
      resumeImage: resumeImage,
      toggleImage: true,
    };
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
@media print {
  .no-print {
    display: none !important;
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
