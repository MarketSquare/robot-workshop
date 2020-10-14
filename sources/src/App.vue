<template>
  <div class="row no-gutters">
    <navigation-horizontal :pages="pages"/>
    <b-img :src="require('@/assets/img/ROBOTFW_Mark_White_LOW_cropped.png')" class="logo-fixed" alt="Robot Frameworkg logo"/>
    <div class="col-md-12" ref="content" style="width: 100%">
      <app-header/>
      <page-block
        v-for="(page, index) in pages"
        v-bind:page="page"
        v-bind:index="index"
        v-bind:key="index"
        class="pl-md-5 px-lg-2 p-sm-2 p-xs-1 link-fix"
      />
      <app-footer class="mt-3 py-5"/>
    </div>
  </div>
</template>
<script>
import PageBlock from "@/Components/PageBlock.vue";

export default {
  components: {
    PageBlock
  },
  data() {
    return {
      pages: [
        {
          title: "Welcome",
          text_block_centered: true,
          data: {
            text: {
              twitter: false,
              header: "World Wide Workshop Wednesday",
              text:
                `<p>We are happy to announce that the Robot Framework Foundation will be holding a World Wide Workshop Wednesday on <b>December 2nd</b> this year.</p>
                <p>All Workshops will be hold online on <a href="https://bigbluebutton.org/" target="blank">BigBlueButton</a> Servers located in Germany.<br>
                </p>
                <p>Due to COVID-19 we can not have an on-side conference next January and do not get revenues from that ticket sales. 
                With this workshop event we want to give you the possibility to donate for Robot Framework. 
                But you do also get a lot for your money!<br>
                We have gathered experts from the Robot Framework Community to hold great workshops.
                The revenues of the day will be used entirely for the further development of Robot Framework.</p>
                <p>Special thanks go to all workshop organizers who will share their experience with the community.</p>
                <h2 style="margin-left: 1.5rem !important;">Thank you very much! You are the best ❤️ </h2></p>`
            }
          }
        },
        {
          title: "Contribute",
          text_block_centered: true,
          user_contact: true,
          data: {
            text: {
              twitter: false,
              header: "Contribution",
              text:
                `<p>We are still looking for community members who want to share their knowledge in a workshop.<br>
                Please contact us if you want to contribute:`
            },
            users: [
              {
                title: "René Rohner",
                text: "<b>René Rohner</b><br>imbus AG<br><a href='mailto:rene@robotframework.org'>rene@robotframework.org</a><br>@René on Slack",
                href: "mailto:rene@robotframework.org",
                img: require("@/assets/img/users/Rene_Rohner.png")
              },
              {
                title: "Mikko Korpela",
                text: "Mikko Korpela</b><br>Reaktor Oy<br><a href='mailto:mikko@robotframework.org'>mikko@robotframework.org</a><br>@mkorpela on Slack",
                href: "mailto:mikko@robotframework.org",
                img: require("@/assets/img/users/Mikko_Korpela.png")
              }
            ]
          }
        },
        {
          title: "Sponsors",
          text_block_centered: true,
          tab_box: false,
          feature_box: false,
          main_sponsor_box: true,
          data: {
            text: {
              header: "Main Sponsors",
              twitter: false
            },
            users: [
              {
                title: "imbus AG",
                href: "https://www.imbus.de",
                img: require("@/assets/img/sponsors/imbus.png")
              },
              {
                title: "Reaktor Oy",
                href: "https://www.reaktor.com/",
                img: require("@/assets/img/sponsors/reaktor.png")
              },
            ]
          }
        },
        {
          title: "",
          text_block_centered: true,
          tab_box: false,
          feature_box: false,
          user_box: true,
          data: {
            text: {
              header: "Sponsors",
              twitter: false
            },
            users: [
              /*{
                title: "imbus AG",
                href: "https://www.imbus.de",
                img: require("@/assets/img/sponsors/imbus.png")
              },
              {
                title: "Reaktor Oy",
                href: "https://www.reaktor.com/",
                img: require("@/assets/img/sponsors/reaktor.png")
              },*/
            ]
          }
        },
       /* {
          title: "Conference",
          text_block: false,
          text_block_centered: true,
          tab_box: false,
          feature_box: false,
          user_box: false,
          user_box_centered: false,
          data: {
            text: {
              twitter: false,
              header: "Conference Program",
              text: "<p>Click talk's title for description!</p>",
              talks: [
                { header: 'Wednesday, January 15' },
                { author: "08:00", title: "Doors open, registration, breakfast" },
                { author: "09:00 Pekka Klärck", title: "Welcome to Robocon 2020!" },
                { author: "09:10 Esko Valtaoja",
                  title: "KEYNOTE: Matter, energy and knowledge: saving the world with technology",
                  descriptionExpanded: "A long time ago, Karl Marx sketched in his notebooks the true goal of communism: a stateless and classless society based on automation and abundance. Without, it seems, anybody noticing, we are creeping closer and closer to Marx's goal. Technology, machines, automation and digitalization continue to increase our wealth and decrease our work load. But is this process sustainable: can technology also save our planet, not just ourselves? And what is the role of mere humans in a world run by machines and AI?",
                  bio: "Esko Valtaoja is Professor Emeritus of Space Astronomy at Turku University. The NASA ADS database lists 269 scientific publications under his name. He has published a dozen nonfiction books, with total sales well over 200 000 copies. According to the three latest Science Barometers, he is by far the best known living scientist in Finland. One of his favorite pastimes is to ponder, nonmetaphysically, Paul Gauguin's famous questions: \"Where do we come from? What are we? Where are we going?\"." },
                { author: "10:00", title: "Break" },
                { author: "10:30 Jeff King",
                  title: "Robot Framework and the One Man Robot Band",
                  descriptionExpanded: "Being the sole automation engineer in a small organization is like being a musician in one-man band. Robot Framework's toolkit is the perfect instrument for a QA and process automation Rock Star!",
                  bio: "Jeff King is a native of Connecticut, United States. He has 15+ years quality assurance, primarily in the arts/entertainment ticketing field. A graduate of the University of Connecticut, Jeff lives in the Hartford, Connecticut area of the New England region of the US with his wife Carrie, son Joshua, daughter Megan, dog Gordo and cats Willow and Dash.<br><br>Aside from IT, Jeff is a runner, hiker and writer. Jeff's book 'Rivers End', a fiction mystery, was published in 2014. Jeff is the co-host of the 'Wandering Tailgaters', a podcast covering American College Football." },
                { author: "11:00 Anaïs van Asselt",
                  title: "A Robot Rainbow Cake: Implementing a test automation architecture in a government organization",
                  descriptionExpanded: "Imagine a large government organization in Agile transition using a homemade test automation tool. Here I discovered, introduced and coached the implementation of a multi-layer test automation architecture in Robot Framework. I would love to share my journey, complete with struggles and learnings.<br><br>Robot Framework is worth a party, and there is no party without rainbow cake! Robot Framework is a very powerful tool, but with great power comes with great responsibility. When working with several people in a large government organization on a test set without a clearly agreed structure, it is easy to get lost in a labyrinth of keywords. Structure is a must to keep a Robot Framework test set maintainable and can be achieved by a test automation framework architecture. <br><br>In this talk I will take you on a journey discovering and coaching the implementation of a multi-layer test automation architecture Robot rainbow cake. The ingredients include the application of known test automation strategies, writing BDD testcases and using the Page Object Model to automate on GUI level. It concludes with the big picture of Robot Framework and other tooling enabling continuous testing in this large government organization. All of this complete with a frosting of associated struggles and learnings.",
                  bio: "As a coincidental tester I coincidentally found my passion for test automation, Agile and DevOps. I love the endless possibilities of Agile and DevOps. There is not one solution, so I like to do it like Bruce Lee and apply the possibilities and strategies that suit best! After 5 years’ experience within Agile/DevOps teams of several companies, I am now coaching teams in a large government organization with test automation by sharing my experiences, the successes and epic failures. This experience results in a unique view of test automation in a bureaucratic environment." },
                { author: "11:30", title: "Lunch" },
                { author: "12:30 Antti Karjalainen",
                  title: "The Open RPA Ecosystem",
                  descriptionExpanded: "Robotic Process Automation is an opportunity for the Robot Framework community to create something truly big. This talk outlines a new concept, called 'The Open RPA Ecosystem', which is a collection of tools, projects, and ideas around the core Robot Framework.<br><br>Sometimes big innovations happen by bringing existing solutions from one domain into a new one. The technology to create RPA solutions has been there for years, but only recently, we have realized to start applying it in new ways. What started as a few technical experiments is fast growing into a new industry. We call this industry the Open RPA Ecosystem.<br><br>RPA is a huge opportunity for the Robot Framework community, bigger than we can think of. Making the leap from test automation to automating anything is not just a technical challenge. It requires new ways of working, thinking, and organizing collaboration.<br><br>In this talk, we will outline what exactly is the Open RPA Ecosystem, and why do we need to start thinking in terms of an ecosystem instead of a single tool, Robot Framework. We will also take a look at what has happened in Open RPA since the last Robocon and what's expected for the next year. In the spirit of our conference theme, we also ask, what do we need to do in the ecosystem to make it truly a global takeover?",
                  bio: "Robot Framework activist on a mission to change the RPA industry.<br><br>Founder and CEO of Robocorp. Member of the board at Robot Framework Foundation." },
                { author: "13:00 Petteri Mannersalo",
                  title: "Robot Framework as an enabler for Intelligent Process Automation",
                  descriptionExpanded: "Intelligent Process Automation (IPA) is RPA on steroids. The boost is realized by applying machine learning and other related approaches to extend simple rule based reasoning to more intelligent actions. Robot Framework with intelligent microservices provides a flexible platform for IPA solutions.<br><br>The basis of Intelligent Process Automation (IPA) is built by a combination of Robotic Process Automation (RPA), AI and analytics. On the other hand, Robot Framework provides solutions to automate, integrate and orchestrate various functionalities and services together with the enterprise software. When offering enterprise-grade robotics environments, the typical way of including intelligent functionalities is to offer them as microservices which can easily be integrated into any automation process.<br><br>In this talk, the ongoing progress from RPA to IPA and beyond is presented first. Then we consider how Robot Framework and intelligent microservices can form a flexible basis for the IPA. The current Robotics as a Service (RaaS) setup by Siili is described as an example. Finally, some applications of machine learning and related approaches are discussed in the context of IPA.",
                  bio: "D.Sc. (Tech.) Petteri Mannersalo is a seasoned expert on applied mathematics and machine learning with an open mind for new problems and challenges. He has a long career as a research scientist working at various research institutes and universities. Since moving to consulting  in 2016, he has been helping customers to utilize data science in their business.<br><br>At the moment, he is machine learning lead in Intelligent Automation at Siili Solutions and his main goal is to empower the robotic process automation with enablers based on machine learning and other advanced approaches." },
                { author: "13:30", title: "Break" },
                { author: "14:00 Tuomas Lempiäinen",
                  title: "QA driven RPA at Veikkaus",
                  descriptionExpanded: "Automation on Robot Framework. You already know how to do it. But you've been lying in your foxhole of testing. Get up! Production is out there. <br><br>Why to drive RPA within the QA team? What changes technically, from the process point of view and most importantly, how do you change the culture?<br><br>I'll encourage you to consider combining your test automation and RPA development. Typically the specialists developing automation on RF are doing either (mostly) TA or RPA alone. Yet, there exists many benefits in combining these two. Answers to the following questions are given:<br><br>* Why should QA (or test automation developers) be the entity in your organization driving RPA development? <br>* The core differences between RPA and TA?<br>* Why you'll be most likely just fine with RF when doing RPA?<br>* Be the change. Each company deserves their own automation evangelist. You already know most of the stuff you need to know. Why wouldn't it be you?",
                  bio: "Together (you, me and coffee) we make the world a better place.<br><br>Family (wife, 2 kids, 2 dogs), sports (captain to a floorball team), music (piano, guitar, composing) control my time after work.<br><br>We manage through the polar night with coffee and some dark, yet beautiful, heavy metal." },
                { author: "14:30 Virpi Luostarinen, Mikael Siirtola (Signant Health)",
                  title: "RPA on Rails: Automating manual processes at VR",
                  descriptionExpanded: "RPA is getting more and more traction and with increase support for it in Robot Framework we decided to come and showcase our example cases here at VR and what we have learned thus far from doing RPA (we are using Robot Framework). We have had great success on removing manual work by usage of RPA and we are here to showcase it. We will show our process, how find out what to automate, and our general RPA architecture.",
                  bio: "<h3 class='mb-0 mt-2'>Mikael Siirtola</h3>I grow digital factories. Before automation engineers went to paper mills to improve production quality and speed, now I employ latest methodologies and technologies to do the same to companies that work on software. I have successfully implemented improvements to various embedded and desktop production pipelines and made a huge turnaround in testing of a big project. In six months, we got same amount of work done as previous 2,5 years. The stagnating progress of automation testing of the system was nine times faster after I took leadership in the test automation activities. Now I set my sight to work where I can do the most impact. As a leader I specialize in running expert organizations and creating low hierarchy networks that produce best product at fastest speed, a team of teams. My motto is try fast, fail fast, improve fast. Companies need to win the minds and the hearts of their talent to succeed and I am a person who does that by creating an atmosphere where people thrive.<br><br>Core competences: #devops #leadership #agile #lean #systemintegration #qa #quality #testing #testautomation #softwaredevelopment #organizationdevelopment #healthcare #medicaldevices" },
                { author: "15:00", title: "Break, coffee" },
                { author: "15:30 Kristina Sabotic",
                  title: "End-to-end testing for end-users",
                  descriptionExpanded: "Have you read a book about testing? A blog? Attended a course? Done a certification? Then you might have noticed that basically all theory about testing concerns product development, and product development only. As if testing ended there! As if it's not a whole different deal to receive a product and test that it actually does what it was brought in to do.<br><br>Our customers have complex structures of† products from different providers, where we verify the integrations by setting up end-to-end tests of complete business flows. The same test script tests through web UI, desktop UI, database, etc., depending on the needs of the situation.<br><br>This is a talk about what happens after product release, about the challenges a tester faces when testing from an end-users perspective, and how we use Robot Framework to do so.",
                  bio: "My professional roots are in test leading, but I have shifted towards test automation - because it's so much fun! I thrive on solving challenging technical issues, as much as I thrive on being the spider in the web, as a test leader often is.<br><br>I live in Stockholm, with a hubbie and two kids. Currently we spend every weekend renovating an old holiday house we bought last year.<br><br>If you don’t feel like gibbering more about RF, feel free to come and discuss knitting with me - I would love to learn which is Helsinki´s best yarn shop. Every time I have a chance to sit down a few minutes, you can find a knitting in my hands. At the moment it's a sock with pink flamingoes on. " },
                { author: "16:00 Luca Giovenzana, Angelo Caovilla",
                  title: "Beware the Brittle Dragon",
                  descriptionExpanded: "At the beginning there was chaos; manual tests ruled the world. A chosen few showed the automating path, the light was seen and everyone started to write automation disregarding the prophecy. But soon their weapons raised up against themselves and waken the Brittle Dragon. Automation was abandoned...<br><br>Everyone that is used to test automation knows that having automated tests is not enough to get real value from them. In order to put a test suite in a continuous test cycle many different aspects of the tests need to be considered. We've been recently passed through the Calvary of rewrite, fix, optimize our suite of 1000+ test cases we want to share what we learned.",
                  bio: "<h3 class='mb-0 mt-2'>Luca Giovenzana</h3>I'm an Open Source and Linux passionate guy.<br><br>I worked for 9 years in a security company www.endian.com that build up from scratch an Open Soucre Linux distribution. <br><br>At Endian I discovered RobotFramework but never used since we already have created our own testing framework in python, based on unittest and around fabric library to remotely control via ssh our firewalls.<br>2 years ago I moved to a shining streaming company www.chili.com where I made up a 7 people QA team and initiated the company to test automation with RobotFramework.<br><br>The whole team enjoyed RF, me and Angelo attended the 2019 RoboCon edition. Back in Italy we started contributing and founded RobotFramework Italy/Milan Meetup.<br><br>I'm now an active contributor to RequestsLibrary, I'm very exited about it!" },
                { author: "16:30", title: "Break" },
                { author: "17:00", title: "Lightning talks", descriptionExpanded: 'Topic of the day, you decide! Sign-up your name, topic, and contact information to the lightning talk list at the venue during the conference day and get ready to present a 10 minute lightning talk on the big stage.' },
                { author: "18:00", title: "Dinner and networking", descriptionExpanded: 'After the exciting conference day you still have a change to chat and mingle with your old and new Robot-friends. There is food available (included into the conference ticket) and the bar is open (own costs). <br><br>We also have <a href="https://www.esgrove.fi/" target="blank">DJ Esgrove</a> (<a href="https://soundcloud.com/dj-esgrove" target="blank">SoundCloud</a>, <a href="https://www.mixcloud.com/djesgrove/" target="blank">Mixcloud</a>) a.k.a. Akseli Lukkarila, playing some cool disco/funk/house/lounge tunes for us. All this happens at Bio Rex, our conference venue, so there\'s no need to move anywhere.' },
                { author: "22:00", title: "Venue closes" },
                { header: 'Thursday, January 16', margin: true },
                { author: "08:00", title: "Doors open, registration, breakfast" },
                { author: "09:00 Pekka Klärck & Ismo Aro",
                  title: "Keynote: What's new? What's next? Who are we?",
                  descriptionExpanded: "In his keynote Pekka & Ismo will take a look at the Robot Framework community at large. We will first learn how the organization behind the funding of Robot Framework is doing. Then about the latest enhancements and the planned future features of Robot Framework and its ecosystem. Once we know where we are coming from and where we are going to, we will look who we are. What kind of domains is Robot Framework used at? Is it used for testing or other kind of automation? Where is everyone coming from?",
                  bio: "<h3 class='mb-0 mt-2'>Pekka Klärck</h3>Pekka Klärck is a tester, developer and independent consultant from Finland with experience from testing and test automation since 2000. He is the original author and lead developer of Robot Framework.<br><br><h3 class='mb-0 mt-2'>Ismo Aro</h3>Ismo Aro is the Chairman of the Board in Robot Framework Foundation and a Partner/CTO at NorthCode. He has a long track record of working in software projects as a change agent." },
                { author: "10:00", title: "Break" },
                { author: "10:30 Akseli Lukkarila",
                  title: "Acceptance testing a real-time music education application with audio",
                  descriptionExpanded: "<b>How to do automated acceptance testing when the input and output is sound?</b><br><br><a href='https://yousician.com' target='blank'>Yousician</a> is a cross-platform music education application for guitar, bass, piano, ukulele and singing. Millions of people around the world from total beginners to expert musicians use Yousician to advance their music skills and play the music they love. Yousician analyses the user's playing on their real musical instrument, and provides them with instant feedback and guidance.<br><br>One year ago, we started a project at the company to develop an automated acceptance testing system that would be able to validate our Unity-based main application <b>Yousician</b>, and our musical instrument tuner app GuitarTuna using real audio input on real devices from Android and iOS to Mac and Windows computers. To accomplish this, we created our own audio signal generation, playback and recording library for Robot framework, implemented in Python with NumPy and PyAudio. The physical test setup consists of an array of custom-build acoustically sealed test boxes and multiple audio interfaces, that enable parallel test runs with independent audio playback and recording for each individual smart device.<br><br>This talk will present how we implemented our acceptance testing system using Robot framework and Jenkins, and gives general insights for audio-based testing using Robot.",
                  bio: "Akseli Lukkarila is a software engineer and audio specialist based in Helsinki, Finland. In his relatively short but highly interesting career after graduating from <i>Aalto University</i> with a Master’s degree in acoustics and audio technology, he’s already worked on automatic speech recognition applications at Aalto, done game audio programming at <i>Remedy Games</i>, and currently works as a test automation developer at <i>Yousician</i>, the largest and fastest growing music education company in the world. In addition, Akseli has been deejaying and doing practical audio engineering professionally for over a decade, and hosted a biweekly radio show for eight years on <i>Basso</i>, the foremost urban and electronic music radio station in Finland." },
                { author: "11:00 Maria Prokhorova",
                  title: "New Image Library for advanced image processing",
                  descriptionExpanded: "Hi, my name is Maria. I am a QA automation engineer at XOOOX Games. <br><br>In this talk I would like to introduce a new RobotFramework Image Library for UIs automation requiring analysis and information extraction from graphical entities. The library provides automation for various graphical testing objects.<br><br>The library was designed from needs of our own product; the need of automated testing (with RobotFramework) of the graphical application containing slots games and 10 interfaces. Due to the specifity of the application there is no other way to check the events than processing the screenshots.<br><br>The new Image Library's aim is to help automate UIs, inside the RobotFramework system avoiding integrating external tools and waiting for support. The idea of this library is to get a powerful tool which will be constantly upgrading and extending the keywords power." },
                { author: "11:30", title: "Lunch" },
                { author: "12:30 Tatu Aalto",
                  title: "SeleniumLibrary 4.0: Plugin API and Event Firing WebDriver support",
                  descriptionExpanded: "The SeleniumLibrary 4.0 allows user new ways to build on top of the SeleniumLibrary, without the need to build new library on top of the SeleniumLibrary. This presentation explains how to use plugin API and the Event Firing WebDriver with short demos.<br><br>Before the SeleniumLibrary 4.0, users needed to build new libraries on top of the SeleniumLibrary if they wanted to expand or modify the SeleniumLibrary functionality.  Also user needed to build some boiler plate code the have IDE support and to ease access the SeleniumLibrary public API. Like the popular <a href='https://github.com/Selenium2Library/robotframework-angularjs' target='blank'>AngularJSLibrary</a>. <br><br>Now with the SeleniumLibrary 4.0 release, the plugin API allows adding and modifying keywords directly in the SeleniumLibrary. Also with plugins SeleniumLibrary allows public interface to some internal methods which have been private in the past. As second major update, SeleniumLibrary now supports <a href='https://seleniumhq.github.io/selenium/docs/api/py/webdriver_support/selenium.webdriver.support.event_firing_webdriver.html#module-selenium.webdriver.support.event_firing_webdriver' target='blank'>Event Firing WebDriver</a>, which is a listener like interface for the low level Selenium API calls. <br><br>The aim of the presentation is introduce the new capabilities of the SeleniumLibrary with demos and how it enables user to better stay in control of the test automation in the browser UI.",
                  bio: "Tatu Aalto is the current lead developer of the <a href='https://github.com/robotframework/SeleniumLibrary' target='blank'>SeleniumLibrary</a> and he has been working with Robot Framework since 2011. In the 2011 he was a regular user, by sending many questions and problems to the community. After some time Tatu started to answer questions  send by other users and he did provide his very first pull request to the Robot Framework core in 2012. Tatu has been active community member all these years and 2016 he started as an SeleniumLibrary lead developer.<br><br>Tatu has used the Robot Framework in several work places to to guide and aid companies in their test automation efforts. Currently he is working in F-Secure as a Software Developer In Test, automating windows antivirus client for business users." },
                { author: "13:00 René Rohner",
                  title: "DataDriver or: How I learned to stop worrying and love open source",
                  descriptionExpanded: "This talk shows how to handle Data-Driven Testing with Robot Framework if you have a larger amount of test data combinations and if you need to maintain them.<br><br>I also tell a story of how the contribution to RobotFramework's ecosystem evolved for me and the result: DataDriver Library.<br><br><a href='https://github.com/Snooz82/robotframework-datadriver' target='blank'>DataDriver</a> is a library that enables Robot Framework to load data from csv, xlsx or any other external data source.<br><br>It will be shown how easy it is to take DataDriver into use and how to do DataDriven Testing. We will also have look into DataDriver's Plugin API, which enables users to implement their own DataReaders, if they need to fetch test data from different sources.",
                  bio: "René Rohner is a Senior Consultant for Testing Systems in Germany and member of the board of Robot Framework Foundation.<br><br>He has over 6 years of experience with Keyword-Driven and Behavior-Driven Testing in multiple small and huge projects in Germany." },
                { author: "13:30", title: "Break" },
                { author: "14:00 Tommi Oinonen",
                  title: "Self managing testing pipelines",
                  descriptionExpanded: "Wouldn't you like to have a testing pipeline that fails fast by automatically running first the test cases that are effected by the changes you just made? What about a pipeline that schedules test runs according to availability of test environments?<br><br>These are examples of smart autonomous testing pipelines can work and how the simplest test managing decisions could be done by the testing pipelines. These things are not that difficult to implement but a small paradigm shift might be needed. I have been working on techniques that would allow the simplest day-to-day test management decisions to be done by the testing pipeline itself. Such automation can be achieved using machine learning or even the simplest of algorithms.<br><br>While prototyping and trying to help others to leverage such algorithms and machine learning that would allow for e.g. automatic smart test prioritization and optimal resource usage, I have encountered a couple of obstacles that make the transition difficult or impossible for many teams. These are related on how the pipelines are used and how they are build. I would like to share with you how to get past these obstacles and make your testing pipeline ready for the next level of automation. Robot Framework is an excellent tool with many features that can help you get past these obstacles if you just know how to use it appropriately.<br><br>I will be sharing a very simple demo of a test prioritization algorithm that we have been working on to demonstrate these issues and possibilities of the algorithms. The algorithm is especially suitable for acceptance testing and system testing since it does not require any explicit code coverage or model data.",
                  bio: "Tommi Oinonen has six years of experience in test automation and supporting teams with testing infrastructure and reporting.<br><br>Currently working as a consultant at Siili Solutions in Software Automation Laboratories (SALabs) unit. SALabs is aiming to move both state-of-the-practice and state-of-the-art of software automation using and developing open source tools and technologies.<br><br>For the last two years researching and implementing test prioritization techniques as part of the TESTOMAT project."
                },
                { author: "14:30 Juho Saarinen",
                  title: "Robot Framework Remote library in practice (with demos)",
                  descriptionExpanded: "In the talk I'll present Robot's Remote Library, and then show demos how that can be used to e.g. create dynamic free environment to the GCP's AppEngine, 'hide' credentials to access services or offer a way to access services that are not directly accessible from current network.",
                  bio: "Juho has been doing testing since 2005. He is interested of testing and it's efficiency, and eager to make all kind of testings as soon as possible.<br><br>Juho maintains various java-based RF libraries.<br><br>His 'normal working day' to contain also application development and various operations related things in addition to testing."
                },
                { author: "15:00", title: "Break, coffee" },
                { author: "15:30 Joonas Köppä, Riku Halonen",
                  title: "Orchestrating Robot Framework test containers and remote libraries in Kubernetes",
                  descriptionExpanded: "Kubernetes enables building a distributed testing environment with remote keyword libraries and disposable test containers. This session displays how Robot Framework tests and keyword libraries can be deployed and run in Kubernetes to build powerful acceptance testing as part of a CI/CD pipeline.<br><br>The presentation includes high level diagrams and explanations of how different test automation and containerization technologies are used in our Robot Framework testing. We will also talk about the structure of our current remote library implementation followed by a short demo of actually deploying a new version of a service and having it tested. <br><br>Keywords: Robot Framework, remote libraries, Jenkins, Docker, Kubernetes",
                  bio: "<h3 class='mb-0 mt-2'>Joonas Köppä</h3>Joonas Köppä is working as a Senior Software Engineer at OpenText, working on implementing efficient and modern test automation procedures with the main focus on testing cloud based micro services.<h3 class='mb-0 mt-2'>Riku Halonen</h3>Riku has total of 15 years of software engineering experience e.g. from mobile, machine control and cloud product industry. Currently, Riku is working as a Sr. Manager and DevOps/ Test Automation lead at OpenText engineering department for cloud products." },
                { author: "16:00 Maciej Brzozowski",
                  title: "Microservices testing using Argo: container-native workflows for Kubernetes",
                  descriptionExpanded: "The team decides to use Kubernetes in the project. How are you going to test it? Docker Compose? Is there anything else more suitable? The answer is Argo, container-native workflow engine for orchestrating jobs on Kubernetes. Together with Robot Framework you can perform all your testing scenarios.",
                  bio: "Software developer focused on test automation. Currently working as Senior Software Developer in Big Data department at Nordea Bank in Gdynia, Poland. Enthusiast of Python and Kubernetes." },
                { author: "16:30", title: "Break" },
                { author: "17:00", title: "Lightning talks", descriptionExpanded: 'Topic of the day, you decide! Sign-up your name, topic, and contact information to the lightning talk list at the venue during the conference day and get ready to present a 10 minute lightning talk on the big stage.' },
                { author: "18:00", title: "Networking" },
                { author: "19:00", title: "After party at Vala", description: 'Official after party at Vala offices close to the conference venue at <a target="blank" href="https://goo.gl/maps/UNh2MSy24BU2">Erottajankatu 11 B</a>. <br><br>Sign up for the afterparties <a href="https://spiikresearch.typeform.com/to/IenZT9" target="blank">here</a>!' }
              ]
            }
          }
        },*/
        /*{
          title: "Tickets",
          text_block: false,
          text_block_centered: true,
          tab_box: false,
          feature_box: false,
          data: {
            text: {
              twitter: false,
              header: "Tickets",
              text:
                '<p><a href="https://www.lyyti.in/Robocon_2020_6339" target="blank">Tickets available here!</a></p> <table style="width: 100%; display: flex; margin-top: 10px"><tr><th></th><th>1 day</th><th>2 days</th><th>Available until</th></tr><tr><td><del>Blind Robot</del></td><td>-</td><td><del>600€</del></td><td><del>2019-09-30</del></td></tr><tr><td><del>Early Robot</del></td><td><del>600€</del></td><td><del>900€</del></td><td><del>2019-12-31</del></td></tr><tr><td>Late Robot</td><td>800€</td><td>1200€</td><td>2020-01-15</td></tr></table><br><p>All prices are exclusive of 24 % VAT. <a href="#workshops">Workshop</a> tickets are sold separately.</p>'
            }
          }
        },*/
        {
          title: "Workshops",
          text_block: false,
          text_block_centered: true,
          tab_box: false,
          feature_box: false,
          user_box: false,
          user_box_centered: false,
          data: {
            text: {
              twitter: false,
              header: "Workshops",
              text: `<p>Date: December 02, 2020<br>Location: The World Wide Web.<br>
              Detailed information will be sent to workshops participants separately.<br>
              <br>Ticket sale starts on Wednesday, November 4, at 08:00 UTC.</p>
              <p>
              Prices:<br>
              <br>
              Workshops in East Asia / Oceania time zones (UTC +12 to UTC +8):</p>
              <table style="width: 100%; display: flex; margin-top: 0; margin-bottom: 5px">
                <tr>
                  <th></th>
                  <th>Supporter</th>
                  <th>Standard</th>
                  <th>Budget *</th>
                </tr>
                <tr>
                  <td>Half-day</td>
                  <td>400€</td>
                  <td>200€</td>
                  <td>100€</td>
                </tr>
                <tr>
                  <td>Full-day</td>
                  <td>800€</td>
                  <td>400€</td>
                  <td>200€</td>
                </tr>
              </table>
             
              <p>Workshops in Central Asia / India time zones (UTC +7 to UTC +4):</p>
              <table style="width: 100%; display: flex; margin-top: 0; margin-bottom: 5px">
                <tr>
                  <th></th>
                  <th>Supporter</th>
                  <th>Standard</th>
                  <th>Budget *</th>
                </tr>
                <tr>
                  <td>Half-day</td>
                  <td>300€</td>
                  <td>100€</td>
                  <td>50€</td>
                </tr><tr>
                  <td>Full-day</td>
                  <td>500€</td>
                  <td>200€</td>
                  <td>100€</td>
                </tr>
              </table>

              <p>Workshops in Europe / Africa / America time zones (UTC +3 to UTC -12):</p>
              <table style="width: 100%; display: flex; margin-top: 0; margin-bottom: 5px">
                <tr>
                  <th></th>
                  <th>Supporter</th>
                  <th>Standard</th>
                  <th>Budget *</th>
                </tr>
                <tr>
                  <td>Half-day</td>
                  <td>600€</td>
                  <td>300€</td>
                  <td>150€</td>
                </tr><tr>
                  <td>Full-day</td>
                  <td>1000€</td>
                  <td>500€</td>
                  <td>300€</td>
                </tr>
              </table>
              <p style="font-size: 0.95rem">*) Budget Tickets are for anyone who can not afford normal ticket price. Just send an email to <a href="mailto:rene@robotframework.org">Ren&eacute;</a> or contact me on slack @Ren&eacute; and you get a voucher code to buy a budget ticket. No questions! No explanation requested!</p>`,
              /*<a class="col-sm-12 pl-0 mb-5 mt-3" href="https://www.lyyti.fi/reg/robocon2020workshops" target="blank">Tickets available here!</a>`,*/
              talks: [
                { type: "workshop", header: 'Half-day workshops' },
                { type: "workshop", author: "Kamal Girdher",
                  title: "🇬🇧 Introduction to Robot framework [India/EN]",
                  description: "Basic workshop for robot framework beginners.",
                  descriptionExpanded: `<h3>Section 1 - Introduction & Installation</h3>
                    <b>Duration:</b> 10-15 minutes<br>
                    Introduction to Robot framework<br>
                    Edge of Robot framework over other automation tools/frameworks<br>
                    Installation<br>
                    <h3>Section2 - Key Concepts</h3>
                    <b>Duration:</b> 40 mins lecture 30 minutes for practice/questions<br>
                    Test cases, Test Suite and User Keywords<br>
                    Built-in Library<br>
                    Scalars, Lists, Dictionaries and Variable files<br>
                    Suite/Test setup teardown<br>
                    External resources<br>
                    Loop statements<br>
                    Conditional functions<br>
                    <h3>SECTION 3 - SeleniumLibrary</h3>
                    <b>Duration:</b> 1 Hr + 40 mins practice<br>
                    Introduction to Selenium & SeleniumLibrary<br>
                    Object Identification techniques<br>
                    Operations on web elements<br>
                    Wait statements<br>
                    Assertions<br>
                    Switching to windows and popups<br>
                    Switching to frames<br>
                    Handling Alerts`,
                  bio: "<h3 class='mb-0 mt-2'>Kamal Girdher</h3>" ,
                  imgUrl: ["Kamal_Girdher.jpg"]
                },
                { type: "workshop",
                  author: "René Rohner",
                  title: "🇩🇪 Browser library für SeleniumLibrary User [Germany/DE]",
                  description: "Einführung in die brandneue Robot Framework Browser library für alle Nutzer*Innen der SeleniumLibrary mit Vorkenntnissen in Web-Automatisierung.",
                  descriptionExpanded: "Die brandneue Robot Framework Browser library is eine top moderne Web-Automatisierungsbibliothek basierend auf Microsofts neuer Web-Automatisierungstechnologie Playwright. Dieser Halbtages-Workshop ist für alle Nutzer der SeleniumLibrary mit Vorkenntnissen in Web-Automatisierung.",
                  bio: "<h3 class='mb-0 mt-4'>René Rohner</h3>René Rohner is a Senior Consultant for Testing Systems in Germany and member of the board of Robot Framework Foundation.<br><br>He has over 6 years of experience with Keyword-Driven and Behavior-Driven Testing in multiple small and huge projects in Germany." ,
                  imgUrl: ["Rene_Rohner.png"]
                },
                { type: "workshop",
                  author: "René Rohner",
                  title: "🇩🇪 Robot Framework Advanced [Germany/DE]",
                  description: "Einführung in die APIs des Robot Framework. Listener, Pre-Run-Modifier, etc. ",
                  descriptionExpanded: "Robot Framework bietet manigfaltige APIs um Tests vor oder währen der Ausführung zu verändern, Tests live mitzulesen, Testprotokolle zu manipulieren oder Bibliotheken zu Entwickeln oder zu Dokumentieren. Dieser Workshop gibt einen guten Überblick über wichtigsten APIs des Robot Framework. Python Basiskenntnisse werden vorausgesetzt.",
                  bio: "<h3 class='mb-0 mt-4'>René Rohner</h3>René Rohner is a Senior Consultant for Testing Systems in Germany and member of the board of Robot Framework Foundation.<br><br>He has over 6 years of experience with Keyword-Driven and Behavior-Driven Testing in multiple small and huge projects in Germany." ,
                  imgUrl: ["Rene_Rohner.png"]
                },
                { type: "workshop",
                  author: "Nils Balkow-Tychsen",
                  title: "🇬🇧 KubeLibrary - Verify the state of objects in your Kubernetes Cluster [Germany/EN]",
                  description: "RobotFramework library for testing Kubernetes cluster.",
                  descriptionExpanded: "KubeLibrary is a Robot Framework test library for Kubernetes.<br><br>KubeLibrary is a wrapper for the Python Kubernetes Client. It enables you to assert the status of various objects in your Kubernetes Clusters. As the library can be integrated with any RobotFramework test suite, it is ideal to verify the testability of your System-under-Test by asserting the status of your nodes, deployments, pods, configmaps, and others Kubernetes objects before running any end to end tests.",
                  bio: "<h3 class='mb-0 mt-4'>Nils Balkow-Tychsen</h3>Nils is Lead QA Engineer at Humanitec. He has worked in software testing for more than 20 years, in different industries like finance, games and developer platforms. He specializes in test automation for web apps based on Microservice Architectures.",
                  imgUrl: ["Nils_Balkow.jpeg"]
                },
                { type: "workshop",
                  author: "Michael Hallik",
                  title: "🇳🇱 HTTP-level testing with the RF RequestsLibrary [Netherlands/NL]",
                  description: "RobotFramework library for testing Kubernetes cluster.",
                  descriptionExpanded: `<p><b>Language:</b> Workshop will be in Dutch.</p>
                  <p>Experience the power, versatility and simplicity of Robot Framework. In this workshop you will learn the basics of HTTP-level test automation. We will cover everything from creating and maintaining an HTTP session, to validating every aspect of the response and everything in between.</p>
                  <ul>
                    <li style="margin-bottom: 0;">Use cases for HTTP-level test automation.</li>
                    <li style="margin-bottom: 0;">HTTP compared to other API-level test automation interfaces (e.g. SOAP).</li>
                    <li style="margin-bottom: 0;">Web-api vs. REST-api.</li>
                    <li style="margin-bottom: 0;">Overview HTTP support within the RF ecosystem (all libraries compared).</li>
                    <li style="margin-bottom: 0;">RequestsLibrary: it's place in a typical RF tool stack (architectural overview).</li>
                    <li style="margin-bottom: 0;">Installation RequestsLibrary.</li>
                    <li style="margin-bottom: 0;">Creating and maintaining an HTTP session with RequestsLibrary.</li>
                    <li style="margin-bottom: 0;">The session object: exposed methods, attributes and how to access them.</li>
                    <li style="margin-bottom: 0;">The session object: various ways to manipulate it (e,g, def headers, cookies).</li>
                    <li style="margin-bottom: 0;">Making HTTP requests with RequestsLibrary (based on our session object).</li>
                    <li style="margin-bottom: 0;">The response object: exposed methods, attributes and how to access them.</li>
                    <li style="margin-bottom: 0;">Validate the response:</li>
                    <ul>
                    <li style="margin-bottom: 0;">status code and message</li>
                    <li style="margin-bottom: 0;">headers</li>
                    <li style="margin-bottom: 0;">cookies</li>
                    <li style="margin-bottom: 0;">the cookieJar object</li>
                    <li style="margin-bottom: 0;">the response body</li>
                    </ul>
                  </ul>

                  <b>Required knowledge:</b>
                  <ul>
                    <li style="margin-bottom: 0;">Robot Framework - Good Knowledge</li>
                    <li style="margin-bottom: 0;">HTTP concepts - Basic Knowledge</li>
                    <li style="margin-bottom: 0;">Object oriented programming concepts - Basic Knowledge</li>
                  </ul>`,
                  bio: "<h3 class='mb-0 mt-4'>Michael Hallik</h3>",
                  imgUrl: ["Michael_Hallik.jpeg"]
                },

                { type: "workshop", header: 'Full-day workshops', margin: true },
                { type: "workshop", author: "Mikko Korpela",
                  title: "🇬🇧 Pabot Introduction / Tipps & Tricks [Finland/EN]",
                  description: "A hands-on introduction to parallel test execution with Robot Framework and Pabot.",
                  descriptionExpanded: "Introduction to parallel test execution with Pabot.",
                  bio: "<h3 class='mb-0 mt-2'>Mikko Korpela</h3>Mikko Korpela is a consultant and former core developer of Robot Framework. He invented the awesome Pabot." ,
                  imgUrl: ["Mikko_Korpela.png"]
                },
                { type: "workshop",
                  author: "Tatu Aalto",
                  title: "🇬🇧 SeleniumLibrary (Advanced) [Finland/EN]",
                  description: "Techniques and tooling to ease up web testing and automation by expert developers and maintainer of the SeleniumLibrary. If you need to beef up your Selenium tests, this is the course for you.",
                  descriptionExpanded: "<h2 class='no-arrow mb-3 mt-5'>Outline/overview of the workshop</h2><h3 class='mb-0 mt-2'>Browser Configuration</h3>We will be taking a look at desired capabilites, Selenium options and Firefox profile. Differences between Open Browser and Create WebDriver keywords will be highlighted. Finally we will build small examples showing how to configure the browser in diffrent situations.<h3 class='mb-0 mt-2'>Advanced Debuging</h3>The course will cover when encountering flaky test(s), where to look and how to stabilise them.<h3 class='mb-0 mt-2'>Parallel Execution</h3>We'll discuss running SeleniumLibrary in parallel with pabot and Selenium grid.<h3 class='mb-0 mt-2'>API</h3>SeleniumLibrary has an public API which allows users to extend on top of the SeleniumLibrary. Here we take a look what is available in the public API.<h3 class='mb-0 mt-2'>Expanding the library</h3>Looking at different pros and cons we will talk about how to extend SeleniumLibrary as well as building a new library and the Plugin API. We will show a small exmample. And we will discuss overriding existing keywords with functionality not covered by Selenium.<h3 class='mb-0 mt-2'>EventFiringWebDriver</h3>Using and abusing EventFiringWebDriver for monitoring events and how they affect the interactions with SUT will be covered.<h3 class='mb-0 mt-2'>Page Objects</h3>What are page objects and where it might be useful.<h3 class='mb-0 mt-2'>Python Page objects verses SeleniumLibrary</h3>Looking inside of a page object library and how to build one.<h3 class='mb-0 mt-2'>Checking for time of tests</h3>We will talk about verifying and reacting to execution times of tests/keywords/suites either via tags or the separate Timer library.<h3 class='mb-0 mt-2'>Using Javascript to interact with SUT</h3>Extending SeleniumLibrary with new keywords where functionality is implemented in Javascript.<h2 class='no-arrow mb-3 mt-5'>Learning Outcomes</h2>At the end of the workshop, user should have broad overview of advanced features of SeleniumLibrary, web automation and ways to extend and debug test tooling.<h2 class='no-arrow mb-3 mt-5'>Target Audience</h2>This workshop is for people with previous hands on experience with testing in Robot Framework & SeleniumLibrary. Students should already have experience testing web applications, know how to identify locators for webelements and validate those loctors, and feel comfortable working with SeleniumLibrary. Although the course will take a measured pace through the material, students should be prepared for advanced topics that will be thoroughly explained.<br><br>This workshop will be presented in English with two presentors, both who are bi-lingual in Finnish and English.<h2 class='no-arrow mb-3 mt-5'>Prerequisites</h2>* All participates will need to bring a laptop preconfigured to the workshop.<br>* Particapte must have access to add and modify software on their laptops.<br>* Detailed setup instructions will be shared couple of weeks before workshop day.<br>* Configure your laptops well before the workshop day<br><br>Any special needs should be requested through the conference organizers, at best two weeks prior to the workshop. We will do our best to accomidate any needs and will communicate back either our ability or inability to meet those needs.",
                  bio: /*`
                  <h3 class='mb-0 mt-4'>Ed Manlove</h3>
                  Ed Manlove has been a part of the Robot Framework community since 2011. He inherited the leadership of the Selenium2Library project from Ryan Tomac sharing it with Jeremy Johnson and passing on that role to Tatu Aalto. He is the author of a couple libraries dealing with timing issues within AJAX enabled websites. Ed is currently a Senior Software Test Engineer at Cox Automotive testing with Robot Framework and taught several teams how to test with Robot Framework. A member of the Selenium user community Ed has presented at the Selenium Conference, ran an unconference focusing on user issues, and volunteered at the conferences (even being a maître d').
                  */`<h3 class='mb-0 mt-5'>Tatu Aalto</h3>
                  Tatu Aalto is the current lead developer of the <a href='https://github.com/robotframework/SeleniumLibrary' target='blank'>SeleniumLibrary</a> and he has been working with Robot Framework since 2011. In the 2011 he was a regular user, by sending many questions and problems to the community. After some time Tatu started to answer questions  send by other users and he did provide his very first pull request to the Robot Framework core in 2012. Tatu has been active community member all these years and 2016 he started as an SeleniumLibrary lead developer.<br><br>Tatu has used the Robot Framework in several work places to to guide and aid companies in their test automation efforts. Currently he is working at F-Secure as a Software Developer In Test, automating windows antivirus client for business users.` ,
                  imgUrl: ["Tatu_Aalto.jpg"]
                },
                { type: "workshop",
                  author: "Pekka Klärck",
                  title: "🇬🇧 Extending Robot Framework (Advanced) [Finland/EN]",
                  description: "In this workshop you will learn how to extend Robot Framework using various different interfaces.",
                  descriptionExpanded: "This workshop is for you if you already know basics of using Robot Framework, preferably also basics of writing tests libraries, and want to take your skills to the next level. These skills make it easier to adapt the framework to your own needs in different contexts.<br><br>The workshop is 100% hands-on, no slides, learn-by-doing. In addition to learning from the person who has designed these powerful APIs, you have a change to ask hard questions related to Robot Framework from its creator.<br><br>Participants should know basics of Robot Framework, including test library API, and Python programming. Participants should bring their own laptop with Python 3.6 or newer and Robot Framework 3.2 or newer installed. They should also have adequate admin rights to install possible additional Python modules using pip. A text editor or an IDE for writing Python code and Robot Framework tests is needed as well.<br><br><h3>Recommended for advanced users.</h3><h3>Max number of participants: 16</h3>",
                  bio: "Pekka Klärck is a tester, developer and independent consultant from Finland. He is the original author and lead developer of Robot Framework.",
                  imgUrl: ["Pekka_Klarck.jpg"]
                },
                { type: "workshop",
                  author: "Christoph Singer",
                  title: "🇩🇪 Einführung Webautomatisierung mit RF Browser [Germany/DE]",
                  description: "Einführung in die Webautomatisierung mit der brandneuen Robot Framework Browser library für alle Interessierte.",
                  descriptionExpanded: "Grundlagenschulung in Webautomatisierung. Von XPATH bis CSS Selektoren und von 'Open Browser' bis 'Execute Javascript' wird in diesem Grundlagen-Workshop alle nötige Basiswissen vermittelt was zum Einstieg in die Browserautomatisierung notwendig ist. Unter Nutzung der neuen Browser library werden wir ein Beispiel Testobjekt automatisieruen und dabei typische Probleme lösen lernen.",
                  bio: "<h3 class='mb-0 mt-4'>Christoph Singer</h3>Christoph Singer is a Consultant for Test Automation in Germany.",
                  imgUrl: ["ChristophSinger.jpg"]
                },
                { type: "workshop",
                  author: "Juho Saarinen",
                  title: "🇬🇧 Remote library usage and advantages [Finland/EN]",
                  description: "Learn first basics about remote library interface, and then how to make own libraries that utilize it.",
                  descriptionExpanded: "At the latter part of the day we go through running remote libraries really remote (meaning not on “my machine”), and what advantages that brings.<br><br>Also showing what to do with the Java libraries when Python 2 support is dropped and no suitable replacement available.",
                  bio: "Juho has been doing testing since 2005. He is interested of testing and it's efficiency, and eager to make all kind of testings as soon as possible.<br><br>Juho maintains various java-based RF libraries.<br><br>His 'normal working day' to contain also application development and various operations related things in addition to testing.",
                  imgUrl: ["Juho_Saarinen.jpg"]
                },
                
              ]
            }
          }
        },
        /*{
          title: "Sprints",
          text_block: false,
          text_block_centered: true,
          tab_box: false,
          feature_box: false,
          data: {
            text: {
              twitter: false,
              header: "Sprints",
              text: "<div><p>Date: January 17, 2020<br>Start time: 10:00<br>Location: Eficode, <a href='https://goo.gl/maps/h3FYLAHAW8TCvadX6' target='blank'>Pohjoinen Rautatiekatu 25</a><br><br>After the main conference we still have development sprints on Friday. Sprints are for you if you want to contribute to some existing project in Robot Framework ecosystem, have a project or project idea you'd like to work with others, or just want to meet with other Robot Framework users and developers.<br><br>Sprints are free of charge and open for everyone. No sign-up is needed so you can just pop by, but please bring your conference badge and show it at the door. Joining sprints is possible also if you cannot participate the conference, but please send an email to info@robocon.io beforehand in that case. Lunch and beverages will be provided and we'll also have sauna afterwards!<br><br>Some existing projects that are known to be present at the sprints are listed below. If you have a project to be added to the list, send an email to info@robocon.io or simply come to the sprints and present your project there.<br><br>- <a target='blank' href='https://github.com/robotframework/robotframework'>Robot Framework</a><br>- <a target='blank' href='https://github.com/robotframework/SeleniumLibrary/'>SeleniumLibrary</a><br>- <a target='blank' href='https://robots-from-jupyter.github.io/'>RobotLab</a><br>- <a target='blank' href='https://github.com/Snooz82/robotframework-datadriver'>DataDriver</a><br>- <a target='blank' href='https://github.com/Omenia/robotframework-whitelibrary'>WhiteLibary</a><br>- <a target='blank' href='https://robotframework.org/MavenPlugin/'>MavenPlugin</a> and other Java tooling<br>- <a target='blank' href='https://github.com/bulkan/robotframework-requests'>RequestsLibrary</a><br><br>Project maintainers are advised to add common <code>good first issue</code> and <code>help wanted</code> labels to issues they believe are good for new contributors and to issues they'd especially like someone to help with, respectively. Participants can use these labels to find suitable issues for them, but they are obviously free to work with anything they feel interesting. Many of the tasks are likely to involve coding, but there certainly are also non-coding tasks like testing, documentation and work with infrastructure like CI.</p> <p>If you are new to contributing to open source, we recommend you to take a look at the <a target='blank' href='https://opensource.guide/how-to-contribute/'>How to Contribute to Open Source</a> guide. Individual projects typically also have their own contribution guidelines that you can find via their project pages. We'll also have a dedicated session for new contributors at the sprints.<br><br><p><h3 class='mb-0 mt-4'>ROUGH AGENDA:</h3></p><p>10:00 - Welcome! Introduction to participating projects and tasks they have available.</p> <p>10:30 - Development! Participants can work with tasks they find interesting either alone, in pairs, or in small groups. Project leaders help as much as they can.</p><p>10:30 - Introduction to contributing to open source session for interested new contributors.</p><p>12:30 - Lunch (most likely pizza).</p><p>15:30 - Presenting what has been accomplished.</p> <p>16:00 -  Official program ends. Sauna opens. Coding can continue.</p></div>"
            }
          }
        },
        {
          title: "Arrival",
          text_block: false,
          text_block_centered: true,
          tab_box: false,
          feature_box: false,
          data: {
            text: {
              twitter: false,
              header: "Arrival",
              text:
                "<div><p>The main conference venue is Bio Rex, <a href='https://goo.gl/maps/gnd4duvnunP2' target='blank'>Mannerheimintie 22-24</a>. Pre-conference workshops are organize at Siili, <a href='https://goo.gl/maps/CPUAifmpZ56sTUaH9' target='blank'>Ruoholahdenkatu 21</a>, and post-conference sprints at Eficode, <a href='https://goo.gl/maps/h3FYLAHAW8TCvadX6' target='blank'>Pohjoinen Rautatiekatu 25</a>.</p><h2 class='no-arrow'>TRANSPORTATION: AIRPORT</h2><p>The distance from Helsinki airport to Bio Rex is 21 km. Trains marked as “I” and “P” go from the airport to Helsinki Central Station. From the Helsinki Central Station it is only 5 minutes' walk to Bio Rex.</p><p>Buses operate between Helsinki airport and Helsinki Central Station. The bus stops for both arriving and departing buses are located in front of the terminals (T1 & T2). Finnair bus goes from airport to Eliel Square and bus nr. 615 goes from airport to Rautatientori. There is a short walk to Bio Rex from both Eliel Square (300 meters) and Rautatientori (350 meters).</p><p>Time estimation for the journey is 40 minutes by bus and about 30-35 minutes by train or taxi. Taxi cost is approximately 40-55 euros depending on the traffic and the taxi company.</p><p>At Helsinki airport there are informative signage for trains, buses and taxis to ensure that you won’t get lost.</p><h2 class='no-arrow'>TRANSPORTATION: RAILWAY STATION</h2><p>Railway station is only 5 minutes’ walk (350 meters) from Bio Rex. To reach Siili's and Eficode's offices you can either walk or go one stop to Kamppi with the metro departing from Railway station.</p><h2 class='no-arrow'>TRANSPORTATION: BUS STATION</h2><p>Intercity bus connections from Kamppi bus station (400 meters away) and bus connections for Helsinki's internal traffic from Rautatientori (350 meters) located close to Helsinki Central Station. Buses to Helsinki Airport leave from Eliel Square (300 meters) and Rautatientori (350 meters).</p></div>"
            }
          }
        },
        {
          title: "Accommodation",
          text_block: false,
          text_block_centered: true,
          tab_box: false,
          feature_box: false,
          data: {
            text: {
              twitter: false,
              header: "Accommodation",
              text:
                "<div><h2 class='no-arrow'>Hotel deals</h2><p><a href='https://www.sokoshotels.fi/en/helsinki/sokos-hotel-presidentti' target='blank'>Original Sokos Hotel Presidentti</a><br>- Standard single room: 150€ / night<br>- Standard double room: 170€ / night<br>- Breakfast and Wi-Fi included<br>- Promo code will be sent after ticket purchase</p></div>"
            }
          }
        },*/
        {
          title: "CoC",
          text_block: false,
          text_block_centered: true,
          tab_box: false,
          feature_box: false,
          data: {
            text: {
              twitter: false,
              header: "Workshop Code of Conduct",
              text:
                `
<p>All attendees, speakers, sponsors and volunteers at our workshops are required to agree with the following
    <a href='http://confcodeofconduct.com' target='blank'>code of conduct</a>.
    Organisers will enforce this code throughout the event. 
    We expect cooperation from all participants to help ensure a safe environment for everybody.<br>
    <br>
    Our conference is dedicated to providing a harassment-free conference experience for everyone,
    regardless of gender, gender identity and expression, age, sexual orientation, disability, physical appearance, body
    size, race, ethnicity, religion (or lack thereof), or technology choices. We do not tolerate harassment of
    conference participants in any form. Sexual language and imagery is not appropriate for any conference venue,
    including talks, workshops, parties, Twitter and other online media. Conference participants violating these rules
    may be sanctioned or expelled from the conference without a refund at the discretion of the conference
    organisers.<br>
    <br>
    For more detailed code of conduct, see: <a href='http://confcodeofconduct.com' target='blank'>confcodeofconduct.com</a>
</p>`
            }
          }
        },
        /*{
          title: "Previous-talks",
          text_block: false,
          text_block_centered: true,
          tab_box: false,
          feature_box: false,
          user_box: false,
          user_box_centered: false,
          data: {
            text: {
              twitter: false,
              header: "Previous talks - 2020",
              text: '<p>(Click title for video)</p>',
              talks: [
                { author: "Jeff King", title: "ROBOT FRAMEWORK AND THE ONE MAN ROBOT BAND", url: "https://www.youtube.com/embed/0yEnJt6Sf50" },
                { author: "Anaïs van Asselt", title: "IMPLEMENTING A TEST AUTOMATION ARCHITECTURE IN A GOVERNMENT ORGANIZATION", url: "https://www.youtube.com/embed/Asy5xHl0uRA" },
                { author: "Antti Karjalainen", title: "THE OPEN RPA ECOSYSTEM", url: "https://www.youtube.com/embed/cO6FxG-RAtQ" },
                { author: "Petteri Mannersalo", title: "ROBOT FRAMEWORK AS AN ENABLER FOR INTELLIGENT PROCESS AUTOMATION", url: "https://www.youtube.com/embed/ViSKJiuT6xo" },
                { author: "Tuomas Lempiäinen", title: "QA DRIVEN RPA AT VEIKKAUS", url: "https://www.youtube.com/embed/3Drlg1q4fkM" },
                { author: "Virpi Luostarinen, Mikael Siirtola", title: "RPA ON RAILS: AUTOMATING MANUAL PROCESSES AT VR", url: "https://www.youtube.com/embed/R7bNgxPjDJ4" },
                { author: "Kristina Sabotic", title: "END-TO-END TESTING FOR END-USERS", url: "https://www.youtube.com/embed/qkQpzGA51go" },
                { author: "Luca Giovenzana, Angelo Caovilla", title: "BEWARE THE BRITTLE DRAGON", url: "https://www.youtube.com/embed/rgpqyPblo28" },
                { title: "Lightning Talks I", url: "https://www.youtube.com/embed/0sKyczF0SDE" },
                { title: "Lightning Talks II", url: "https://www.youtube.com/embed/Xb9npqzJkFY" },
                { title: "Lightning Talks III", url: "https://www.youtube.com/embed/5axgakabN_0" },
                { title: "Lightning Talks IV", url: "https://www.youtube.com/embed/AZOZIW1BJJs" },
                { title: "Lightning Talks V", url: "https://www.youtube.com/embed/G24aU0unvVE" },
                { title: "Lightning Talks VI", url: "https://www.youtube.com/embed/oo11OlAaWWA" },
                { title: "Lightning Talks VII", url: "https://www.youtube.com/embed/7Ks8XSM2Uoc" },
                { title: "Lightning Talks VIII", url: "https://www.youtube.com/embed/jS-HZqLwmIY" },
                { title: "Lightning Talks IX", url: "https://www.youtube.com/embed/HTZ-R3HgByg" },
                { author: "Ismo Aro", title: "Day II", url: "https://www.youtube.com/embed/m1KA3PVukhg" },
                { author: "KEYNOTE: Pekka Klärck", title: "WHAT'S NEW? WHAT'S NEXT? WHO ARE WE?", url: "https://www.youtube.com/embed/DRAu1du3UFU" },
                { author: "Akseli Lukkarila", title: "ACCEPTANCE TESTING A REAL-TIME MUSIC EDUCATION APPLICATION WITH AUDIO", url: "https://www.youtube.com/embed/Fkh-EQ5O7zo" },
                { author: "Maria Prokhorova", title: "NEW IMAGE LIBRARY FOR ADVANCED IMAGE PROCESSING", url: "https://www.youtube.com/embed/AWuh-r-T6Yo" },
                { author: "Tatu Aalto", title: "SELENIUMLIBRARY 4.0: PLUGIN API AND EVENT FIRING WEBDRIVER SUPPORT", url: "https://www.youtube.com/embed/zyNZRTR821Q" },
                { author: "René Rohner", title: "DATADRIVER OR: HOW I LEARNED TO STOP WORRYING AND LOVE OPEN SOURCE", url: "https://www.youtube.com/embed/RtEUr1i4x3s" },
                { author: "Tommi Oinonen", title: "SELF MANAGING TESTING PIPELINES", url: "https://www.youtube.com/embed/W3JUzeV8lp4" },
                { author: "Juho Saarinen", title: "ROBOT FRAMEWORK REMOTE LIBRARY IN PRACTICE (WITH DEMOS)", url: "https://www.youtube.com/embed/B-67yPvMh8Q" },
                { author: "Maciej Brzozowski", title: "MICROSERVICES TESTING USING ARGO: CONTAINER-NATIVE WORKFLOWS FOR KUBERNETES", url: "https://www.youtube.com/embed/xBBTvv4mz0U" },
                { author: "Joonas Köppä, Riku Halonen", title: "ORCHESTRATING ROBOT FRAMEWORK TEST CONTAINERS AND REMOTE LIBRARIES IN KUBERNETES", url: "https://www.youtube.com/embed/SypNjILTRl0" },
                { title: "Day II - Lightning Talks I", url: "https://www.youtube.com/embed/Yjlsl3eHGMI" },
                { title: "Day II - Lightning Talks II", url: "https://www.youtube.com/embed/jDQWBrYD-w8" },
                { title: "Day II - Lightning Talks III", url: "https://www.youtube.com/embed/_T_PCx-tVFk" },
                { title: "Day II - Lightning Talks IV", url: "https://www.youtube.com/embed/-dBWW_77QG4" },
                { title: "Day II - Lightning Talks V", url: "https://www.youtube.com/embed/TZiJLT1fShk" },
                { title: "Day II - Lightning Talks VI", url: "https://www.youtube.com/embed/_XkgOcvKgtc" }]
            }
          }
        },
        {
          title: "",
          text_block: false,
          text_block_centered: true,
          tab_box: false,
          feature_box: false,
          user_box: false,
          user_box_centered: false,
          data: {
            text: {
              twitter: false,
              header: "Previous talks - 2019",
              text: '<p></p>',
              talks: [
                { author: "Ismo Aro / Pekka Klärck", title: "Welcome back! What's new since RoboCon 2018?", url: "https://www.youtube.com/embed/wBhY5Z2RoqQ" },
                { author: "Antti Karjalainen", title: "The start of the open source RPA movement", url: "https://www.youtube.com/embed/uv6dvcoxdvU" },
                { author: "Juho Saarinen", title: "Evolution of Robot Framework user", url: "https://www.youtube.com/embed/ynUmfWvZxpw" },
                { author: "Tatu Aalto", title: "Decade with SeleniumLibrary and browsers' UI automation", url: "https://www.youtube.com/embed/HVAnWH8t4rU" },
                { author: "Brady Hill", title: "RobotFramework for Embedded Software Testing", url: "https://www.youtube.com/embed/0q4-AjqpO9M" },
                { author: "Nguyen Huu Bach", title: "RENAT - a network testing plugin based on Robot Framework", url: "https://www.youtube.com/embed/FSjmJLq4S4A" },
                { author: "Mikael Siirtola", title: "Robot Framework with Patient Monitors: Test Automation at GE Healthcare Finland", url: "https://www.youtube.com/embed/gxbz5QJWdq4" },
                { author: "Päivi Raulamo-Jurvanen", title: "Practical Experiences on Evaluating Software Testing Tools", url: "https://www.youtube.com/embed/2qKa3GEqcvY" },
                { author: "Nicholas Bollweg / Asko Soukka", title: "Robots from Jupyter The Future of Authoring Tests and Tasks", url: "https://www.youtube.com/embed/rbYF_RmiAR8" },
                { author: "Joonas Lehtimäki", title: "Dynamically scalable test environment on top of Kubernetes", url: "https://www.youtube.com/embed/ivLsjU77Q6c" },
                { author: "Oleksandr Kravchenko", title: "Dynamic Generation of Model Based Testcases Using Listener Interface Version 3", url: "https://www.youtube.com/embed/qtEYZ5Om1Qk" },
                { title: "Lightning Talks I", url: "https://www.youtube.com/embed/ck_zvTq4zz8" },
                { title: "Lightning Talks II", url: "https://www.youtube.com/embed/a-27Ot_suEU" },
                { title: "Lightning Talks III", url: "https://www.youtube.com/embed/hA99dYnlb-s" },
                { title: "Lightning Talks IV", url: "https://www.youtube.com/embed/g98m3XpE8gw" },
                { title: "Lightning Talks V", url: "https://www.youtube.com/embed/YJ4FTjxVG3o" },
                { title: "Lightning Talks VI", url: "https://www.youtube.com/embed/9HHgrLb41go" },
                { title: "Lightning Talks VII", url: "https://www.youtube.com/embed/fb42449bdz0" }]
            }
          }
        },

        {
          title: "",
          text_block: false,
          text_block_centered: true,
          tab_box: false,
          feature_box: false,
          user_box: false,
          user_box_centered: false,
          data: {
            text: {
              twitter: false,
              header: "Previous talks - 2018",
              text: '<p></p>',
              talks: [
                { author: "Ismo Aro", title: "Robot Framework Foundation: Welcome to RoboCon", url: "https://www.youtube.com/embed/eAG18mS8UXA" },
                { author: "Pekka Klärck", title: "How Did We Get Here? Where Do We Go Next?", url: "https://www.youtube.com/embed/6Kb1M3NECic" },
                { author: "Régis Déau", title: "The Naked Truth About Successful Test Automation Journey", url: "https://www.youtube.com/embed/Z-9XIGZBf9U" },
                { author: "Aldina Codesso-Lipponen", title: "Mega Robot Projects - What To Expect", url: "https://www.youtube.com/embed/KsRP9TsZwEQ" },
                { author: "Asko Soukka", title: "Robot Framework in Plone CMS Project", url: "https://www.youtube.com/embed/iJEWobuwPeI" },
                { author: "Ed Manlove", title: "The Importance of Open Source Communities", url: "https://www.youtube.com/embed/2GDrtvz_1Ds" },
                { author: "Anssi Syrjäsalo", title: "Towards Contract - Based API Testing with a New Rest Json Test Library", url: "https://www.youtube.com/embed/TMU4WCIq3NA" },
                { author: "Tatu Aalto", title: "Extending SeleniumLibrary 3.0", url: "https://www.youtube.com/embed/ZPqQ-RozkYQ" },
                { author: "Martin Taylor", title: "Design Patterns for Efficient Multi-Platform", url: "https://www.youtube.com/embed/QDaXTkiviT0" },
                { author: "Mikko Korpela", title: "Parallel test execution with Pabot", url: "https://www.youtube.com/embed/i0RV6SJSIn8" },
                { author: "", title: "Lightning Talks", url: "https://www.youtube.com/embed/xb1Udosom6o" },
              ]
            }
          }
        }*/
      ]
    }
  }
}
</script>
