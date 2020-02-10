# Resume ~ updated in Feburary,2020

## Self-introduction
My name is Yan. I have 9 years of working experience, including 2 years of embedded software development experience, 2 years of front-end development experience, 2 years of web full stack development experience, and the most recent year as project leader. My experience is not flat. I once lost direction and experienced the trough of life. In 2015, I started learning web technology by myself. After one year of hard working, I found a job of front-end development and achieved a career change. I learned lessons from my previous failure and focused on front-end, expanded technical capabilities and enhanced my soft power. For example:
1. Back-end technology: Continuously accumulate back-end technical capabilities in the work, learn SQL, and realize the role change from front-end to full stack.
2. English ability: Persistently reading English articles, English technical documents, and memorizing words every day at work and in life. Recently, I got 85 points in my first TOEFL test.
3. Writing ability: Persist in writing skills. Write down experiences and solutions aquired from work and share it with my colleagues. Then, collect their feedbacks to improve my writing ability.
4. Communication skill: I would use the oppotunities of meetings to enhance my communication skills. For example, I would try to explain an idea or suggestion in the aspects of the background of the issue, what the problem is, what is the solution and the plan to apply the solution.

I learned focus the hard way and I will definitely focus on web technology in the future. I also hope I could be the leader of a large project or the head of the entire front-end team in the near future. That is why I keep expanding my knowlodge and skills in effort.

## Job I want
Senior full stack engineer

## Why I am looking for a job
I am currently a full stack engineer of Didi's takeaway project team, and I am the head of the R & D of the internal tool system. I am satisfied with the current work content and prospects. The reason for my job application is that I want to experience a more free and democratic culture.

## Personal information

<img style="float: right;" width="120px" height="120px" src="https://user-images.githubusercontent.com/21496977/47612176-081cbb00-dab0-11e8-827c-10cd4f0bc656.jpeg">

