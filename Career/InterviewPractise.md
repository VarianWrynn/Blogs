# Interview Practise
@(Interview)[Practise with myself, English Interview]


[toc]







* [Interview Practise](#interview-practise)
  * [Preface](#preface)
  * [0\. Technical Interview](#0-technical-interview)
    * [1)\. Contrast the strengths and capabilities of NoSql and RDB\. Explain in context of performance and distributed systems\.](#1-contrast-the-strengths-and-capabilities-of-nosql-and-rdb-explain-in-context-of-performance-and-distributed-systems)
    * [2)\. How exactly does Hashmaps work\. How do they hash values? How exactly arethe values retrieved in the implementation? Explain with the use of Big O Notation](#2-how-exactly-does-hashmaps-work-how-do-they-hash-values-how-exactly-arethe-values-retrieved-in-the-implementation-explain-with-the-use-of-big-o-notation)
    * [3)\. Name a circumstance where you solved a crisis/big issue and how you had handled it](#3-name-a-circumstance-where-you-solved-a-crisisbig-issue-and-how-you-had-handled-it)
    * [4)\. How do you usually handle criticism?](#4-how-do-you-usually-handle-criticism)
    * [5)\. If you had a massive stored procedure and you needed to ensure that it works correctly with no failure\. Backed with thirty developers and two months, how would you go about testing it?](#5-if-you-had-a-massive-stored-procedure-and-you-needed-to-ensure-that-it-works-correctly-with-no-failure-backed-with-thirty-developers-and-two-months-how-would-you-go-about-testing-it)
    * [6)\. Find the biggest number in an array of unique integers as efficiently as possible\.](#6-find-the-biggest-number-in-an-array-of-unique-integers-as-efficiently-as-possible)
    * [7)\. Contrast the fundamental differences between a multithreaded process and an asynchronous process\. Preferably in the context of c\#\.](#7-contrast-the-fundamental-differences-between-a-multithreaded-process-and-an-asynchronous-process-preferably-in-the-context-of-c)
    * [8)\. Describe one tech thing you learnt recently and learnt well\.](#8-describe-one-tech-thing-you-learnt-recently-and-learnt-well)
    * [9)\. How would you speed up a stored procedure or a database's performance?](#9-how-would-you-speed-up-a-stored-procedure-or-a-databases-performance)
    * [10)\. What are DB Indexes? What are the advantages and disadvantages?](#10-what-are-db-indexes-what-are-the-advantages-and-disadvantages)
  * [1\. PM Interview](#1-pm-interview)
    * [1\.  Introduce yourself](#1--introduce-yourself)
    * [2\. Why would you transfer your career job from RD to PM?](#2-why-would-you-transfer-your-career-job-from-rd-to-pm)
    * [3\. And why you return back now?](#3-and-why-you-return-back-now)
    * [4\. How do you handle a new requirement?](#4-how-do-you-handle-a-new-requirement)
    * [5\. How did you start with a new product?](#5-how-did-you-start-with-a-new-product)
    * [6\. What is the Product Manager?](#6-what-is-the-product-manager)
    * [7\.  What do you know about our comany?](#7--what-do-you-know-about-our-comany)
    * [8\. What and how agile](#8-what-and-how-agile)
    * [9\.  How do you plan the product roadmap?](#9--how-do-you-plan-the-product-roadmap)
    * [10\.  User Profile: What\-Why\-How](#10--user-profile-what-why-how)
    * [11 \.  How do you collect requirements?  =&gt; the process of requirement analysis\.](#11---how-do-you-collect-requirements---the-process-of-requirement-analysis)
  * [\. 文档修订记录](#-文档修订记录)

















## Preface

我还记得，当我还是初中生的时候，我和我弟弟跟我舅舅学过一阵子的功夫。舅舅是当时镇上远近闻名的功夫行家，几个小流氓要在他电影院刷威风，一招就被舅舅制伏不能动弹，几个小流氓自知不敌，在电影院在众目睽睽之下，灰溜溜的溜走了，从此舅舅一战成名。

舅舅是典型的儒家弟子，内圣外儒，喜欢祭拜孔子和毛泽东，因此对于亲人也是倾其所能去帮助，不会私藏。

舅舅要我们每天扎马步2个小时，之后再打一套拳法，每天如此，反复一个月多月，对我们来说是异常的艰苦，弟弟不到2个礼拜就放弃逃跑了，我坚持不到2个月也尿遁了。

然后现在回想起起来，我逐渐明白了一些道理：天下武功，尽是先从套路起步，反复刻意练习，需要长时间积累，到了一定的境界，才能入门更高阶的功法，进而才会对天赋有所要求。

**天赋决定了你能达到的上限，努力程度决定了你能达到的下限。以绝大多数人的努力程度之低，远远没有达到拼天赋的地步**。

在我的内心里面，其实一直对模板和套路有相当的抵制，觉得日常和工作中，需要随机应变，张口既来，因此对平时的英语口语学习，缺少了有针对性的刻意练习。

但这其实是错误的想法。套路和模板不仅可以短期内在有针对性的领域大幅提升表现，也可以跨出它所在的领域影响到各方面。最好的例子，就是我在10年前马尾，每天30-60分钟的不断练习发音，由此入门，掌握了自然拼读法，大幅扩大单词库，也为连读这些打下基础；

另外我在头马获得过的Table Topic演讲名词，也是短时间内刻意模仿各个冠军的结果；最早期上台的我，表无表情，疯狂眨眼睛的，也是有一阵子使用了套路刻意练习，一场演讲甚至做了4~5次才逐渐克服的。

然而反观近期（2018~2020），虽然我也系统的去学习一哈佛大学公正课，但是由于基础不牢，很多课程也仅仅蜻蜓点水的过了一遍有个概念，缺乏深入的反复练习背诵，因此这2年的口语水平我自己并不满意。要知道前几年我对自己口语是很自信和满意的，我甚至敢大言不惭的跟一个英国人讨论他的RP音不是很准，一方面我年轻无知，另一方面又何尝不是自己对满意自信的体现吗。

我想这就是为什么我要搭建这些手脚架模板的原因，我需要反复打牢我的基础，正如练武之人需要反复扎马步和练拳一样。我需要一个能让我在面试上脱口而出，在table topic上自信表达的马步。

























## 1. Technical Interview

### 1). Contrast the strengths and capabilities of NoSql and RDB. Explain in context of performance and distributed systems.  
> One google search away. NoSql has higher throughput read/write, very suitable for datasets that are not relational. I had almost no experience with NoSql.

### 2). How exactly does Hashmaps work. How do they hash values? How exactly arethe values retrieved in the implementation? Explain with the use of Big O Notation  


### 3). Name a circumstance where you solved a crisis/big issue and how you had handled it  

### 4). How do you usually handle criticism?  

### 5). If you had a massive stored procedure and you needed to ensure that it works correctly with no failure. Backed with thirty developers and two months, how would you go about testing it?  

### 6). Find the biggest number in an array of unique integers as efficiently as possible. 
> The answer is something to do with heapsort/quicksort and Big O Notation with a run time of O(n *log n) or something like that.  

### 7). Contrast the fundamental differences between a multithreaded process and an asynchronous process. Preferably in the context of c#.  

1. [What is the difference between asynchronous programming and multithreading? -- StackOverflow](https://stackoverflow.com/questions/34680985/what-is-the-difference-between-asynchronous-programming-and-multithreading#:~:text=In%20multithreaded%20workflows%20you%20assign,of%20the%20just-completed%20task.)

### 8). Describe one tech thing you learnt recently and learnt well.  

### 9). How would you speed up a stored procedure or a database's performance?  

### 10). What are DB Indexes? What are the advantages and disadvantages?  

Used to speed up queries. Formed from multiple columns usually. They need to be updated. They take up some space. Primary key by default is an Index but you can make your own for really busy tables. Usually good for tables with loads of data you can't search from the beginning to end cause it takes too long.

- **参考**
1. [Software Engineer Interview --  WiseTech](https://www.glassdoor.com.au/Interview/WiseTech-Global-Software-Developer-Interview-Questions-EI_IE658123.0,15_KO16,34.htm)

## 2. PM Interview

### 1.  Introduce yourself

This is Lee here, and I am very pleased to apply **for** product manager, ~~I think I am quite suitable for this position because~~ I think this position is quite suitable for me because:
- **First of all**, I have more than 6 years of product management experience,  ~~and familiar with the~~ mastering the required skill as being a product manage, such as market research, competitive product analysis, product requirement analysis, product designing and reviewing with team members.

  > Avoid using [product life cycle managemne](https://zipinventory.com/product-lifecycle-management.html)t, because it involves a big picture, including the industry, marketing, and business model of your company. 

- **Meanwhile**, I used to be a software developer for more than 6 years from 2007 to 2014, So one of my strengths to be a product manager is that I am good at communicating with the RD team because I know how to accurately translate the product requirement into the way of understandable specifications and acceptable by RD.
- **In addition**, I took the PMP (Project Management Professional) exam and got the certification with 5 A in 2019 as well.  It helps me to get a big picture of software engineering projects. 
- **Last but not least,** I have been a member of Toastmasters for more than 6 years. Toastmasters is a non-profit organization that focuses on members' public speaking and leadership training.  It helps me significantly improve my communication skill and leadership.


I've graduated in 2007,  since then, I've been an employee in [Silverlake Axis Group](https://www.linkedin.com/company/silverlake-axis-ltd/?trk=organization-update_share-update_actor-image) as a junior software engineer.  I have worked in this company for more than 4 years. 



### 2. Why did you transfer your career job from RD to PM? 

### 3. And why you return back now?

### 4. How do you handle a new requirement?


### 5. How did you start with a new product?


### 6. What is the Product Manager?

分为三个层次

### 7.  What do you know about our company?

### 8. What and how agile 

### 9.  How do you plan the product roadmap?


1. [产品经理应该如何规划产品线路图？ -- 知乎](https://www.zhihu.com/question/63020639/answer/1359867158)



### 10.  User Profile: What-Why-How

1. [用户画像的基础、原理、方法论（模型）和应用 --刘启林 --知乎](https://zhuanlan.zhihu.com/p/140104236)


### 11 .  How do you collect requirements?  => the process of requirement analysis.

- Stakeholders interview
- 用户画像、需求调研: 通过用户调研、数据分析等手段找到用户的需求点。
- data analysis:根据数据指标，衡量产品的薄弱点，评估新功能的效果
- users feedback
- competitive product: 关注竞品动态，比较彼此的商业模式和运营思路。
- market research

商业分析：发现精准驱动点，带来可持续收入增长，这一点很多人都做不到，但这才是企业的命根子。





## 3. TMC

> **Effective Coach L3P1** -  INTERVIEWER INSTRUCTIONS（8016 )
>
>  
>
> Presenting yourself in a strong and positive way is an important skill when you are the focus of an interview. Whether it is an opportunity to share your expertise with an unfamiliar audience or communicate your skills and experience when interviewing for a new job, talking about yourself comfortably paves the way for success in many settings.
>
>  
>
> **Purpose**: The purpose of this project is to practice the skills needed to present yourself well in an interview.



### ANTICIPATE QUESTIONS

Anticipate questions you may be asked and practice answering them. Review practical examples of how you have contributed or would contribute in a given situation in which your skills apply. Practice answering questions with your examples woven into your responses.

Rehearse with friends or family to get feedback on responses and poise. Record yourself on video or practice in front of a mirror.



#### Appearance

Your appearance matters when you are interviewed. Dress in the way you would like to be perceived. For instance, if you are being interviewed for a job, choose professional clothing



#### Demeanor

The way you are perceived is affected by your demeanor. Your demeanor is **your outward manner**. You can be perfectly dressed for an interview and make a poor impression because of your demeanor.

Focus on behaving in a genuine, respectful way and be yourself. Your interviewer wants to learn about and understand you. Misrepresenting yourself will only lead to problems.

Take your behavioral cues from your interviewer. Make note of her level of formality and match that level or behave in a slightly more formal way



#### Body Language 

Be aware of your body language and what it communicates to the interviewer. Having the best posture possible **shows self-confidence**.

**Make eye contact with your interviewer**. If more than one person is interviewing you, divide your attention evenly among panel members.

Focus on the person asking each question as he or she speaks. When you respond, **acknowledge everyone on the panel of interviewers by making eye contact** with each while you answer.



#### HOW TO SPEAK ABOUT YOUR STRENGTHS

When you are in an interview, focus on the best way to **communicate your strengths**. You have only one opportunity to make a first impression, so take a deep breath and gather your thoughts before you enter the interview.

> **Make an effort to** repeat the name of the interviewer once you have been properly introduced. Doing so demonstrates your respect and consideration to the individual performing the interview.



#### RESPOND WITH CONFIDENCE

When asked a question, answer it as directly as possible. Confident responses that are accurate and succinct demonstrate your preparation. Give interviewers an honest assessment of yourself and your skills. Acknowledge your level of expertise and promote yourself.

If asked, offer carefully-considered plans to build your skills or expertise. 

- Share your intentions to take a training course or join a professional organization. 
- Acknowledging areas where your skills can be developed shows self-awareness. 
- Expressing ways you can build those skills demonstrates motivation. Both self-awareness and motivation are important characteristics to possess and demonstrate to the interviewer.



### 3.1 Simple

- Can you tell me a little bit about yourself?

  Hi everybody, this is Lee, I'm very pleased to be here to apply for Area Director position. I think I am suitable for this position because I've been the member more than 6 year since 2015. Servicing the Shining Stars as the Club President in 2016, and **moreover**, I used to be triple members to support the club growth in Fuzhou.

  

  Beside the Toastmasters, I'm a IT engineer work in a e-commerce**[ˈkɑːmɜːrs]** business company, as we know, this is a rapid changing industry, everyone who works on this industry is required to **develop** a certain kind of leadership, and leadership is the core training skill in Toastmasters, that is the reason why I am really great interesting in the Area Director.

  

- How did you hear about this opportunity?
- Why do you want this job?
- What are your greatest professional strengths or achievements?

  - Being a senor members in Toastmasters
  - High recognize the value of Toastmasters
  - Expertise in IT.
- Why are you leaving your current company?



### 3.2 Challenging

- What do you consider to be your greatest weakness?

  Thank you Sir, that is a really good question. I have to admin that I have many weaknesses that are need to be improved, but I think the one of the greatest weaknesses for me is about delegation. As a senior IT engineer, I could see clearly that sometimes I am not comfortable to breakdown and assign tasks to the team member. Maybe that is associated with my personality characters. I'm still remember when I was a president there was an area speech contest that I need to org**a**nize it. Since I don't like to ask the team members for help, so I decided it arrange everything by myself. It turned out that every 



- What’s your management style?
- How do you deal with stressful situations?
- What can you tell me about our competitors?
- What do you look for in a job?



### 3.3 Most Challenging

- Tell me about a challenge or conflict you have faced at work and how you dealt with it.

  - **Withdraw / avoid**
  - **Smooth / accommodate**
  - **Compromise / reconcile**
  - **Force / direct**

  Different strategy can be applied into different situation. 

- What can you do for us that someone else cannot?

- How would you deal with an angry customer or client?

- What didn’t you like about your last job?

- Where do you see yourself in five years?







## Reference

1. [Job Interview Questions, Answers, and Tips to Prepare](https://www.thebalancecareers.com/job-interview-questions-and-answers-2061204)
2. [Information Technology (IT) Job Interview Questions](https://www.thebalancecareers.com/information-technology-it-job-interview-questions-2061206)
3. [How to Answer "Tell Me About Yourself?" in an Interview](https://www.thebalancecareers.com/tell-me-about-yourself-job-interview-question-2060956)









## . 文档修订记录

1. [Product manager interview prep (relax, start here)](https://igotanoffer.com/blogs/product-manager/pm-interview-prep)
2. [Google PM interview: the only post you'll need to read](https://igotanoffer.com/blogs/product-manager/google-product-manager-interview)
3. ![Alt text](./王力-6年产品经验.docx)
4. [外企面试的时候英语自我介绍该说点什么？--知乎](https://www.zhihu.com/question/19666878/answer/1910689754)


| 版本号|     变化状态|   简要说明|  日期	|   变更人/参与者   |
| :-------- | :--------| :------ |:------ |:------ |
| V0.1|   建立| 文档初建 |2019-11-25  | Lee|
| V1.0| 增加| 1. 新增 `7. What do you know about our company?`章节 |2020-2-14|Lee|

*变化状态：建立，修改，增加，删除
