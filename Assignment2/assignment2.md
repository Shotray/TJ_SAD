<center><font size=5 color=#008b8b>Content</font></center> 

[TOC]



<div STYLE="page-break-after: always;"></div>

## 1.Brief Description

### 1.1 Purpose

The purpose of the document is to illustrate the JIYU's architectural analysis and analysis model. What's more, the snapshots of the system's user interface updated with the advancement of our work, so we also include the updated snapshots and annotated references of what we have learned.

### 1.2 Project Scope

The **JIYU ( Meet What You Will Meet )** is a web-based club management system, whose goal is to simplify the club management process and provide an online club social platform. The users can access the system by PC or mobile device through a Website.

Specially, potential scenarios of this system mainly include searching clubs, browsing activities information and club information, joining clubs, dropping out of a club, and so on. Both club members and non-club members can browse the information and join in the activities, make comments through the system after they register and log in. In addition, club members can use the system to organize activities, making the organization easier. As for club union supervisor, they have the authority to manage the online forum and highlight the activities, which simplifies their work.

Compared with **last document**, our system has added a new subsystem which is named as **User Information System**. The subsystem can illustrate the operations when users interact with their own information. Its **Use Case Diagram** will be seen in the **Introduction**.

![gbSGg1.png](https://z3.ax1x.com/2021/05/21/gbSGg1.png)

Besides, this online system also has the listed features: 

- running in a networked environment.
- handling the user authentication for security.
- owning a centralized database and etc.

### 1.3 Glossary of Terms

| Terms                    | Definition                                                   |
| ------------------------ | ------------------------------------------------------------ |
| **JIYU**                 | The name of our system, which means that you will meet the friends after using our system to join the world of different activities. |
| **Club**                 | A club is usually composed of a group of people in the university who have common hobbies and goals. It is also usually an important part of university life. |
| **TOWS**                 | A diagram to analyze the main internal strengths, weaknesses and external opportunities and threats closely related to the research object with the idea of systematic analysis, and draw a series of corresponding conclusions. |
| **Online Forum**         | A website part, which refers to discussions among different people around the same topic |
| **Authority**            | the different operations that each actor can perform when using this system. |
| **Column**               | A collection of the same type of topic posts in the forum.    |
| **Publicize Activities** | the club union supervisor can post the activities reported by the associations to the homepage, so that more people can pay attention to the activities. |
| **Report**               | Some complaints made by users about the inappropriate columns or comments (e.g.: insulting people or spreading terrifying information) on the forum. The supervisor will check whether it's a proper report. |
| **Club Statics**         | Data on the development of the club, usually including changes in the number of clubs over time, participation in activities, etc. |
| **Resume**               | In our system, it refers to an account's basic information when registered, including email, cellphone number,student ID and some other minor information. |
| **Activity**             | The online or offline activity held by the university club, whose main body is users or club members. |
| **Modify Permission**    | The system modifies the user's authority and changes the scope of the user's function. |

### 1.4 Target Readers and Suggestions

This document is for the developers and users of **JIYU** ( Meet What You Will Meet ) club communication system and others involved in it.

To get an overview of the document, we suggest that all readers read Part1, which is a brief introduction to this system.

Part 2 includes the updates of the goals and illustrate progress made since the previous document. In this part you can get the knowledge of changes about our system.

For details of the architectural decisions, you may read Part 3, from which you will know more about the high-level architecture and system-level analysis of JIYU club communication system.

Focusing on the functions, Part 4 will show you the sequence diagram for use cases and class diagram for further development.

To be familiar with the updates in our system in an intuitive way, you can read Part 5 to see the update snapshots.

Part 6 (Annotated References) show the list of references for this document, and Part 7 gives the contributions of team member.



<div STYLE="page-break-after: always;"></div>

## 2.Introduction

### 2.1 Goals

At present, most club platforms are managed manually, which cannot achieve the purpose of real-time update of personnel data and active promotion of club activities. Besides, most club management system only focus on single club function and do not combine the periphery functions. Therefore,it is great to shift the focus on integrating club information with big data and software development technology to make the system more comprehensive. By constructing a club management system, it is convenient for different users to participate in it well.

To solve the problems, **the Club Communication Platform** mainly aims to build an online student club management system with the purpose of simplifying club management process and achieving real-time club data updating,which promises different kind of target users can take part in club activities or club management with convenience.

### 2.2 Progress and Current Status

In the first document, we have already provided readers with a detailed description of the functionalities of JIYU( Meet What You Will Meet ), and this document covers the progress of analysis model and architectural analysis. 

In this System Analysis Document, we have presented the project in terms of high-level architecture, detailed architectural decisions until current stage. We create the layer architecture diagram of the system and built the package diagram to illustrate the components of each layer.

To make system more reliable and easier to be developed, the document present analysis model which includes sequence diagram and class diagram. For sequence diagram, the developers can get to know how the system works in every use cases. As for class diagrams, it presents relationship between entity classes, boundary classes and control classes.

Besides, we also update our system during analysis. A new subsystem is added to make the system more completed, which will be introduced in next subsection. And the snapshots of system are also changed to be more user-friendly and function-completed.

### 2.3 Changes in the System

In the construction of the analysis model this time, we found that there were some operations can be optimized:

- Only allow access to the data through given interface to avoid direct access to the database, which may cause errors in the data of the database.
- Separate all classes into three parts: boundary class, control class and entity class to make the system clearer and safer.
- Add a new subsystem named **User Information System** to make it easier for user to interact with their information.
  <img src="https://z3.ax1x.com/2021/05/21/gHzgk4.png" alt="gHzgk4.png" style="zoom:67%;" />
- Modify the use case diagram appropriately.

<div STYLE="page-break-after: always;"></div>

## 3.Architecture Decisions

### **3.1 System-Level Architecture Analysis and Designs**

JIYU system is a based on the web platform focusing on club management and communication between diffrent people. In order to promote the club communication platform by taking advantage of the system and seize the opportunity, on the one hand, from the user perspective we should pay attention to the rich and complete functions and the security and confidentiality of personal information in the system. On the other hand, we should extract the same functions and mechanisms in the business to improve the platform performance and availability from the perspective of developers. 

#### 3.1.1 System detailed analysis

In the requirement phase, we focus on the interaction between different objects outside the system and all the system. We also complete the preliminary analysis of the system in the form of use cases. In the early stage of architecture design, we consider the specific behavior steps of the system to realize the use case, further divide the system into smaller granularity systems according to the function, and complete the transformation of the use case in the form of robust graph.

<img src="https://z3.ax1x.com/2021/05/11/gaxIz9.png" alt="gaxIz9.png" style="zoom: 33%;" />

- Robustness diagram of activity management system  

<img src="https://z3.ax1x.com/2021/05/11/gaxzzd.png" alt="gaxzzd.png" style="zoom: 50%;" />

- Robustness diagram of club management system

<img src="https://z3.ax1x.com/2021/05/11/gazFdf.jpg" alt="gazFdf.jpg" style="zoom: 50%;" />

Through the classification of functions, the system is divided into login registration system, activity management system, club management system, member management system, forum system and personal information maintenance system. On this basis, we carry on the hierarchical structure of the system according to the **responsibility** and **universality**, and divide the system into subsystems.

#### 3.1.2 Hierarchical architecture design

The traditional three-layers architecture design is as follows:

<img src="https://z3.ax1x.com/2021/05/11/gdSQcd.png" alt="gdSQcd.png" style="zoom: 33%;" />

We complete the architecture analysis and design of the system by subdividing the traditional three-layer logic system architecture. The system-level architecture can be expressed as the below figure:

<img src="https://z3.ax1x.com/2021/05/21/gbpfL6.png" alt="gbpfL6.png" style="zoom:50%;" />

Combined with the functions of the system, we integrate the above architecture design into the JIYU system by means of package diagram and components:

<img src="https://z3.ax1x.com/2021/05/21/gbSpB8.png" alt="gbSpB8.png" style="zoom: 33%;" />



##### 1.Presentation Layer

The presentation layer contains the interface information and components that interact with users. The presentation layer responds to user events through components, and encapsulates the page data as VO (view object), which can be directly transferred to the application layer components for further business logic processing, and can also directly call the external API to realize functions.

<img src="https://z3.ax1x.com/2021/05/11/gdSFXR.png" alt="gdSFXR.png" style="zoom:50%;" />

- Interface interaction component 

  Display UI and trigger components of binding events for users.

- Data encapsulation component

  Encapsulate the collected data as VO.

- Message feedback component

  Feedback the interaction between users and the system.

- Data transmission component

  Transfer the encapsulated VO to the external interface layer or application layer.

##### 2.Application Layer

The application layer is responsible for the data scheduling between the presentation layer and the business logic layer. It takes out the data information in the VO transferred by the presentation layer, encapsulates it as DTO and passes it to the business interface layer components to realize the business logic processing. On the other hand, it repackages the data returned by the business interface layer as VO and returns it to the presentation layer for users.

<img src="https://z3.ax1x.com/2021/05/11/gdpxWF.png" alt="gdpxWF.png" style="zoom:50%;" />

- Data unpacking component

  The object will be unwrapped to get the data information.

- Data encapsulation component

  Encapsulate the data as DTO/VO.

- Data transmission component

  Transfer the encapsulated object to the business interface layer or presentation layer.

##### 3.External API Layer

The external API layer is to accept the data objects of a certain layer or a certain subsystem, call the external interface for logical processing, and then return the data objects for the subsystem or presentation layer to use.

<img src="https://z3.ax1x.com/2021/05/11/gd9nQH.png" alt="gd9nQH.png" style="zoom:50%;" />

- Data transmission component

  Return the result of external calling interface to presentation layer, application layer or a subsystem.

- External API

  The business logic can be realized through the external API.

  External function calls in external interface package to realize some business logic:

  <img src="https://z3.ax1x.com/2021/05/11/gd9aOs.png" alt="gd9aOs.png" style="zoom:50%;" />

With the expansion of the system requirements and functional improvement, the expanded external interface will not have a significant impact on the architecture design.

##### 4.Business Interface Layer

The business interface layer is the embodiment of the external functions of the system. The controller layer transfers the data to the business interface layer. The business interface layer calls the corresponding business implementation layer components to complete the business logic processing, and returns the processed information upward through the business interface layer.

<img src="https://z3.ax1x.com/2021/05/11/gd9b1e.png" alt="gd9b1e.png" style="zoom:50%;" />

- Data transmission component

  Transfer the upper data to the business implementation layer, and transfer the results to the controller layer.

- Business Interface

  Provide the external function interface of the system, call the lower layer to realize the specific logic classification.

  The business interface package is divided into different systems according to their functions, which is conducive to the iterative development of the system in depth.

  Different system interface packages contain the specific functional interfaces that the system can achieve.

  <img src="https://z3.ax1x.com/2021/05/11/gdCAns.png" alt="gdCAns.png" style="zoom:50%;" />

##### 5.Business Implementation Layer

Business implementation layer is the core of the whole hierarchical architecture, through which business logic is processed.

<img src="https://z3.ax1x.com/2021/05/11/gdC3u9.png" alt="gdC3u9.png" style="zoom:50%;" />

- Data transmission component

  Accept the data from the business interface layer and transfer the data to the data access layer according to the business requirements.

- Business Implementation

  The business logic processing with smaller granularity is located in the business implementation package. In order to support depth first iterative development, the package is also divided into different areas according to different functions.

  ![gdCwge.png](https://z3.ax1x.com/2021/05/11/gdCwge.png)



##### 6.General Service Layer

The general service layer is the mechanism function extraction of logic processing in the business implementation layer to improve the reusability of business logic processing.

<img src="https://z3.ax1x.com/2021/05/11/gdCfgg.png" alt="gdCfgg.png" style="zoom:50%;" />

- Data transmission component

  Accept the data from the business interface layer and transfer the data to the data access layer according to the business requirements.

- General Service

  The general service package contains some generic business methods that can be called by the business implementation layer.

  <img src="https://z3.ax1x.com/2021/05/11/gdCIDs.png" alt="gdCIDs.png" style="zoom:50%;" />

##### 7.DTO Component Library

DTO (data transport object) layer contains different classes defined according to the needs of business logic. The use of DTO is conducive to the transmission of useless information, and improves the operation efficiency and data security.

<img src="https://z3.ax1x.com/2021/05/11/gdCxKJ.png" alt="gdCxKJ.png" style="zoom:50%;" />

##### 8.Business Entity Library

The business entity layer defines the system data class for business logic processing and mapping with the data source, which reduces the number of interactions with the data access layer and improves the security of data operation.
<img src="https://z3.ax1x.com/2021/05/11/gdP0iV.png" alt="gdP0iV.png" style="zoom:50%;" />



##### 9.Data Access Layer

The data access layer is mainly responsible for accessing the database, adding, deleting, modifying and querying the data table, and returning the corresponding data for the business logic layer.

<img src="https://z3.ax1x.com/2021/05/11/gdPUZn.png" alt="gdPUZn.png" style="zoom:50%;" />

The data access layer mainly defines the methods used for database connection and operation. With the rich functions of the system, the data access layer will also adopt the form of separating the interface from the general service layer to improve the reusability of some services.



##### 10.Common Service Library

The comment service library contains some functional services which are closely related to all levels of the system architecture for the components of all levels to call.

<img src="https://z3.ax1x.com/2021/05/11/gdPdI0.png" alt="gdPdI0.png" style="zoom:50%;" />

<div STYLE="page-break-after: always;"></div>

## 4.Analysis Model

### **4.1 Login & Register System**


#### 4.1.1 Class Diagram

<img src="https://z3.ax1x.com/2021/05/21/gbkdy9.png" alt="gbkdy9.png" style="zoom: 80%;" />

#### 4.1.2 Interaction Diagram


This sequence diagram shows how Visitors login or register a new account to gain User Authorities.Followed by a corresponding communication diagram.

<img src="https://z3.ax1x.com/2021/05/21/gbkwLR.png" alt="gbkwLR.png" style="zoom: 50%;" />

<img src="https://z3.ax1x.com/2021/05/21/gbkaQJ.png" alt="gbkaQJ.png" style="zoom:67%;" />

<div STYLE="page-break-after: always;"></div>

### **4.2 Club Change System**

#### 4.2.1 Class Diagram

<img src="https://z3.ax1x.com/2021/05/21/gHXRMT.jpg" alt="gHXRMT.jpg" style="zoom:67%;" />



#### 4.2.2 Interaction Diagram

##### 1.Establish New Club

This sequence diagram shows how a user establish a new club and how the club union supervisor review the creating club application.

![gHXIo9.jpg](https://z3.ax1x.com/2021/05/21/gHXIo9.jpg)

##### 2.Modify Club Information

This sequence shows how Club Leader Modify Club Information and how Club Union Supervisor review the modifying club application.

![gHXDaj.jpg](https://z3.ax1x.com/2021/05/21/gHXDaj.jpg)

##### 3. Dismiss Club

This sequence diagram shows how Club Leader dismiss a club.

![gHj9JI.jpg](https://z3.ax1x.com/2021/05/21/gHj9JI.jpg)

<div STYLE="page-break-after: always;"></div>

### **4.3 Activity Organization System**

#### 4.3.1 Class Diagram

![gbVmRO.png](https://z3.ax1x.com/2021/05/21/gbVmRO.png)



#### 4.3.2 Interaction Diagram

##### 1.Organize the activities

After the club leaders click to launch a new activity, they can fill in the information of the activity. After the necessary information is completed, they will fill in the application form and the activity in the activity form. The status of the activity will be added to the status of not approved. After that, they will return the corresponding information to the club leaders.

![gbVEIx.png](https://z3.ax1x.com/2021/05/21/gbVEIx.png)

##### 2.Review the Activity Application

The club supervision can click to view the activity information of the application, and can choose to accept the application for the activity, give the corresponding modification opinions or refuse the activity application and give the reasons.

![gbVAd1.png](https://z3.ax1x.com/2021/05/21/gbVAd1.png)

##### 3.Participate in the Activity

After the user selects the activity interface, he chooses an activity according to his interests to view specific information, and chooses to participate in the activity to fill in the information, and then submit the activity application and receive feedback.

![gbVeJK.png](https://z3.ax1x.com/2021/05/21/gbVeJK.png)

##### 4.Publicize the Activity

Club members can choose to volunteer to participate in activities, submit the application form and wait for approval.

![gbVZi6.png](https://z3.ax1x.com/2021/05/21/gbVZi6.png)

<div STYLE="page-break-after: always;"></div>

### **4.4 Membership Change System**

#### 4.4.1 Class Diagram

<img src="https://z3.ax1x.com/2021/05/21/gbScKP.png" alt="gbScKP.png" style="zoom: 50%;" />

#### 4.4.2 Interaction Diagram

These two sequence diagrams show how the club leader apply to resign, as well as how the Club union Supervisor review the application.

<img src="https://z3.ax1x.com/2021/05/21/gHjuYn.png" alt="gdAJf0.png" style="zoom:50%;" />

<img src="https://z3.ax1x.com/2021/05/21/gHjGmF.png" alt="gHjGmF.png" style="zoom: 50%;" />

<div STYLE="page-break-after: always;"></div>

### **4.5 Online Forum System**

#### 4.5.1 Class Diagram

![gbVfOJ.png](https://z3.ax1x.com/2021/05/21/gbVfOJ.png)

#### 4.5.2 Interaction Diagram

##### 1.Forum Interaction

This sequence diagram shows the action that user interact with the forum. User can Create Column and Leave Comments on the forum. If User is in the blacklist, he or she can do neither of things, otherwise the Forum Page will show the comment or column on the page.

<img src="https://z3.ax1x.com/2021/05/11/gdA26O.png" alt="gdA26O.png" style="zoom:67%;" /> 

##### 2.Report Illegal User Account

The sequence diagram shows how the Club Union Supervisor update the black list and how the system add the student to the database. 

<img src="https://z3.ax1x.com/2021/05/11/gdAg1K.png" alt="gdAg1K.png" style="zoom:67%;" />

##### 3.Search Column

This sequence diagram shows how the user search a column in the forum and how the system search the data in the database.
A corresponding communication diagram of this use case is appended.

<img src="https://z3.ax1x.com/2021/05/11/gdAcp6.png" alt="gdAcp6.png" style="zoom:67%;" />

<img src="https://z3.ax1x.com/2021/05/21/gb9AO0.jpg" alt="gb9AO0.jpg" style="zoom:67%;" />

##### 4.User Report

This sequence diagram shows how the user report comments and the system send it to club union supervisor.

<img src="https://z3.ax1x.com/2021/05/11/gdAyfx.png" alt="gdAyfx.png" style="zoom:67%;" />



<div STYLE="page-break-after: always;"></div>

## 5.Updated Use Case Model

### 5.1 Updated System: User Information System


![gHjYTJ.png](https://z3.ax1x.com/2021/05/21/gHjYTJ.png)

### 5.2 Modified System: Membership Change System

![gbVDwn.png](https://z3.ax1x.com/2021/05/21/gbVDwn.png)

Compared with the previous version, we add user filling the application form and club leader reviewing user application procedures. In that case, we can provide a more comfortable and harmonious communication and entertainment environment for the club members.

<div STYLE="page-break-after: always;"></div>


### 5.3 Modified System: Activity Organization System

![gbC05F.png](https://z3.ax1x.com/2021/05/21/gbC05F.png)

The use case diagram modification of activity organization system focuses on the promotion of community leaders' power. Community leaders can manage activities, upload materials or delete activities that have been carried out, and the operation of new activities can also be moved to the management activities section.



### 5.4 Modified System: Online Forum System

![gbPCMn.png](https://z3.ax1x.com/2021/05/21/gbPCMn.png)

Compared with the previous version,we add a extended use case **search column** ,which allows users to search for particular columns on the forum.

### 5.5 Use Case Detailed Specification

System: User Information System

Use Case: Modify Information

| USE CASE         | MODIFY USER INFORMATION                                      |
| ---------------- | ------------------------------------------------------------ |
| ID               | UC17                                                         |
| Specification    | Allows user to modify his or her self information            |
| Actors           | **User**                                                     |
| Pre-condition    | None                                                         |
| Basic Path       | 1. The use case starts when User requests to modify his or her self information <br />2. User fill the information needed<br />3. System updates the information |
| Alternative Path | 1. User doesn't fill all the information<br />     1.1 User receives a warning message says "The information cannot be empty"<br />     1.2 User input the information<br />2. User logs out of the system |
| Post-condition   | None                                                         |



System: Membership Change System

Use Case: Join A Club

| Use case         | join a CLUB                                                  |
| ---------------- | ------------------------------------------------------------ |
| ID               | UC18                                                           |
| Specification    | user applies to join a club                                  |
| Actor            | user, club leader                                            |
| Pre-Condition    | The user wants to join a new club.                           |
| Basic Path       | 1. The user click the button to join a new club; <br />2. Club leader review the application.; <br />3. After the review is passed, the authority of the user will be changed in the background. And basic information of the club will be updated at the same time. |
| Alternative Path | The club leader rejects the application of the user.         |
| Post-Condition   | The user becomes a member of the club and the basic information of the club is updated. |


System: Activity Organization System

Use Case: upload activity information

| Use Case         | upload activity information                                  |
| ---------------- | ------------------------------------------------------------ |
| ID               | UC19                                                         |
| Specification    | The club leader can provide supplementary information for the activities, and upload activity photos, documents and other format recording materials for the activities that have been carried out. |
| Actors           | **Club Leader**                                              |
| Pre-condition    | Club Leader successfully login and has authority to manage the club activities. |
| Basic Path       | 1. Club Leader clicks to login the system<br>2. Club Leader clicks to manage the activity<br>3. Club Leader clicks to upload activity information<br>    3.1 Club Leader uploads the text information<br>    3.2 Club Leader select the upload attachment<br>4. Club Leader click to submit upload information |
| Alternative Path | 1. The activity has not been carried out yet<br>    1.1 Club Leader will receive the message that he can't select the upload attachment<br>    1.2 Club Leader exit upload attachment section<br>2. If user logs out during the process of filling in the information by accident, the content will remain<br>3. Club Leader leaves the page during the process of filling in the information<br>    3.1 Club Leader will receive the message on whether submit or save the content<br>    3.2 If Club Leader chooses to submit, the upload will be submitted automatically<br>    3.3 Otherwise, the upload will not be saved and user will leave the page |
| Post-condition   | None.         |


System: Online Forum System

Use Case: Search column

| Use case         | search column                                             |
| ---------------- | ------------------------------------------------------------ |
| ID               | UC19                                                      |
| Specification    | Users search particular columns.                                  |
| Actor            | User                                         |
| Pre-Condition    | Users enter the forum page                         |
| Basic Path       | 1. User types in contents he wants to search for; <br />2. The user click the search button; <br />3. System returns the search result. <br />4.Related columns are shown on the page.|
| Alternative Path | If system can't find any related columns,it will return with "related columns not found" result to the user.         |
| Post-Condition   | None. |


<div STYLE="page-break-after: always;"></div>

## 6.Update Snapshots

### 6.1 New Use Case Snapshots

#### 6.1.1   User Participates in Activities

Description: a snapshot of the web page to fill in the activity registration form is added. Users can fill in their own relevant information (such as contact information, registration reasons, etc.) on this page as the information required for activities.

![gHjRfI.jpg](https://z3.ax1x.com/2021/05/21/gHjRfI.jpg)


<div STYLE="page-break-after: always;"></div>

#### 6.1.2 User Views Club Activities

Description: a snapshot of the view-event page is appended. Users can view the activities organized by participating clubs and non-participating clubs on this page。

![gHjT0g.jpg](https://z3.ax1x.com/2021/05/21/gHjT0g.jpg)

<div STYLE="page-break-after: always;"></div>

#### 6.1.3 User modifies Personal Information

Description: a snapshot of the web page to modify personal information is appended. Users can maintain personal information (including nickname, brief introduction, etc.) on this web page.

![gHjbkj.jpg](https://z3.ax1x.com/2021/05/21/gHjbkj.jpg)
<div STYLE="page-break-after: always;"></div>

#### 6.1.4 User Checks Participated Activity Information

Description: a snapshot of the web page to check participated activity information is appended. Users can view the club activities they participate in on this page, so as to control the place and time.

![gHjqts.jpg](https://z3.ax1x.com/2021/05/21/gHjqts.jpg)

<div STYLE="page-break-after: always;"></div>

#### 6.1.5 User Apply For Leadership

Description: a snapshot of the member serving applying page is appended, which is used by the club member to apply for inaugurating. On this page club members  submit their application information which will be reviewed by the Club Union Supervisor.  

![gHviN9.jpg](https://z3.ax1x.com/2021/05/21/gHviN9.jpg)

<div STYLE="page-break-after: always;"></div>

#### 6.1.6 Review User Join Application

Description: a snapshot of the user join reviewing page is appended, which is used by club leader to review the application submitted by users who want to join. On this page the club leader can click the applicant avatar to view the application and decide whether to approve users' application.  

![gHxIoQ.md.jpg](https://z3.ax1x.com/2021/05/21/gHxIoQ.md.jpg)

![gHvnBD.jpg](https://z3.ax1x.com/2021/05/21/gHvnBD.jpg)

<div STYLE="page-break-after: always;"></div>

#### 6.1.7 User Joins a Club

Description: a snapshot of the user join page is appended, which is used by users to apply to join an interesting club. On this page users submit their basic information which will be used for club leader's reviewing. 

![gHvMAH.jpg](https://z3.ax1x.com/2021/05/21/gHvMAH.jpg)

<div STYLE="page-break-after: always;"></div>

#### 6.1.8 Quit the Club

Description: a snapshot of the resignation applying page is appended, which is used by the Club Leader or Minister of Finance to apply for resignation. On this page club leader and minister of finance submit their resignation information which will be reviewed by the Club Union Supervisor. 

![gHv83t.jpg](https://z3.ax1x.com/2021/05/21/gHv83t.jpg)


<div STYLE="page-break-after: always;"></div>

#### 6.1.9 Modify Information

Description: a snapshot of the club information modified page is appended, which are used by the club leader to modify club information. On this page the club leader submits the updated club information which will be used for club union supervisor's reviewing. 

![gHvGgP.jpg](https://z3.ax1x.com/2021/05/21/gHvGgP.jpg)

<div STYLE="page-break-after: always;"></div>



### 6.2 Modification of the Original Use Case Snapshots


#### 6.2.1 Find Club

Description: compared with the previous version, we append "Create A Club of Interests" module in account that the users want to establish a new club.

![gHvtu8.jpg](https://z3.ax1x.com/2021/05/21/gHvtu8.jpg)
<div STYLE="page-break-after: always;"></div>

#### 6.2.2  Club Member Arrangement

Description: compared with the previous version, we append "Applying Member" navigation bar item of navigation item "Member Arrangement" in account that the club leader need to review user join application. 

![gHvDCn.jpg](https://z3.ax1x.com/2021/05/21/gHvDCn.jpg)

<div STYLE="page-break-after: always;"></div>

## 7.Reference

### 7.1 Tan Yunjie. (2012). Elephant: Thinking in UML. Beijing: China Water Conservancy and Hydropower Press.

By using UML as the carrier, this book ingeniously integrates object-oriented analysis and design ideas into the modeling process, and organically combines all aspects of the software system development process via examples throughout the book, from which we learned concept and drawing method of sequence diagram, collaboration diagram, class diagram as well as how to apply them to our system analysis.

In chapter 4, we learned how to draw class diagram, sequence diagram and collaboration diagram. UML uses class diagrams to represent classes, interfaces, and their associations. Classes have Attributes and methods. There is also a relationship between classes, such as association, aggregation, generalization, and so on. We have designed class diagrams as shown in chapter4 based on these knowledge.

The sequence diagram describes the events which occur in the objects participating in the interaction, and how these objects communicate by sending messages to each other. Based on these concepts, we have drawn some sequence diagrams for the main use cases in JIYU club management system, as shown in chapter 4.

Since the collaboration diagram presents almost the same information as the sequence diagram, we directly converted it into a collaboration diagram based on the above sequence diagram.

### 7.2 Wen Yu. (2009). Design guide for first-line architects. Beijing: Electronic Industry Press.

This book summarizes the frequently encountered problems in software architecture design, expounds the three stages of software architecture design, the Pre-Architecture phase, the Conceptual Architecture phase and the Refined Architecture phase, and gives the best practice principles and methods, from which we learned how to perform architectural analysis of JIYU club management system.

Chapter 8 describes how to make a preliminary design of a system. The goal of the preliminary design is to discover responsibilities simply and clearly and use this as the basis for subsequent architecture design work. As each "High-Level Segmentation Unit" is the carrier of the responsibilities, and the purpose of the segmentation is to plan the high-level responsibility model precisely, the subsequent high-level segmentation plan will have a foundation after the responsibilities identified in the preliminary design. This chapter also introduces how to use robustness diagram to aid preliminary design. Based on this, we designed the robustness diagram of JIYU club management system to assist in dividing the system into subsystems.

In chapter 9, this book interprets the concept and practical essentials of hierarchical conceptual service architecture. In practice, stratification has different perspectives and is usually summarized as the "3 + 1" genre (logical layer, physical layer, layered by versatility, and technology stacking), which do not contradict each other. The layered method by versatility refers to dividing system into parts with different versatility into different layers as an overall segmentation method of the system.

Chapter 13 explains how to carry out logical architecture design and subsystem partitioning more rationally and professionally from three aspects, hierarchical refinement, partition introduction, and mechanism extraction.

Based on the above knowledge, having considered the domain concept, system complexity and functional characteristics, we subdivide our system functions on the basis of the traditional three-tier architecture according to the principle of separation of duties, the principle of separation of general, the principle of special purpose, the principle of skills separation and the principle of workload balance. Finally, we carried out the architecture analysis of JIYU club management system as shown in chapter 3, which fits our requirement quite well. 

### 7.3 Kenneth E. Kendall, Julie E. Kendall.(2014) System Analysis and Design, Ninth Edition. Pearson Education Press.

This book combines the author's years of teaching and practical experience, from five aspects of the system analysis basis, information demand analysis, demand analysis procedure, design basis, quality assurance and realization, with a clear structure, vivid language and rich cases, comprehensively explaining the theories and tools involved in system analysis and design.

Chapter 10 introduces how to draw a package diagram. There are many different types of package diagram. The logical package diagram indicates which classes or use cases are combined into a subsystem; the component package diagram contains the physical group components of the system and the use case package diagram contains a set of use cases. The folder symbol is used to represent a package diagram, and the package name is on the folder label or in the center of the package diagram. Package diagram can also have relationships, including association relationships and inheritance relationships, which are similar to relationships in class diagram. According to these principles, we design component packages, use case packages and etc for each layer.

The design goals of effective output and general guidelines for screens designing are explained in chapter 11. When designing web pages, keeping page simple, maintaining the consistency of the page display, creating attractive pages and other factors should be taken into consideration. From this part, we learned the design principles of the Graphical User Interface (GUI) and use them into our project to make UI more user-friendly.

<div STYLE="page-break-after: always;"></div>
## 8.Contributions

This system analysis project has been discussed for five times. In the process of completing this task, all team members actively participate in the discussion and strive to complete their own tasks. Team members cooperate harmoniously, communicate and solve problems in time. The division of labor within the group was average and clear, as follows:



$i$. **Brief Introduction**:
The brief introduction is written by Ningyu Xiang.

$ii$. **Introduction**:
The introduction is written by Ningyu Xiang.

$iii$. **Architectural Analysis:**
The architectural analysis is written by Liyou Wang.

$iv$. **Analysis model**:
All members in group participate in model analysis.

$v$. **Use Case Specification**:
All members in group participate in completing the use case specification.

$vi$. **Updated use case model:**
All members in group participate in use case model updating.

$vii$. **Updated snapshots of the system’s user interface:**:
All members in group participate in snapshots updating.

$viii$. **Annotated references:**
The reference is written by Zhongyue Chen.

$ix$. **Contributions of team members**:
The presentation PPT is mainly made by Mingjie Wang.

$x$. **Contributions of team members**:
The team member contributions are written by Zhongyue Chen.

$xi$. **Document:**
The document is integrated and beautified by Kaixin Chen.

​	


| Student Number | Name          | Score Weight |
| -------------- | ------------- | ------------ |
| 1851055        | Mingjie Wang  | 100%         |
| 1954098        | Ningyu Xiang  | 100%         |
| 1951724        | Kaixin Chen   | 100%         |
| 1851049        | Zhongyue Chen | 100%         |
| 1851231        | Liyou Wang    | 100%         |