- Name: Yan/male/1988/China/Bachelor/[Jinan University](https://english.jnu.edu.cn)/Electronic Information Engineering
- Work Experience: 9 years, within which 6 years software development
- Hobbies: travel, movie
- Github: https://github.com/zzz945

## Blog

English：https://medium.com/@zhangdaiyan
Chinese：https://juejin.im/user/5bf622cef265da615c58e51b/posts

## Fields I am familiar with
1. Business: online food takeaway industry, online education industry
2. Technical aspects: MIS system (including CRM)

## Work Experience

| Company | Start Time | End Time | Department | Title |
| ----- | ---- | ---- | ---- | ---- |
| [Didi](https://www.didiglobal.com) | October, 2018 | - | Didi Food | Senior full stack engineer | 
| [Vipkid](https://www.vipkid.com/?vk_fromcode=US) | June, 2016 | October, 2018 | Lingobus | Senior frontend engineer |
| Freelancer | July, 2015 | June, 2016 | Home | Frontend engineer |
| [Actions Technology](http://www.actions-semi.com/en/index.aspx) | July, 2011 | July, 2013 | Firmware 2 | Embedded software engineer |

## Work at Didi
Responsible for the needs assessment, solution design, implementation of the internal tool system of Didi Food's overseas projects, including database tools, search engine evaluation tools, and micro-user analysis tools.

### Didi Food Time Machine Project
This project occupies 70% of the usual work energy, so I would describe this project for short.

##### Background and Goals
The pain in internationalization projects <br>
1.The distance between the R & D team and the user is so long that the cost of money and time to understand the user well is too much.
2. Language and cultural differences between R & D team and user is so huge that understanding user have high requirements for team capabilities

In order to reduce the cost of understanding users and allow each role of the team to get close to users conveniently, we have developed a user micro-behavior analysis product “Didi Food Time Machine”: <br>
1. Help "product manager" and other roles understand users better, increase cognition, discover problems and improve user experience in interactions, strategies, and services.
2. Help "R & D team" trace badcase and provide the context of the problem.  We know that the most frequently asked question by "R & D" is what the user had done before he ran into the problem.

##### Product Features Overview
1. Filter users by tag combination
2. View user portrait
3. Check individual user behavior at the session level

Similar products: https://support.google.com/analytics/answer/6339208?hl=en-Hans

##### My Role
Responsible for R & D, including user needs assessment, project architecture, solution design and code implementation of key features, etc.

##### Technology Overview
Main technology stack: <br>
1. Front end: vue
2. Server: nodejs, koa, mysql
3. Data layer: hive, druid, elastic search
<img width="950" alt="Screenshot 2020-02-08 2 12 39" src="https://user-images.githubusercontent.com/21496977/74080340-0c3ed300-4a7e-11ea-8d41-95e38d63885b.png ">

Solution overview of user behavior display<br>
1. Data layer: The data comes from the event tracking and api logs of the Didi food ios/android app. After processing, it is stored in druid and elastic search database.
2. Timeline display: Time-series event tracking data and back-end api logs are displayed user-friendly in time sequence. We also developed a management tool which we can use to configure event data display rules through UI, and an engine parses the rule to render automaticly, reducing the development workload a lot.

#### Didi Food Search Engine Evaluation Platform

##### Background and Goals
Didi Food currently mainly have business abroad. The language differences made it more difficult for R & D to optimize the  searching results for food and stores. Therefore, we have developed a search engine evaluation platform to be used by foreign local operating teams, who could give more professional assessment on the search results of hot words in different regions to give feedback to the search engine team for strategy optimization.

##### Product Features Overview
The search engine team regularly collects the top 100 hot words and search results in each region, and assigns them to foreign local operating teams to evaluate, and then optimizes search strategies based on the evaluation results.

##### My Role
1. Product design, including ux design, database table structure design
2. Full-stack development, including back-end api and front-end page

### Work at vipkid

Responsible for the development, iteration and maintenance of Lingobus web application (pc + mobile). Lingobus is an online Chinese learning website for kids, with users all around the world.  I am responsible for the optimization of the project architecture, the development of core business logic, such as the registration and login(phone/email/WeChat/facebook), libraries, word cards, etc.
  
During the project, I paid great attention to accumulating reusable components and solutions, and produced documents and demos. https://github.com/lingobus/mpa-starter is a universal scaffolding for multi-page web applications, and contains solutions to the following issues:
  1. Internationalization
  2. Lazyload
  3. bem
  4. Mobile screen adaptation
  5. Login and registration
  6. prerender
  7. Add/del/mod/view solution
In addition, I also developed the pug webpack plugin that the project depends on: https://github.com/lingobus/pug-webpack-plugin

## Open source project
 
### write-vue3-from-scratch (April 2019 ~ May 2019)

 -Project URL: https://github.com/zzz945/write-vue3-from-scratch
 
Write a simple vue from scratch

### vue-d3-chart (February 2018 ~ present)
    
 -Project URL: https://github.com/zzz945/vue-d3-chart
 
Visual component library based on vue and d3

### react-native-alibc-sdk (February 2017 ~ July 2017, maintenance stopped)

 -Project URL: https://github.com/zzz945/react-native-alibc-sdk
 
Provide React Native interface for the Ali Baichuan ios/android SDK

## MY skills

***** Proficient, **** familiar, *** know, ** know a little bit, * not know

| Front-end skills | Years | Capability |
| ----- | ---- | ---- |
| html | 5 | **** |
| js | 5 | ***** |
| css | 5 | **** |
| vue | 4 | ***** |
| vue-cli | 4 | **** |
| vue-router | 4 | **** |
| webpack | 3 | **** |
| element-ui | 4 | ***** |
| axios | 4 | **** |
| lodash | 4 | **** |
| react | 1 | ** |

Back-end skills | Duration (years) | Capability |
| ----- | ---- | ---- |
| nodejs | 2 | **** |
| koa | 2 | **** |
| sql | 2 | **** |
| mysql | 2 | **** |
| sql | 2 | **** |
| thrift | 2 | *** |
| redis | 2 | *** |
| elastic search | 2 | *** |
| shell | 3 | **** |
| pm2 | 3 | *** |
| nginx | 3 | *** |
| docker | 2 | ** |
| go | 2 | ** |

| Tool Ability | Duration (year) | Capability |
| ----- | ---- | ---- |
| git | 10 | **** |
| npm | 4 | **** |
| vscode | 4 | **** |
| jsdoc | 1 | **** |
| jtest | 2 | **** |
| chrome dev tool | 5 | **** |
| iterm2 | 4 | **** |
| postman | 4 | **** |

| Soft Power | Capability |
| ----- | ----- |
| Learning Ability | ***** |
| Search Ability | ***** |
| Communication | **** |
| Document | **** |
| English | **** |
| Empathy | *** |
