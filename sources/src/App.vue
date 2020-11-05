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

setTimeout(() => {
  window.addEventListener("mousemove", (e) => {
    const ticketElm = document.getElementById("ticket");
    const { x, y, width, height } = ticketElm.getBoundingClientRect();
    const centerPoint = { x: x + width / 2, y: y + height / 2 };
    const degreeX = (e.screenY - centerPoint.y) * -0.016;
    const degreeY = (e.screenX - centerPoint.x) * 0.016;

    ticketElm.style.transform = `perspective(1000px) rotateX(${degreeX}deg) rotateY(${degreeY}deg)`;
  });
}, 500);

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
              text: `<p>Come and learn new skills and support Robot Framework development!</p>
                <p>
                We have gathered experts around the world from the Robot Framework Community to hold great workshops for you.
                The revenue of the day will be used entirely for the development of Robot Framework.</p>
                <p>Workshops in English, Suomeksi, Deutsch, Dutch, Portuguese, Русский, Español and Italiano.</p>
                <p>Special thanks to all workshop organizers who will share their experience with the community.</p>
                <h2>Keep scrolling down to learn about workshops and get tickets ⬇️ </h2></p>`,
            },
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
          title: "Contact",
          text_block_centered: true,
          user_contact: true,
          data: {
            text: {
              twitter: false,
              header: "Contact",
              text: `<p>If you have any questions please do not hesitate to contact us!`,
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
              {
                title: "Robocorp Oy",
                href: "https://robocorp.com/",
                img: require("@/assets/img/sponsors/robocorp.png"),
                text:
                  "Robocorp is making RPA accessible to everyone through license-free open source technologies.",
              } /*,
              {
                title: "Reaktor Oy",
                href: "https://www.reaktor.com/",
                img: require("@/assets/img/sponsors/reaktor.png")
              },*/,
            ],
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
              <div class="ticket-visual_visual" id="ticket">
                <canvas id="ticket-canvas"></canvas>
                <div class="ticket-visual-wrapper">
                  <div class="ticket-visual_profile">
                    <div class="ticket-buy-container" onclick="ga('send', 'event', 'toTicketShop', 'magicTicket'); window.open('https://pretix.eu/robocon/WWWW2020/');">
                      <img src="data:image/png;base64,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ERdeQIUvAhKxekAECicgERdeQIUvAhKxekAECicgERdeQIUvAhKxekAECicgERdeQIUvAhKxekAECicgERdeQIUvAhKxekAECicgERdeQIUvAhKxekAECicgERdeQIUvAhKxekAECicgERdeQIUvAhKxekAECicgERdeQIUvAhKxekAECicgERdeQIUvAhKxekAECicgERdeQIUvAhKxekAECicgERdeQIUvAhKxekAECicgERdeQIUvAhKxekAECicgERdeQIUvAqP4+8RtmQ/8sfH2LW19EeAfN183f+fZV2YHshmFiCHeCrlfwedwmX8CM6R4hbrX2N5AzEts3Zr7x2kUco7q3cO5lY2LQIV0F+iBezj3XZprEaNwC1SNPnFZPSXVlcAUJ1LI3LoztyJGwa5Rrbm7iimhvgR4I7/zKGSXIkahZigYvwaWicAuAQqZT2auzKWIUSF3hXLVdXmTmTZPaXmjCDi7OxGjQHPwqQIy0lD+CHxAn3BVdmHuRIyqfHBRGSURkwAFfBZzgpRjuxJxc3edpgSouYol8K7YyPcCdyVi5CYB7xVYL58lMHv2ncLekIgLK5jCDUagCjZS5oG8iZhf68hEYFQEvIl4VMVTsiJAAt5EvFZZRaAjgW3H88yf5k3EtXniCtAKgbWVQIbG4UrE+JWzGkDoMhF4jQB/59iFuRJxU5E/XFRGScQmsIo9QarxPYr4FvDcfL2TqhFGNs+yeWpzkbY7EaM4FPCNi+ooiRgE2B+XMQbONaY7ERMkhMzVeJULquY1TeC8udGbDvKY4FyKuAFwju3mGBg61z0BCtjdzd2tiJu77Snacum+NZXgawS2OOE9emL52oklvu9WxCwGhQznivweXsNl4yOwRMpv0QfuVuC2lK5F3CbJAsLf4DXFvITXcJlfAmukdgt/g7qfw2vsu7VRfO50Wz0Uk3djt3fkNk9tx0VgFCvxuEqqbMdGQCIeW8WVrzsCErG7kiqhsRGQiMdWceXrjoBE7K6kSmhsBCTisVVc+bojIBG7K6kSGhsBiXhsFVe+7ghIxO5KqoTGRkAiHlvFla87AhKxu5IqobERkIjHVnHl646AROyupEpobARSibgaG1jlKwIgMEtBIZWIf02RjOYQAWMEfkkRTyoRn6VIRnOIgDECSfo+lYgr/AHwuTHACkcEohFAv19g8Em0CXYGTiViTvkRiSVJaic/7YpAcgLo8wqTXqWamCLeJJqMAr6TkBPR1jRZCDT9/RmTJ1uwKOK/E2Y7xVwSckLgmiodgUbAd5iRfZ7MKOJtstm+TyQhJwau6eITyCVgZLZJ+Ti9S1JC3qWh/aIJZBQwudUn/BdB/MNtBttgzlN8lGzqp4EMqWpKjwQyC5h/HOFnrsS01fdN8n+1IidHrglDEcgsYKbxoNtWxF9CJdZjHAm5BzRdkpeAAQETwFf+0z5OT7D/Fw9ktA3m1qN1xgJo6m4EjAj44VGaET+sxM3XpMtuKUQ7SytyNLQaOBQBIwJmOp/anB5WYr5AcBU237if2bQiZy6Apj9MwJCAt4jwTbP4fl+JGTIO1Njccj+zaUXOXABN/5SAIQEzuE+tgPnix0rMF02g99it+DqzaUXOXABN/52AMQFvIOC3u7Vpvzv9cKxR9/nuCRn3tSJnhK+pvxMwJuAtonqiz0ciZtgQ8vrQiXwvg0nIGaBryu8EjAmYQV1Cn3xC7WZIYAG3YvcIZNItcp0lAsMJsN/g7DsrNu+VFaJfWMkAcUjIvaqoi44lgF7zIeA2cSS0gFsxCbktjLZRCKDRfQm4pYTEFlZUjDgk5LYw2gYlgN7yKeCWEhJcwK2YhNwWRtsgBNDYvgXcUkKiCysqRhwSclsYbQcRQC+NQ8AtJSS8gFsxCbktjLa9CKCRxyXglhISX1hRMeKQkNvCaHsUAfTOOAXcUgKABdyKUchVG5u2IvAaAfTLFM6+sWLz12KO8j6yX1ghgDj+gl/DqyjJalAXBNgf8AXcks2HwH30CxB9BgKJBa4bFESfeV+5hj+atn3lHL09PgIVUqZbsnP8KOVySECDRczJjQp5CBddKwIpCAwWMIMMImIOJCGTgkwEOhMIImDOFkzEHExCJgWZCLxKIJiAOVNQEXNACZkUZCLwLIGgAuYswUXMQSVkUpCJwBMCwQXMGaKImANLyKQgE4EfBKIImKNHEzEHl5BJQSYCP0UTMNlGFTEnkJBJQTZiAlEFTK7RRcxJJGRSkI2QQHQBk2kSEXMiCZkUZCMikETA5JlMxJxMQiYF2QgIJBMwWSYVMSeUkElB5phAUgGTY3IRc1IJmRRkDgkkFzAZZhExJ5aQSUHmiEAWAZNfNhFzcgmZFGQOCGQTMNllFTEDkJBJQVYwgawCJrfsImYQEjIpyAokkF3AZGZCxAxEQiYFWUEETAiYvJ78VcRcEE9OTs4x922u+TWvCBxBwIyAGbOZlbgFiBV5jv2PcP0VxBaKtlYI8HPbKOCVlYAYhzkRMygIeYoNP4CPW5kIWCCwRhAUcG0hmN0YzDxO7wYFUBv4WxzjIzbvfjIRyEWgxsQU7ymc++bM5Eq8Swmr8gSvz+BX8AouE4EUBDaY5BOEu0wx2ZA5zIt4N7nmMZuCfgef7b6nfREYSGCL6yncL/CV1VX3UI5FiXg/AYi6wjG6TASGEKhLEu1+ov8HNJr5BA1F6okAAAAASUVORK5CYII=" alt="Robot Framework logo" class="ticket-profile_image">
                      <div class="ticket-main-texts">
                        <p class="ticket-buy-text">Buy your ticket HERE</p>
                        <p class="ticket-rf-text">Robot Framework</p>
                      </div>
                    </div>
                    <div class="ticket-event-info">
                      <h3>World Wide Workshop Wednesday</h3>
                      <div class="ticket-event-more-info">
                        <h3 class="ticke-date">02/DEC/2020</h3>
                        <h3 class="ticket-position">ONLINE</h3>
                      </div>
                    </div>
                  </div>
                  <div class="ticket-visual_ticket-number-wrapper">
                    <h3 class="ticket-visual_ticket-number">№ 43770</h3>
                  </div>
                  <div class="left"></div>
                  <div class="right"></div>
                </div>
              </div>
              `,
              /*<a class="col-sm-12 pl-0 mb-5 mt-3" href="https://www.lyyti.fi/reg/robocon2020workshops" target="blank">Tickets available here!</a>`,*/
              talks: [
                { type: "workshop", header: "Half-day workshops" },
                {
                  type: "workshop",
                  pretixid: "239850",
                  author: "Kamal Girdher 🇮🇳",
                  start: "2020-12-02T02:30:00+0000",
                  end: "2020-12-02T06:00:00+0000",
                  title:
                    "🇬🇧 Introduction to Robot framework [India/English] 1️⃣",
                  price: 100,
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
                  price: 300,
                  author: "Mikko Korpela 🇫🇮",
                  start: "2020-12-02T07:00:00+0000",
                  end: "2020-12-02T11:00:00+0000",
                  title: "🇫🇮 Browser kirjasto suomeksi [Finland/Suomi] 3️⃣",
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
                  pretixid: "244011",
                  price: 300,
                  author: "Liviu Avram 🇷🇴",
                  start: "2020-12-02T08:00:00+0000",
                  end: "2020-12-02T12:00:00+0000",
                  title:
                    "🇬🇧 Mobile Automation With Robot Framework And Appium [Romania/English] 3️⃣",
                  description:
                    "In this workshop you will learn the basics about automating a native mobile application on Android.",
                  descriptionExpanded: ` We will also take a quick look at iOS.<br>
                    <h3 class='mb-0 mt-2'>Topics that will be covered<h3>
                    <p>
                    <ul>
                    <li>Prerequisites for mobile Automation</li>
                    <li>Tools and Operating systems</li>
                    <li>How to create Android emulators with Android Studio with different versions of Android</li>
                    <li>How to use ADB to interact with the Android device (install/uninstall applications, interact with the Android interface and more)</li>
                    <li>How to locate elements on the mobile interface using UiautomatorViewer and Appium inspector</li>
                    <li>How to create Appium server sessions with desired capabilities</li>
                    <li>How to correctly launch the application on the mobile device using Robot Framework and Appium</li>
                    <li>Create simple automation scripts for some of the application features</li>
                    <li>Implement automation best practices for Keywords and Variables</li>
                    <li>Overview of Android vs iOS when it comes to automation</li>
                    <li>Tips and tricks about mobile automation</li>
                    <li>Q&A session</li>
                    </ul></p>
                    `,
                  bio: `I am a QA Engineer since 2007 and since 2015 I started automating on web, mobile and desktop with Robot Framework.<br>
                    Since 2018 I am also a scrum master on a qa project in my company`,
                  imgUrl: ["Liviu_Avram.png"],
                  sponsorUrl: "https://www.pentalog.com",
                  sponsorLogo: require("@/assets/img/sponsors/Pentalog.png"),
                },
                {
                  type: "workshop",
                  pretixid: "239596",
                  price: 300,
                  author: "René Rohner 🇩🇪",
                  start: "2020-12-02T08:00:00+0000",
                  end: "2020-12-02T12:00:00+0000",
                  title:
                    "🇩🇪 Browser library für SeleniumLibrary User [Germany/Deutsch] 3️⃣",
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
                  price: 300,
                  author: "Michael Hallik 🇳🇱",
                  start: "2020-12-02T09:00:00+0000",
                  end: "2020-12-02T13:00:00+0000",
                  title:
                    "🇳🇱 HTTP-level testing with the RF RequestsLibrary [Netherlands/Dutch] 3️⃣",
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
                  bio: `<p>Michael has been a software tester since 2000, in various roles.</p>
                        <p>His first exposure to Robot Framework (and test automation) came as early as 2011.
                        It was love at first sight.
                        Since then he has utilized its unmatched power and versatility within such disparate domains as banking, real estate, insurance and the worlds of CMS, CDP and EDP systems.
                        Just as diverse have been the interfaces that had to be automated against. But regardless whether it were web GUIs, SOAP services, database APIs, REST-APIs, proprietary JAVA APIs, MQ or ILE RPG based mainframe systems: RF and its rich ecosystem always came to the rescue.</p>
                        <p>Michael has written extensively about various aspects of working with Robot Framework, in the form of a series of blog posts. He has also created his own series of Robot Framework related workshops, around themes such as the Remote Library Interface, the testing of RESTful JSON APIs or the testing of SOAP services.
                        For Michael's profile, please see: <a href="https://www.linkedin.com/in/michaelhallik/">linkedin.com/in/michaelhallik/</a></p>`,
                  imgUrl: ["Michael_Hallik.jpeg"],
                  sponsorUrl: "https://immune.it/",
                  sponsorLogo: require("@/assets/img/sponsors/immune.png"),
                },
                {
                  type: "workshop",
                  pretixid: "243985",
                  price: 300,
                  author: "Hélio Guilherme 🇵🇹",
                  start: "2020-12-02T10:00:00+0000",
                  end: "2020-12-02T13:00:00+0000",
                  title:
                    "🇬🇧 Tips and Tricks with Robot Framework IDE (RIDE) [Portugal/English] 3️⃣",
                  description:
                    "Introduction to Robot Framework, installation and use of internal and external libraries with RIDE.",
                  descriptionExpanded: `In this Workshop, we'll start by installing Robot Framework and RIDE, and run some small examples on command window/shell or terminal, and then in RIDE Run tab.<br>
                    We will explore the internal libraries with some examples, and then with external libraries see the full power of Robot Framework, and at the same time getting to know most useful RIDE features.`,
                  bio: `Hélio Guilherme is an experienced Software Tester since 2008 when he first had contact with Robot Framework and RIDE, at Nokia Networks in Lisbon, Portugal.<br>
                    During his work activities he used all the Robot Framework internal libraries, and other libraries like: <b>SikuliLibrary, SSHLibrary, SeleniumLibrary, RequestsLibrary and AppiumLibrary</b>.<br>
                    He is currently the lead developer and maintainer of RIDE.<br>
                    Professionally, he is QA Engineer at LOAD in Aveiro, Portugal (http://load.digital/), which is sponsoring his time for this Workshop.`,
                  imgUrl: ["Helio_Guilherme.png"],
                  sponsorUrl: "http://load.digital/",
                  sponsorLogo: require("@/assets/img/sponsors/Load.png"),
                },
                {
                  type: "workshop",
                  pretixid: "239854",
                  price: 300,
                  author: "Adrian Yorke 🇫🇮",
                  start: "2020-12-02T11:00:00+0000",
                  end: "2020-12-02T14:00:00+0000",
                  title:
                    "🏴󠁧󠁢󠁥󠁮󠁧󠁿 Robot Framework Cookbook - The Journey So Far [Finland/British English] 3️⃣",
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
                  pretixid: "250361",
                  price: 300,
                  author: "Kerkko Pelttari 🇫🇮",
                  start: "2020-12-02T12:00:00+0000",
                  end: "2020-12-02T16:00:00+0000",
                  title:
                    "🇬🇧 Advantages and possibilities of Robotframework-Browser library [Finland/English] 3️⃣",
                  description:
                    "Let’s get familiar and experiment with the best features of RobotFramework Browser:",
                  descriptionExpanded: `<p>
                  You will learn:<br>
                  - Control of Pages, Contexts and Browsers<br>
                  - Implicit waits (How playwright’s implicit wait heuristics work?)<br>
                  - Implicit cleanup<br>
                  - Assertion syntax<br>
                  - Performance<br>
                  - Possibilities and interest for future features and plugins<br>`,
                  bio:
                    "Kerkko worked as a Reaktor consultant in building the robotframework-browser library in summer of 2020. Now he participates through open-source work and creates RobotFramework based RPA-tooling at Robocor.",
                  imgUrl: ["Kerkko_Pelttari.jpeg"],
                  sponsorUrl: "https://robocorp.com/",
                  sponsorLogo: require("@/assets/img/sponsors/robocorp.png"),
                },
                {
                  type: "workshop",
                  pretixid: "239851",
                  price: 300,
                  author: "René Rohner 🇩🇪",
                  start: "2020-12-02T13:00:00+0000",
                  end: "2020-12-02T16:00:00+0000",
                  title: "🇩🇪 Robot Framework Advanced [Germany/Deutsch] 3️⃣",
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
                  price: 300,
                  author: "Nils Balkow-Tychsen 🇩🇪",
                  start: "2020-12-02T14:00:00+0000",
                  end: "2020-12-02T17:00:00+0000",
                  title:
                    "🇬🇧 KubeLibrary - Verify state of your Kubernetes Cluster [Germany/English] 3️⃣",
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
                  pretixid: "????",
                  price: 300,
                  author: "Andrea Gubellini 🇮🇹 & Angelo Caovilla 🇮🇹",
                  start: "2020-12-02T14:00:00+0000",
                  end: "2020-12-02T17:00:00+0000",
                  title:
                    "🇮🇹 From zero to hero [Italy/IT] 3️⃣",
                  description:
                    "Impara ad automatizzare nel modo corretto senza skill o conoscenze pregresse!",
                  descriptionExpanded: `
                  <p>Durante questo workshop acquisirai conoscenze generali sulle automation best practices,
                  come interagire con pagine web, come impostare un'architettura effettiva per i tuoi test,
                  livelli di astrazione BDD ed altro: tutto utilizzando Robot Framework!</p>
                  `,
                  bio:
                    `
                    <p>Angelo is a Vegan - Heavy Metal - Man with a lot of hobbies and interests.
                    His main interest is quality and he applies it at work.
                    Currently he is the Chapter QA Lead in CHILI, managing 2000+ test case with a great team.
                    Together with Luca Giovenzana he founded the italian RobotfFramework Community.
                    He is also called Automation Hero.</p>
                    <p>Andrea is a self-taught  QA Engineer/Dev with a strong passion about technology.
                    He loves creating stuff and contributing to open source projects.
                    After a few months using and trying Robot Framework he started
                    developing custom libraries and joined Robot framework Italian Meetup as one of the organizers.</p>
                    `,
                },
                {
                  type: "workshop",
                  pretixid: "239858",
                  price: 100,
                  author: "Jani Palsamäki 🇫🇮 & Mika Hänninen 🇫🇮",
                  start: "2020-12-02T14:00:00+0000",
                  end: "2020-12-02T18:00:00+0000",
                  title:
                    "🇬🇧 RPA with Robot Framework and Robocorp Cloud [Finland/English] 1️⃣",
                  description:
                    "Robocorp is making RPA accessible to everyone through license-free open source technologies, delivered from a cloud platform. Join us and learn to build and orchestrate software robots with Robocorp's developer tools and RPA Framework's open-source libraries.",
                  descriptionExpanded: `<p>
                    The goal is to offer well-documented and actively maintained core libraries for Software Robot Developers.<br>
                    <br>
                    This workshops give you an introduction to the basics of RPA and how to use Robot Framework for that usecase.</p>
                    Agenda:<br>
                    - Robocorp & introductions 00-00:15<br>
                    - Test automation and RPA differences 00:15-00:30<br>
                    - Building a robot with Robocorp 00:30-1:30<br>
                    - Break 01:30-01:45<br>
                    - Continue building 01:45-2:45<br>
                    - Running the robot on Cloud, scheduling 2:45-3:30<br>
                    - Wrap up & feedback 3:30-4:00<br>`,
                  bio: `<p>Jani is a technical content author at Robocorp with a background in software development. He likes bad humor and enjoys writing tongue-in-cheek.</p>
                  <p>Mika is a developer for RPA Framework libraries with a background as a software and test automation developer. He likes to help people implement their robots as smooth as possible. Known also as a provider of bad jokes.</p>`,
                  imgUrl: ["Jani_Palsamäki.jpg", "Mika_Hänninen.jpeg"],
                  sponsorUrl: "https://robocorp.com/",
                  sponsorLogo: require("@/assets/img/sponsors/robocorp.png"),
                },
                {
                  type: "workshop",
                  pretixid: "244001",
                  price: 200,
                  author: "Hélio Guilherme 🇵🇹",
                  start: "2020-12-02T15:00:00+0000",
                  end: "2020-12-02T18:00:00+0000",
                  title:
                    "🇵🇹 Dicas e Truques com Robot Framework IDE (RIDE) [Portugal/Portuguese] 2️⃣",
                  description:
                    "Introdução ao Robot Framework, instalação e uso das bibliotecas internas e externas com o RIDE",
                  descriptionExpanded: `Neste Workshop, começamos pela instalação do Robot Framework e do RIDE, correremos alguns pequenos exemplos na linha de comandos e no separador Run do RIDE.<br>
                    Iremos explorar as bibliotecas internas com alguns exemplos, e depois com as bibliotecas externas veremos o potencial do Robot Framework, e ao mesmo tempo conhecer as importantes funcionalidades do RIDE.`,
                  bio: `Hélio Guilherme é um Testador de Software desde 2008 quando teve o primeiro contacto com Robot Framework e o RIDE, na Nokia Networks em Lisboa, Portugal.<br>
                    Durante as suas actividades profissionais, ele utilizou todas as bibliotecas internas do Robot Framework, e outras bibliotecas como sejam: SikuliLibrary, SSHLibrary, SeleniumLibrary, RequestsLibrary e AppiumLibrary.<br>
                    Ele é presentemente o líder de desenvolvimento e manutenção do RIDE. Profissionalmente, ele é Engenheiro de Qualidade na LOAD em Aveiro, Portugal (http://load.digital/), que patroncina o seu tempo neste Workshop.`,
                  imgUrl: ["Helio_Guilherme.png"],
                  sponsorUrl: "http://load.digital/",
                  sponsorLogo: require("@/assets/img/sponsors/Load.png"),
                },
                {
                  type: "workshop",
                  author: "Maria Prokhorova 🇷🇺",
                  price: 200,
                  pretixid: "250362",
                  start: "2020-12-02T15:00:00+0000",
                  end: "2020-12-02T18:00:00+0000",
                  title:
                    "🇷🇺 Практический семинар по работе с библиотекой Image Library [Russian/Русский] 2️⃣",
                  description:
                    "На семинаре будет много практики с объяснением нюансов работы с библиотекой для анализа изображений.",
                  descriptionExpanded:
                    " А также знакомство с новыми кейвордами и их использованием в задачах автоматизации тестирования графических интерфейсов.",
                  bio: "",
                  imgUrl: ["Maria_Prokhorova.jpeg"],
                },
                {
                  type: "workshop",
                  pretixid: "239595",
                  price: 300,
                  author: "Mikko Korpela 🇫🇮",
                  start: "2020-12-02T15:00:00+0000",
                  end: "2020-12-02T19:00:00+0000",
                  title:
                    "🇬🇧 Pabot Introduction / Tips & Tricks [Finland/English] 3️⃣",
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
                  pretixid: "256053",
                  price: 300,
                  author: "Anton Cervantes 🇪🇸",
                  start: "2020-12-02T16:30:00+0000",
                  end: "2020-12-02T20:30:00+0000",
                  title:
                    "🇪🇸 Introducción a SeleniumLibrary y RequestsLibrary (Web Testing + API Testing) [España/Español] 3️⃣",
                  description:
                    "Curso de iniciación en el testing web y API con Robot Framework.",
                  descriptionExpanded: `<p>Parte 1: Fundamentos de Robot Framework (1h)
                    En esta sección aprenderemos a crear test cases, test suites, keywords de usuario, tipos de variables, keywords condicionales, bucles, manipulación de ficheros json, etc.</p>
                    <p>Parte 2: Introducción al testing UI con SeleniumLibrary (1h 30m)
                    En esta sección automatizaremos el proceso de compra en una tienda online (e-commerce). Para ello aprenderemos a identificar objectos, operaciones con elementos, instrucciones de espera, validaciones, etc.</p>
                    <p>Parte 3: Introducción al testing API con RequestsLibrary (1h 30m)
                    En esta sección validaremos el correcto funcionamiento de una API de una web de reservas. Para ello aprenderemos a hacer llamadas Get, Post, Put, Patch, Delete, Health Check y validaremos las respuestas obtenidas del servidor.</p>
                    `,
                  bio:
                    "Anton Cervantes ha trabajado como ingeniero de test desde 2008 en diferentes empresas de consultoría entre otras. Anton empezó a automatizar utilizando Robot Framework en 2017 para web y mobile utilizando SeleniumLibrary, AppiumLibrary y RequestsLibrary.",
                  imgUrl: ["A_Cervantes.jpg"],
                },
                {
                  type: "workshop",
                  pretixid: "250361",
                  price: 300,
                  author: "Luca Giovenzana 🇮🇹",
                  start: "2020-12-02T16:00:00+0000",
                  end: "2020-12-02T19:00:00+0000",
                  title:
                    "🇬🇧 HTTP api testing and RPA with RequestsLibrary [Italy/English] 3️⃣",
                  description:
                    "This workshop is about HTTP api for direct test or as prerequisites for your end to end test automation suite.",
                  descriptionExpanded: `<p>
                  You will learn:<br>
                  - how to setup a basic API testing/rpa project using the RequestsLibrary<br>
                  - how to handle shared session and authentication<br>
                  - how to validate the response<br>
                  - what to address with api testing in your test suite<br>
                  - how to use RF for basic stress tests<br>
                  - how to use pabot and RequestsLibrary to execute many requests in parallel<br>
                  We will use the new 0.8 pre-release version and we will talk about the development roadmap.<br>`,
                  bio: `Luca Giovenzana is an Open Source and Linux passionate guy.<br>
                  Before discovering RobotFramework he built his own Python framework to remotely control and test Linux based firewalls.<br>
                  He has been Head of QA for many years and, together with an amazing team, created a full stack test automation suite with more than 2 thousands test cases.<br>
                  Now he fosters the Quality culture as an Agile Coach.<br>
                  Together with Angelo Caovilla founded the RobotFramework Italian community and Meetup.<br>
                  He contributes to the community and he is the maintainer of RequestsLibrary.`,
                  imgUrl: ["Luca_Giovenzana.jpeg"],
                  sponsorUrl: "https://chili.com",
                  sponsorLogo: require("@/assets/img/sponsors/Chili.png"),
                },

                {
                  type: "workshop",
                  header: "Full-day workshops",
                  margin: true,
                },
                {
                  type: "workshop",
                  pretixid: "239857",
                  price: 500,
                  author: "Juho Saarinen 🇫🇮",
                  start: "2020-12-02T07:00:00+0000",
                  end: "2020-12-02T15:00:00+0000",
                  title:
                    "🇬🇧 Remote library usage and advantages [Finland/English] 3️⃣",
                  description:
                    "Learn first basics about remote library interface, and then how to make own libraries that utilize it.",
                  descriptionExpanded:
                    "At the latter part of the day we go through running remote libraries really remote (meaning not on “my machine”), and what advantages that brings.<br><br>Also showing what to do with the Java libraries when Python 2 support is dropped and no suitable replacement available.",
                  bio:
                    "Juho has been doing testing since 2005. He is interested of testing and it's efficiency, and eager to make all kind of testings as soon as possible.<br><br>Juho maintains various java-based RF libraries.<br><br>His 'normal working day' to contain also application development and various operations related things in addition to testing.",
                  imgUrl: ["Juho_Saarinen.jpg"],
                  sponsorUrl: "https://mavericks.fi/",
                  sponsorLogo: require("@/assets/img/sponsors/mavericks.png"),
                },
                {
                  type: "workshop",
                  pretixid: "239856",
                  price: 500,
                  author: "Christoph Singe 🇩🇪",
                  start: "2020-12-02T08:00:00+0000",
                  end: "2020-12-02T16:00:00+0000",
                  title:
                    "🇩🇪 Einführung Webautomatisierung mit RF Browser [Germany/Deutsch] 3️⃣",
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
                  price: 500,
                  author: "Pekka Klärck 🇫🇮",
                  start: "2020-12-02T14:00:00+0000",
                  end: "2020-12-02T21:00:00+0000",
                  title:
                    "🇬🇧 Extending Robot Framework (Advanced) [Finland/English] 3️⃣",
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
                  author: "Tatu Aalto 🇫🇮",
                  price: 500,
                  start: "2020-12-02T14:00:00+0000",
                  end: "2020-12-02T21:00:00+0000",
                  title: "🇬🇧 SeleniumLibrary (Advanced) [Finland/English] 3️⃣",
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
          title: "Tickets",
          text_block: false,
          text_block_centered: true,
          tab_box: false,
          feature_box: false,
          data: {
            text: {
              twitter: false,
              header: "Tickets 🎉",
              text: `
              <p><a href="https://pretix.eu/robocon/WWWW2020" onclick="ga('send', 'event', 'toTicketShop', 'ticket')" target="blank">Tickets are available here!</a>
              <br>Tickets are available NOW!! Note: times in the shop are in UTC.
              <p>All Workshops will be held online on <a href="https://bigbluebutton.org/" target="blank">BigBlueButton</a> Servers located in Germany.<br>
              </p>
              <p>
              You can try out our <a href="https://pretix.eu/robocon/BBB/ticket/Q0QRP/1/z39cjbggz466x9fs/call/" target="blank">Test Platform here</a> to ensure technical compatibility.
              </p>
              <br>

              <p>Workshops are sold in three different price zones.
              With these zones we try to set fair prices all around the globe.
              The zones are selected based on the expected participants.
              We want to create an event where everyone can afford tickets.

              <p>Workshops in price zone 1️⃣:</p>
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

              <p>Workshops in price zone 2️⃣:</p>
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

              <p>Workshops in price zone 3️⃣:</p>
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
