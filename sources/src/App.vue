<template>
  <div class="row no-gutters">
    <navigation-horizontal :pages="pages" />
    <b-img
      :src="require('@/assets/img/ROBOTFW_Mark_White_LOW_cropped.png')"
      class="logo-fixed"
      alt="Robot Framework logo"
    />
    <div class="col-md-12" ref="content" style="width: 100%">
      <app-header />
      <page-block
        v-for="(page, index) in pages"
        v-bind:page="page"
        v-bind:index="index"
        v-bind:key="index"
        class="pl-md-5 px-lg-2 p-sm-2 p-xs-1 link-fix"
      />
      <app-footer class="mt-3 py-5" />
    </div>
  </div>
</template>
<script>
import PageBlock from "@/Components/PageBlock.vue";
import moment, { locale } from "moment-timezone";

export default {
  components: {
    PageBlock,
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
              text: `<p>We are happy to announce that the Robot Framework Foundation will be holding a World Wide Workshop Wednesday on <b>December 2nd</b> this year.</p>
                <p>All Workshops will be held online on <a href="https://bigbluebutton.org/" target="blank">BigBlueButton</a> Servers located in Germany.<br>
                </p>
                <p>Due to COVID-19 we can not have an on-site conference next January and do not get revenues from that ticket sales.
                With this workshop event we want to give you the possibility to donate for Robot Framework.
                But you do also get a lot for your money!<br>
                We have gathered experts from the Robot Framework Community to hold great workshops.
                The revenues of the day will be used entirely for the further development of Robot Framework.</p>
                <p>Special thanks go to all workshop organizers who will share their experience with the community.</p>
                <h2>Thank you very much! You are the best ❤️ </h2></p>`,
            },
          },
        },
        {
          title: "Contribute",
          text_block_centered: true,
          user_contact: true,
          data: {
            text: {
              twitter: false,
              header: "Contribution",
              text: `<p>We are still looking for community members who want to share their knowledge in a workshop.<br>
                Please contact us if you want to contribute:`,
            },
            users: [
              {
                title: "René Rohner",
                text:
                  "<b>René Rohner</b><br>imbus AG<br><a href='mailto:rene@robotframework.org'>rene@robotframework.org</a><br>@René on Slack",
                href: "mailto:rene@robotframework.org",
                img: require("@/assets/img/users/Rene_Rohner.png"),
              },
              {
                title: "Mikko Korpela",
                text:
                  "<b>Mikko Korpela</b><br>Reaktor Oy<br><a href='mailto:mikko@robotframework.org'>mikko@robotframework.org</a><br>@mkorpela on Slack",
                href: "mailto:mikko@robotframework.org",
                img: require("@/assets/img/users/Mikko_Korpela.png"),
              },
            ],
          },
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
              twitter: false,
            },
            users: [
              {
                title: "imbus AG",
                href: "https://www.imbus.de",
                img: require("@/assets/img/sponsors/imbus.png"),
              },
              {
                title: "Reaktor Oy",
                href: "https://www.reaktor.com/",
                img: require("@/assets/img/sponsors/reaktor.png"),
              },
            ],
          },
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
              twitter: false,
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
            ],
          },
        },
        {
          title: "Tickets",
          text_block: false,
          text_block_centered: true,
          tab_box: false,
          feature_box: false,
          data: {
            text: {
              twitter: false,
              header: "Tickets",
              text: `
              <div><p><a href="https://pretix.eu/robocon/WWWW2020" target="blank">Tickets will be available here!</a>
              <br>Ticket sale: ${utc_time("2020-11-04T08:00:00+0000").format(
                "L"
              )} ${utc_time("2020-11-04T08:00:00+0000").format(
                "LT"
              )} (UTC) <span class="local-time">${local_time(
                "2020-12-02T08:00:00+0000"
              ).format("LT")} (${local_tz()})</span></p>

              <p>Workshops in East Asia / Oceania time zones (UTC +12 to UTC +8):</p>

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
              <p style="font-size: 0.95rem">*) Budget Tickets are for anyone who can not afford normal ticket price. Just send an email to <a href="mailto:rene@robotframework.org">Ren&eacute;</a> or contact me on slack @Ren&eacute; and you get a voucher code to buy a budget ticket. No questions! No explanation requested!</p>
              <p>All prices are exclusive of 24 % VAT.</p>
              </div>`,
            },
          },
        },
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
              text: `<p>Date: ${utc_time("2020-12-02T00:00:00+0000").format(
                "L"
              )}<br>Location: The World Wide Web.<br>
              Detailed information will be sent to workshops participants separately.<br>
              </p>
              `,
              /*<a class="col-sm-12 pl-0 mb-5 mt-3" href="https://www.lyyti.fi/reg/robocon2020workshops" target="blank">Tickets available here!</a>`,*/
              talks: [
                { type: "workshop", header: "Half-day workshops" },
                {
                  type: "workshop",
                  pretixid: "239850",
                  author: "Kamal Girdher",
                  start: "2020-12-02T02:30:00+0000",
                  end: "2020-12-02T06:00:00+0000",
                  title: "🇬🇧 Introduction to Robot framework [India/English]",
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
                    <h3>Section 3 - SeleniumLibrary</h3>
                    <b>Duration:</b> 1 Hr + 40 mins practice<br>
                    Introduction to Selenium & SeleniumLibrary<br>
                    Object Identification techniques<br>
                    Operations on web elements<br>
                    Wait statements<br>
                    Assertions<br>
                    Switching to windows and popups<br>
                    Switching to frames<br>
                    Handling Alerts`,
                  bio: "",
                  imgUrl: ["Kamal_Girdher.jpg"],
                },
                {
                  type: "workshop",
                  pretixid: "239594",
                  author: "Mikko Korpela",
                  start: "2020-12-02T07:00:00+0000",
                  end: "2020-12-02T11:00:00+0000",
                  title: "🇫🇮 Browser kirjasto suomeksi [Finland/Suomi]",
                  description:
                    "Käpistellään yhdessä selainkirjaston avulla internetin ihmeellistä maailmaa.",
                  descriptionExpanded:
                    "Katsahdus uuteen Browser kirjastoon, joka käyttää Playwright selainautomaatiotyökalua.",
                  bio:
                    "Mikko Korpela on konsultti ja satunnainen Robot Framework core-kehittäjä Reaktorilta.",
                  imgUrl: ["Mikko_Korpela.png"],
                  sponsorUrl: "https://www.reaktor.com/",
                  sponsorLogo: require("@/assets/img/sponsors/reaktor.png"),
                },
                {
                  type: "workshop",
                  pretixid: "239596",
                  author: "René Rohner",
                  start: "2020-12-02T08:00:00+0000",
                  end: "2020-12-02T12:00:00+0000",
                  title:
                    "🇩🇪 Browser library für SeleniumLibrary User [Germany/Deutsch]",
                  description:
                    "Einführung in die brandneue Robot Framework Browser library für alle Nutzer*Innen der SeleniumLibrary mit Vorkenntnissen in Web-Automatisierung.",
                  descriptionExpanded:
                    "Die brandneue Robot Framework Browser library is eine top moderne Web-Automatisierungsbibliothek basierend auf Microsofts neuer Web-Automatisierungstechnologie Playwright. Dieser Halbtages-Workshop ist für alle Nutzer der SeleniumLibrary mit Vorkenntnissen in Web-Automatisierung.",
                  bio:
                    "René Rohner is a Senior Consultant for Testing Systems in Germany and member of the board of Robot Framework Foundation.<br><br>He has over 6 years of experience with Keyword-Driven and Behavior-Driven Testing in multiple small and huge projects in Germany.",
                  imgUrl: ["Rene_Rohner.png"],
                  sponsorUrl: "https://www.imbus.de",
                  sponsorLogo: require("@/assets/img/sponsors/imbus.png"),
                },
                {
                  type: "workshop",
                  pretixid: "239853",
                  author: "Michael Hallik",
                  start: "2020-12-02T09:00:00+0000",
                  end: "2020-12-02T12:00:00+0000",
                  title:
                    "🇳🇱 HTTP-level testing with the RF RequestsLibrary [Netherlands/Dutch]",
                  description:
                    "In this workshop you will learn the basics of HTTP-level test automation.",
                  descriptionExpanded: `<p><b>Language:</b> Workshop will be in Dutch.</p>
                  <p>Experience the power, versatility and simplicity of Robot Framework. We will cover everything from creating and maintaining an HTTP session, to validating every aspect of the response and everything in between.</p>
                  <ul>
                    <li style="margin-bottom: 0;">Use cases for HTTP-level test automation.</li>
                    <li style="margin-bottom: 0;">HTTP compared to other API-level test automation interfaces (e.g. SOAP).</li>
                    <li style="margin-bottom: 0;">Web-api vs. REST-api.</li>
                    <li style="margin-bottom: 0;">Overview HTTP support within the RF ecosystem (all libraries compared).</li>
                    <li style="margin-bottom: 0;">RequestsLibrary: it's place in a typical RF tool stack (architectural overview).</li>
                    <li style="margin-bottom: 0;">Installation RequestsLibrary.</li>
                    <li style="margin-bottom: 0;">Creating and maintaining an HTTP session with RequestsLibrary.</li>
                    <li style="margin-bottom: 0;">The session object: exposed methods, attributes and how to access them.</li>
                    <li style="margin-bottom: 0;">The session object: various ways to manipulate it (e.g. def headers, cookies).</li>
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
                  bio: "",
                  imgUrl: ["Michael_Hallik.jpeg"],
                  sponsorUrl: "https://immune.it/",
                  sponsorLogo: require("@/assets/img/sponsors/immune.png"),
                },
                {
                  type: "workshop",
                  pretixid: "239854",
                  author: "Adrian Yorke",
                  start: "2020-12-02T11:00:00+0000",
                  end: "2020-12-02T14:00:00+0000",
                  title:
                    "🏴󠁧󠁢󠁥󠁮󠁧󠁿 Robot Framework Cookbook - The Journey So Far [Finland/British English]",
                  description:
                    "This will be a hands-on workshop exploring numerous curated test recipes from Robot Framework Cookbook.",
                  descriptionExpanded: `We will explain how the CI has been implemented for this project and how we use Robocop for linting services.
                  Excellent for beginners and intermediates who want to learn more across a diverse set of libraries and technology areas.
                  <p><h3>Contents:</h3>
                  Check out the github repository to see the material we will be covering:<br>
                  <a href='https://github.com/adrianyorke/robotframework-cookbook/tree/feature/actions#table-of-contents' target='blank'>Robot Framework Cookbook GitHub Repo</a></p> `,
                  bio: `
                  <p>Adrian Yorke is a senior Data Specialist and DevOps Engineer at OP, one of Finland's largest and oldest Financial groups.</p>
                  <ul>
                    <li style="margin-bottom: 0;">Driving force behind the adoption of DevOps and Test Automation using Robot Framework in the Data Warehousing tribe.</li>
                    <li style="margin-bottom: 0;">During 2019 authored and presented a Python Summer Camp workshop series.  Some of the sessions had 60+ live attendees even though it was held during the month of July.</li>
                    <li style="margin-bottom: 0;">Tech interests: Python, Raspberry Pi projects & recently I've been studying machine learning and data science.</li>
                    <li style="margin-bottom: 0;">When I'm not being a geek: swimming (former national championship swimmer), long distance running (I actually completed the London marathon!), carpentry & just being there for my daughter and helping her grow.</li>
                  </ul>`,
                  imgUrl: ["Adrian_Yorke.jpeg"],
                },
                {
                  type: "workshop",
                  pretixid: "239851",
                  author: "René Rohner",
                  start: "2020-12-02T13:00:00+0000",
                  end: "2020-12-02T16:00:00+0000",
                  title: "🇩🇪 Robot Framework Advanced [Germany/Deutsch]",
                  description:
                    "Einführung in die APIs des Robot Framework. Listener, Pre-Run-Modifier, etc. ",
                  descriptionExpanded:
                    "Robot Framework bietet manigfaltige APIs um Tests vor oder währen der Ausführung zu verändern, Tests live mitzulesen, Testprotokolle zu manipulieren oder Bibliotheken zu Entwickeln oder zu Dokumentieren. Dieser Workshop gibt einen guten Überblick über wichtigsten APIs des Robot Framework. Python Basiskenntnisse werden vorausgesetzt.",
                  bio:
                    "René Rohner is a Senior Consultant for Testing Systems in Germany and member of the board of Robot Framework Foundation.<br><br>He has over 6 years of experience with Keyword-Driven and Behavior-Driven Testing in multiple small and huge projects in Germany.",
                  imgUrl: ["Rene_Rohner.png"],
                  sponsorUrl: "https://www.imbus.de",
                  sponsorLogo: require("@/assets/img/sponsors/imbus.png"),
                },
                {
                  type: "workshop",
                  pretixid: "239852",
                  author: "Nils Balkow-Tychsen",
                  start: "2020-12-02T14:00:00+0000",
                  end: "2020-12-02T17:00:00+0000",
                  title:
                    "🇬🇧 KubeLibrary - Verify the state of objects in your Kubernetes Cluster [Germany/English]",
                  description:
                    "RobotFramework library for testing Kubernetes cluster.",
                  descriptionExpanded: `<p><h3 class='mb-0 mt-2'>Language</h3>
                    Workshop will be in English, Questions in German can also be answered.<br>
                    <h3 class='mb-0 mt-2'>Required knowledge</h3>
                    Basic knowledge of Robotframework, Basic knowledge of Kubernetes
                    <h3 class='mb-0 mt-2'>Description</h3>
                    In this workshop you will learn how to connect from your robot tests to a k8s cluster. Feel free to bring your own GKE/EKS/AKS cluster or work with a local cluster in K3S/KinD/MiniKube. You will build your own test suite to assert objects in your cluster. Finally we'll go over contribution to the KubeLibrary.`,
                  bio:
                    "Nils is Lead QA Engineer at Humanitec. He has worked in software testing for more than 20 years, in different industries like finance, games and developer platforms. He specializes in test automation for web apps based on Microservice Architectures.",
                  imgUrl: ["Nils_Balkow.jpeg"],
                  sponsorUrl: "https://www.humanitec.com",
                  sponsorLogo: require("@/assets/img/sponsors/humanitec.png"),
                },
                {
                  type: "workshop",
                  pretixid: "239858",
                  author: "TBA",
                  start: "2020-12-02T14:00:00+0000",
                  end: "2020-12-02T18:00:00+0000",
                  title:
                    "🇬🇧 RPA INTRODUCTION WITH RF AND RPAFramework [Finland/English] ",
                  description:
                    "RPA Framework is a collection of open-source libraries and tools for Robotic Process Automation (RPA), and it is designed to be used with both Robot Framework and Python.",
                  descriptionExpanded: `<p>
                    The goal is to offer well-documented and actively maintained core libraries for Software Robot Developers.<br>
                    <br>
                    This workshops give you an introduction to the basics of RPA and how to use Robot Framework for that usecase.</p>`,
                  bio: "",
                  imgUrl: [],
                  sponsorUrl: "https://robocorp.com/",
                  sponsorLogo: require("@/assets/img/sponsors/robocorp.png"),
                },
                {
                  type: "workshop-last",
                  pretixid: "239595",
                  author: "Mikko Korpela",
                  start: "2020-12-02T15:00:00+0000",
                  end: "2020-12-02T19:00:00+0000",
                  title:
                    "🇬🇧 Pabot Introduction / Tipps & Tricks [Finland/English]",
                  description:
                    "A hands-on introduction to parallel test execution with Robot Framework and Pabot.",
                  descriptionExpanded:
                    "Introduction to parallel test execution with Pabot.",
                  bio:
                    "Mikko Korpela is a consultant and former core developer of Robot Framework. He invented the awesome Pabot.",
                  imgUrl: ["Mikko_Korpela.png"],
                  sponsorUrl: "https://www.reaktor.com/",
                  sponsorLogo: require("@/assets/img/sponsors/reaktor.png"),
                },

                {
                  type: "workshop",
                  header: "Full-day workshops",
                  margin: true,
                },
                {
                  type: "workshop",
                  pretixid: "239857",
                  author: "Juho Saarinen",
                  start: "2020-12-02T07:00:00+0000",
                  end: "2020-12-02T15:00:00+0000",
                  title:
                    "🇬🇧 Remote library usage and advantages [Finland/English]",
                  description:
                    "Learn first basics about remote library interface, and then how to make own libraries that utilize it.",
                  descriptionExpanded:
                    "At the latter part of the day we go through running remote libraries really remote (meaning not on “my machine”), and what advantages that brings.<br><br>Also showing what to do with the Java libraries when Python 2 support is dropped and no suitable replacement available.",
                  bio:
                    "Juho has been doing testing since 2005. He is interested of testing and it's efficiency, and eager to make all kind of testings as soon as possible.<br><br>Juho maintains various java-based RF libraries.<br><br>His 'normal working day' to contain also application development and various operations related things in addition to testing.",
                  imgUrl: ["Juho_Saarinen.jpg"],
                },
                {
                  type: "workshop",
                  pretixid: "239856",
                  author: "Christoph Singer",
                  start: "2020-12-02T08:00:00+0000",
                  end: "2020-12-02T16:00:00+0000",
                  title:
                    "🇩🇪 Einführung Webautomatisierung mit RF Browser [Germany/Deutsch]",
                  description:
                    "Einführung in die Webautomatisierung mit der brandneuen Robot Framework Browser library für alle Interessierte.",
                  descriptionExpanded:
                    "Grundlagenschulung in Webautomatisierung. Von XPATH bis CSS Selektoren und von 'Open Browser' bis 'Execute Javascript' wird in diesem Grundlagen-Workshop alle nötige Basiswissen vermittelt was zum Einstieg in die Browserautomatisierung notwendig ist. Unter Nutzung der neuen Browser library werden wir ein Beispiel Testobjekt automatisieruen und dabei typische Probleme lösen lernen.",
                  bio:
                    "Christoph Singer is a Consultant for Test Automation in Germany.",
                  imgUrl: ["ChristophSinger.jpg"],
                  sponsorUrl: "https://www.imbus.de",
                  sponsorLogo: require("@/assets/img/sponsors/imbus.png"),
                },
                {
                  type: "workshop",
                  pretixid: "239855",
                  author: "Pekka Klärck",
                  start: "2020-12-02T14:00:00+0000",
                  end: "2020-12-02T21:00:00+0000",
                  title:
                    "🇬🇧 Extending Robot Framework (Advanced) [Finland/English]",
                  description:
                    "In this workshop you will learn how to extend Robot Framework using various different interfaces.",
                  descriptionExpanded:
                    "This workshop is for you if you already know basics of using Robot Framework, preferably also basics of writing tests libraries, and want to take your skills to the next level. These skills make it easier to adapt the framework to your own needs in different contexts.<br><br>The workshop is 100% hands-on, no slides, learn-by-doing. In addition to learning from the person who has designed these powerful APIs, you have a chance to ask hard questions related to Robot Framework from its creator.<br><br>Participants should know basics of Robot Framework, including test library API, and Python programming. Participants should bring their own laptop with Python 3.6 or newer and Robot Framework 3.2 or newer installed. They should also have adequate admin rights to install possible additional Python modules using pip. A text editor or an IDE for writing Python code and Robot Framework tests is needed as well.<br><br><h3>Recommended for advanced users.</h3>",
                  bio:
                    "Pekka Klärck is a tester, developer and independent consultant from Finland. He is the original author and lead developer of Robot Framework.",
                  imgUrl: ["Pekka_Klarck.jpg"],
                  sponsorUrl: "http://eliga.fi/",
                  sponsorLogo: require("@/assets/img/sponsors/Eliga.png"),
                },
                {
                  type: "workshop-last",
                  pretixid: "239849",
                  author: "Tatu Aalto",
                  start: "2020-12-02T14:00:00+0000",
                  end: "2020-12-02T21:00:00+0000",
                  title: "🇬🇧 SeleniumLibrary (Advanced) [Finland/English]",
                  description:
                    "Techniques and tooling to ease up web testing and automation by expert developers and maintainer of the SeleniumLibrary. If you need to beef up your Selenium tests, this is the course for you.",
                  descriptionExpanded:
                    "<h2 class='no-arrow mb-3 mt-5'>Outline/overview of the workshop</h2><h3 class='mb-0 mt-2'>Browser Configuration</h3>We will be taking a look at desired capabilites, Selenium options and Firefox profile. Differences between Open Browser and Create WebDriver keywords will be highlighted. Finally we will build small examples showing how to configure the browser in diffrent situations.<h3 class='mb-0 mt-2'>Advanced Debuging</h3>The course will cover when encountering flaky test(s), where to look and how to stabilise them.<h3 class='mb-0 mt-2'>Parallel Execution</h3>We'll discuss running SeleniumLibrary in parallel with pabot and Selenium grid.<h3 class='mb-0 mt-2'>API</h3>SeleniumLibrary has an public API which allows users to extend on top of the SeleniumLibrary. Here we take a look what is available in the public API.<h3 class='mb-0 mt-2'>Expanding the library</h3>Looking at different pros and cons we will talk about how to extend SeleniumLibrary as well as building a new library and the Plugin API. We will show a small exmample. And we will discuss overriding existing keywords with functionality not covered by Selenium.<h3 class='mb-0 mt-2'>EventFiringWebDriver</h3>Using and abusing EventFiringWebDriver for monitoring events and how they affect the interactions with SUT will be covered.<h3 class='mb-0 mt-2'>Page Objects</h3>What are page objects and where it might be useful.<h3 class='mb-0 mt-2'>Python Page objects verses SeleniumLibrary</h3>Looking inside of a page object library and how to build one.<h3 class='mb-0 mt-2'>Checking for time of tests</h3>We will talk about verifying and reacting to execution times of tests/keywords/suites either via tags or the separate Timer library.<h3 class='mb-0 mt-2'>Using Javascript to interact with SUT</h3>Extending SeleniumLibrary with new keywords where functionality is implemented in Javascript.<h2 class='no-arrow mb-3 mt-5'>Learning Outcomes</h2>At the end of the workshop, user should have broad overview of advanced features of SeleniumLibrary, web automation and ways to extend and debug test tooling.<h2 class='no-arrow mb-3 mt-5'>Target Audience</h2>This workshop is for people with previous hands on experience with testing in Robot Framework & SeleniumLibrary. Students should already have experience testing web applications, know how to identify locators for webelements and validate those loctors, and feel comfortable working with SeleniumLibrary. Although the course will take a measured pace through the material, students should be prepared for advanced topics that will be thoroughly explained.<br><br>This workshop will be presented in English with two presentors, both who are bi-lingual in Finnish and English.<h2 class='no-arrow mb-3 mt-5'>Prerequisites</h2>* All participates will need to bring a laptop preconfigured to the workshop.<br>* Particapte must have access to add and modify software on their laptops.<br>* Detailed setup instructions will be shared couple of weeks before workshop day.<br>* Configure your laptops well before the workshop day<br><br>Any special needs should be requested through the conference organizers, at best two weeks prior to the workshop. We will do our best to accomidate any needs and will communicate back either our ability or inability to meet those needs.",
                  bio: /*`
                  Ed Manlove has been a part of the Robot Framework community since 2011. He inherited the leadership of the Selenium2Library project from Ryan Tomac sharing it with Jeremy Johnson and passing on that role to Tatu Aalto. He is the author of a couple libraries dealing with timing issues within AJAX enabled websites. Ed is currently a Senior Software Test Engineer at Cox Automotive testing with Robot Framework and taught several teams how to test with Robot Framework. A member of the Selenium user community Ed has presented at the Selenium Conference, ran an unconference focusing on user issues, and volunteered at the conferences (even being a maître d').
                  */ `
                  Tatu Aalto is the current lead developer of the <a href='https://github.com/robotframework/SeleniumLibrary' target='blank'>SeleniumLibrary</a> and he has been working with Robot Framework since 2011. In the 2011 he was a regular user, by sending many questions and problems to the community. After some time Tatu started to answer questions  send by other users and he did provide his very first pull request to the Robot Framework core in 2012. Tatu has been active community member all these years and 2016 he started as an SeleniumLibrary lead developer.<br><br>Tatu has used the Robot Framework in several work places to to guide and aid companies in their test automation efforts. Currently he is working at F-Secure as a Software Developer In Test, automating windows antivirus client for business users.`,
                  imgUrl: ["Tatu_Aalto.jpg"],
                },
              ],
            },
          },
        },
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
              text: `
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
              </p>`,
            },
          },
        },
      ],
    };
  },
};

function utc_time(dataTime) {
  var locale = window.navigator.userLanguage || window.navigator.language;
  moment.locale(locale);
  return moment.tz(dataTime, "Africa/Freetown");
}

function local_time(dataTime) {
  var locale = window.navigator.userLanguage || window.navigator.language;
  moment.locale(locale);
  return moment.tz(dataTime, moment.tz.guess());
}

function local_tz() {
  return moment.tz.guess();
}
</script>
