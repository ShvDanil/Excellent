## API for student and tutor search services
This repository describes the solution of the case **Excellent - API for student and tutor search services**. 
It contains information about the domain analysis, use cases, functional and non-functional requirements, component model, proposed architecture and patterns of the solution.


## Contents at a Glance
* [Domain analysis](./README_ENG.md#Domain-analysis)

* [Use cases](./README_ENG.md#Use-Cases)

* [Functional and non-functional requirements](./README_ENG.md#Functional-and-non-functional-requirements)

* [Component model](./README_ENG.md#Component-model)

* [Reference architecture and patterns](./README_ENG.md#Reference-architecture-and-patterns)


## Domain analysis

### A. Introduction
The number of tutors is increasing from year to year. They help with preparation:
- for the first class;

- for entering a prestigious school;

- for passing state exams;

- for a creative test at a university;

- for the student Olympics.

Tutors also help to:
- to improve academic performance;

- to study the subject in depth.

Moreover, the number of clients is also growing up. According to the Internet portal [Rambler:](https://news.rambler.ru/sociology/43812515-eksperty-obyasnili-pochemu-k-2021-godu-v-rossii-vyrastet-potrebnost-v-repetitorah/?utm_content=news_media&utm_medium=read_more&utm_source=copylink) "70% of Russian schoolchildren continue using the services of tutors and visit additional education courses after lessons," furthermore the scientific and educational portal [IQ.HSE](https://iq.hse.ru/news/361059490.html) reports that the approximate turnover of the private tutoring market in three years has grown by almost 70 billion rubles. It means that there is the inherent need for additional classes and shows the need to expand and improve the market for services that provide students with personnel, as well as the need for the personnel themselves.

Due to many problems, the largest services and marketplaces lose part of their profits, as well as their potential paying audience. We will list some of them:
* paid trial lessons and their low efficiency;

* inconsistency of the portfolio with reality;

* unwillingness to continue classes after the first meeting;

* waste of time - the most valuable resource of the 21st century;

* decrease in the conversion rate and refusal to use the services of the marketplace.

These are all key factors that inspired the various solutions. Our purpose is to create an API for student and tutor search services that will save them both time and money. The API will select a tutor based on the results of the student's entrance testing, which makes the search as fast, convenient, and efficient as possible. With such software, on each platform it will be possible to competently build interaction between clients and tutors, increase income and popularity in the market.

The API will be a b2b (business to business) solution for a specific service, where the service pays for using the API.

### B. Clients and users
Potential clients - small online-schools, and large services and marketplaces specialising in the provision of educational services (the EdTech market). There are about a hundred services and online schools in Russia involved in the education sector in total. Each of them is currently actively developing and expanding the audience of their potential customers, as well as working to improve the user-experience.

### C. How is the search for a tutor and matching a client with him currently arranged?
1. The client chooses the platform on which he wants to find a tutor.

2. The client registers and draws up his profile.

3. The client is looking for a tutor and sends him an offer to conduct an introductory lesson, or the teacher invites the client to use his services.

4. The client and the teacher agree to conduct a trial lesson (either for free with a time limit, or for the price of one lesson).

5. After the trial lesson, if the tutor is not suitable for the client, the client continues to search for a teacher.

Paragraph *(2)* may entail a discrepancy between the client's knowledge and the portfolio that they or their parents made. You can also notice that items *(3)*, *(4)* and *(5)* can be extremely time consuming and have low efficiency, so there is a need to improve the efficiency of the match between the two sides.

### D. Environment
The service using our API will provide customers with the full access to the required functions. So, users will be able to choose the required subject for writing a test and then solve the test our API had currently generated. After examination, users will receive their results, and tutors will have information about the knowledge gaps of the students and about the topics that the students know well. 
Now, we would like to pay attention to several number of advantages that our solution provides:
1. Users do not need to install additional extensions or download additional software to use this function, since it will already be built into the service.

2. Writing a test paper will allow you to enter actual data about the client's knowledge in general information about him, which will facilitate the search and selection of a teacher and save time for both parties.

### E. Competitors
After getting acquainted with competing solutions, we can note the following types of competitors: replacement and indirect.

The first type includes companies offering related services. For example, Skyeng, whose clients and teachers are matched by analysing the psych types of students and teachers: "We are experimenting with scoring teachers using psychological tests during selection," [says](https://habr.com/ru/post/446970/) the head of product management at the online-school children's department.

The second type describes companies that focus on the same needs of customers of the same market, the EdTech market. For example: [Profi.ru](https://profi.ru), [Repetitor.ru](https://repetitor.ru), [the Association of Tutors](https://repetit.ru/?roistat_visit=39748148), etc.

### F. General information about sphere
1. The demand for the services of tutors is growing, and accordingly, new solutions are required to improve the work of the services for finding teachers.

2. After analysing the market associated with services in the field of education, we identified our goal - to increase the money turnover of services for the selection of tutors by improving user-experience and the quality of their work, and reducing the time allotted for finding a teacher.

3. According to [IQ.HSE](https://iq.hse.ru/news/361059490.html), the approximate turnover of the tutoring market is 100 billion rubles. This turnover is the capacity of the entire market.


## Use cases
First of all, client is a website, program or service that uses our API.

### Getting a screening test

**Description:** The client receives an examination test according to its request.

**Preconditions:** The client is authorised (has access to the service).

**Result:** The client receives a JSON version of the validation test.

**Trigger:** The client sends a request to the service.

**Successful scenario:**

1. The system receives a request.

2. The system checks the request for correctness.

3. The system unpacks the request body, gets the student data, and saves it.

4. The system creates an instance of the test in accordance with the student’s data.

5. The system forms correct answers for test.

6. The system sends a response to the client.

**Alternative scenarios:**

(2) If the request is invalid, the service reports about an error to the client.

### B. Creation of instance of exam test

**Description:** The system creates an instance of test.

**Preconditions:** The client's request is correct.

**Result:** A test is created.

**Trigger:** --

**Successful scenario:**

1. The system receives assignments from the FIPI website in accordance with the student's category.

2. The system determines the topic of each task.

3. The system determines the correct answer for each task.

4. The system generates a unique identifier for the test.

5. The system adds the test job to the database.

**Alternative scenarios:**

(1) If there is no access to the FIPI website or the necessary tasks were not there, the system takes the prepared tasks from the database.

### C. Receiving answers for test

**Description:** The client sends the student answers to the service.

**Preconditions:** The client has successfully received the test.

**Result:** The system receives the student's answers.

**Trigger:** The client sends a request containing student’s answers and a unique ID for the test.

**Successful scenario:**

1. The system receives a request.

2. The system checks the request for correctness.

3. The system unpacks the request body, receives the student's answers, and saves them.

4. The system receives the verification test from the database by a unique identifier.

**Alternative scenarios:**

(2) If the request is invalid, the service reports about the error to the client.

### D. Sending Assessment Results to Client

**Description:** The system sends the student's assessment results in response to a request with his answers.

**Preconditions:** The request with the students' answers was correct.

**Result:** The client receives the student assessment results.

**Trigger:** --

**Successful scenario:**

1. The system compares the student's answers with the correct answers of the test, taken from the database by a unique identifier.

2. The system determines student's knowledge in each topic of the test based on the comparison from paragraph (1).

3. The system compiles a list of test topics and the student's score in this topic.

4. The system generates a response from this list.

5. The system sends a response to the client.

**Alternative scenarios:** --


## Functional and non-functional requirements 

### A. Functional requirements
1. The system should receive input data about the student in JSON format.

2. The system must process input data and choose a test to generate.

3. The system should parse the FIPI website and generate test based on the input data about the student based on tasks from the “open bank”.

4. The system should send test to the server in JSON format.

5. The system should receive response with answers in JSON format for the previously submitted test.

6. The system should analyze answers to the test and validate it.

7. The system should generate a message in which: an indication of gaps in knowledge, an indication of well-mastered topics, a test score on a 100-point scale.

8. The system must send the message from clause 7 to the server in JSON format.

### B. Non-functional
1. The system must check the performance very quickly. (Must be very fast)

2. An Internet connection is required to work with the system.

3. All source files must be fully documented.

4. The format of received and sent messages should be specified in the documentation.

5. The system must be kept confidential.

6. The system must not crash.

7. The system must work in any browser and on any device.

8. The system must be decomposed and allow changes to the source code without prejudice.


## Component model
*<ins>[Component diagram of solution](https://github.com/ShvDanil/Excellent/blob/main/readme_images/Component_model.png)</ins>*
![Component diagram](./readme_images/Component_model.png)

There is a component diagram of a solution above this paragraph. The communication between the client-server and the API, which is responsible for the execution of all work, is realized through internal components located inside the overall system. Each component is a subsystem that performs a specific task that implements a specific function. So, the scheme contains several components:
* **Request Handler.** This subsystem is responsible for receiving the request from the server and transmitting it to the controller.

* **Controller.** This subsystem receives a request from the request processor, processes it and sends it to the appropriate subsystem with data for further work.

* **Data Handler.** This subsystem receives data, works on it, and transmits it for analysis.

* **Analysis module.** This subsystem receives ready data and process it, analyzes, and returns the result to the body of the request handler to transmit the response to the server.

* **API Database.** This is a database containing test samples and answers to them.


## Reference architecture and patterns
Reference architecture and patterns that fit the domain are key things during the project development.

### SOA - Service Oriented Architecture
First of all, list of [basic elements of SOA](https://www.ibm.com/cloud/learn/soa):
* Services;

* Service bus;

* Service repository catalogue of services;

* SOA security;

* SOA governance.

There are different kinds and types of services, but the most suitable for our solution is the **Composite Utility Service**. Since the service is composite, it is assumed for combining several atomic services that are not to further decomposition. This will provide complex composite functionality and allow API to receive data, process it and issue the required response for different requests (request / reply pattern).

**The service bus, or ESP (Enterprise Service Bus),** is the connecting link of the system that provides the exchange of information between the client-server and the API. It is responsible for the orchestration and routing of data received from the user side. (User - server)

The ESB uses the **Service Repository** catalog of services to send a request to a special service that interacts with other service(s) and database(s) to prepare data for the response.

The final two sections, **SOA Security and SOA Governance**, govern SOA security and governance to ensure that a secure and correct client-server transaction (API) is executed.

*<ins>[Schematic presentation of main SOA components interaction](https://github.com/ShvDanil/Excellent/blob/main/readme_images/SOA_scheme.png)</ins>*
![Schematic presentation of main SOA components interaction](./readme_images/SOA_scheme.png)

Having considered the reference architecture let us describe the patters which are used during the development of API.

### Client / Server / Service pattern
Before development, the question arises: how is it possible to associate SOA with a service user interface, where the client side does not support SOA or uses technologies that are incompatible with this architecture?

For this case, we use the **Client / Server / Service pattern**, which allows us to associate the service with our API. Integration of this pattern as a new service on the server side will minimise the impact on the UI and other existing systems. Next, a diagram of this pattern will be presented, where the role of our API depicts the lower layer of the server agent and its interaction with servers A and B.

*<ins>[Common pattern scheme](https://github.com/ShvDanil/Excellent/blob/main/readme_images/Client_Server_Service_pattern.png)</ins>*                          
![Client/Server/Service pattern](./readme_images/Client_Server_Service_pattern.png)

However, the image of this pattern is only generalised, since it in general terms, without any specifics, describes the methods of interaction between the API and the service. For a more detailed description of interactions, let's move on to the next pattern, which contains specific information about the interaction.

### Request / Reply pattern
How can we structure the client-server-API interaction directly and without complexity?

For this case, we need a **Request / Reply pattern** that fully satisfies the requirements for working between the above-described sides. The aim of this pattern is to receive a request and provide a response to it. When a service receives a request from a user, it transmits data to the appropriate API subsystem in the correct format, then the data is instantly processed synchronously and returned in the appropriate format as a response to the original request. Next, a diagram of this pattern will be presented. It depicts a service that sends a request to an API and receives a response to it.

*<ins>[Common pattern scheme](https://github.com/ShvDanil/Excellent/blob/main/readme_images/Request_Reply_pattern.png)</ins>*                          
![Request/Reply pattern](./readme_images/Request_Reply_pattern.png)

