---
layout: post
title: "How the Different Software Development Specializations tie-in Together"
date: 2020-05-22
---

Imagine for a moment that you were outside your company, looking in at the various software products. Clearly, an overarching architecture couples all the components together. This architecture likely provides a separation between the customer facing software and the backend system that supports it. It also decides how and which components talk to each other.

For each component, there is a set of goals to be met. Each component will have its own architecture that prioritizes its functional and non-functional requirements. It is at this level that choices of what to build with are usually made. I would like to explore the different specializations that are required to build the full suite of components, but beyond that, try to figure out what separates the different specializations, what each is made of, and where the concrete lines are drawn.

## Server-side

Server-side means computation is carried out on a web server or a cluster of servers.

### Backend Development

Backend development is a term usually used to describe the one half of web development that I daresay is the backbone of the web. Backend development refers to the server-side software that is deployed to remote computers. This software serves as the skeletal framework that supports a good range of a business's needs. Think for a moment about what this would include. Every business needs to store data. This is the core of backend development, in a nutshell. Out of this primary concern come the rest. The ways in which the data is structured, stored, accessed and secured are the concerns of backend development.

A single comprehensive backend system can support a wide range of products; desktop, mobile, and web applications. For instance, multiplayer gaming systems are made possible because of backends. Serving downloads and rolling out updates usually rely on content delivery network backends. These are just a few examples of what is made possible by backend systems. It is evident that the backend is integral to the operation of a software company.

Several sub-skills are required to build a performant, secure and scalable backend; database design and administration, high-level programming, system administration, etc. Each of these skills can take a considerable amount of time to master.

The server-side is made up of different conceptual layers. There is the database layer, the application layer, and the infrastructure layer.

On the database layer, data is architected to fit in to business requirements and other non-functional requirements such as security, integrity, and access speed. Backend operations are sometimes termed CRUD; create, read, update and delete. These are all operations carried out on data and databases.

The infrastructure layer deals with the approach taken to deploy the backend onto physical machines. On the scale at which companies usually operate, this could mean cloud infrastructure that orchestrates the use of multiple machines and maintains concurrency. Recently, questions of deployment and scalability on the infrastructure layer have given rise to the relatively new DevOps role. Read about DevOps [here](https://www.atlassian.com/devops)

The application layer defines data access protocols, resource permissions, authorization rules, and an API. This API or application programming interface is the point of access for the various client-side applications deployed to user machines. The API is what ties in the products of the other development specializations. Other developers do not need to know the inner workings of the backend to build a coherent user experience across platforms, they only need know of the API and its documentation. That  is the overarching theme of this article; how the server-side works with the client-side.

## Client-side

Client-side means that computation is carried out on the user's machine or device.

### Frontend Development

Frontend development typically refers to the other side of the web development coin. It involves building the products that the user interacts with directly. Frontend development is done on the client-side. While frontend is frequently shorthand for HTML, CSS and JavaScript, it is not necessarily equivalent to client-side. I think this distinction is important, since mobile and desktop application development are also client-side development.

I should say, that there are different flavors of frontend development. There's the largely static, server-rendered website, and the modern JavaScript single page application. The former kind of application does not possess some of the dynamic features that make SPAs so versatile. I confess that there is a lot of nuance around this topic and I cannot possibly cover all the different classifications of what frontend development is. The Frontend Masters [frontend handbook](https://frontendmasters.com/books/front-end-handbook/2019/) is a great resource to get started with. I focus on the SPA flavor of frontend development in this article, although what is discussed easily applies to other areas.

Frontend developers write code that makes calls to server-side web APIs to perform common functions like authentication, data submission, and data retrieval. They write code to perform input validation, local data persistence, and business specific functions. They also implement the user interface specification.

Frontend developers have certain peculiarities to deal with, most of them due to their deployment platform, the browser. For instance, they need to implement responsive user interfaces across different browser implementations and device sizes, usually within the same codebase. They also need to prevent against vulnerabilities and attacks unique to the browser, such as cross-site scripting (XSS) and cross-site request forgery (CSRF).

It is advantageous for a company to deploy its application to the web for some reasons. There is easy or no installation, easy deployment of updates, and it targets multiple platforms. On the flip side, if you are building for users who live in areas with a poor internet connection, a web application might not be the way to go. Also, applications that require large amounts of data entry might not be well suited for a browser interface. Graphics intensive applications like games and simulations are also not best suited for the web. Knowing these advantages and disadvantages helps guide decisions on which services to offer through what medium.

### Desktop Application Development

Desktop development refers to applications built to run on specific desktop operating systems, most commonly Linux, Windows, and Mac OS.

Desktop applications offer a native user interface, access to low level operating system APIs, and better control over the computer's hardware resources. Now, not all desktop applications are low level, hardware intensive software. Sometimes, a business just wants to offer better integration with user devices without needing to open up a browser. Desktop applications cater to the little guys too. Then, there are the big boys; games, simulation software, virtual machines, developer tools, SDKs, etc. These are complex applications that can only be deployed to the desktop environment.

Desktop applications offer two distinct user interfaces. The graphical user interface, and the console interface. Console interfaces are best suited for batch processing applications and automation tasks, GUIs are suited for whatever else. Sometimes, a desktop application has to have both interfaces.

While desktop applications offer better performance for certain type of applications, it has its drawbacks. For instance, it is difficult to maintain the same codebase for multiple desktop environments. Few development platforms are truly cross-platform across the major desktop operating systems. So developers end up having to rewrite some part of their application, usually the UI layer, for separate operating systems and maintain multiple codebases. Also, choosing a deployment and updating infrastructure that is consistent across platforms for desktop applications is a challenge. Preventing revenue loss from software theft is another issue.

It is possible to create desktop applications that do not connect to the internet or integrate with any backend services, but that is rare. It is customary to have some application features that work offline and others that require an internet connection.

In the context of this article, we are examining how these separate specialization areas of development work together. For this goal, a company will tailor the services that only perform well on the desktop to a desktop application package. The web application could provide complementary services like payment and subscription, a control center/dashboard, download pages, user support, etc. You could throw in a mobile application on this client-side where necessary as well. The web, mobile, and desktop applications all rely on a backend service. This is a very common architecture for building a company's suite of services.

The internal architecture for desktop applications is less easy to describe. It largely depends on the product(s) being built. Any architecture under consideration has to account for the system of input devices required by the application, the amount of low level implementation, data persistence, and whether it is compute bound, I/O bound, or a mix of both. Usually, a desktop application will require an interweaving of a few different architectures.

### Mobile Application Development

Mobile application development refers to applications built to run on Android and iOS smartphones, and might extend to wearables like smartwatches. There are other mobile operating systems, but they have a negligible market share.

Each of these platforms provide their own custom development tools to build applications. These applications are referred to as native. Native applications have the ability to use device specific hardware such as microphones, cameras, GPS, etc. And this is where mobile applications shine. Mobile devices provide for a special computational need, they are portable and usable on the go, rich with an array of sensors, and easy to use. They are also more ubiquitous than personal computers. This means a business targeting mobile platforms can reach a large pool of customers.

There is an interesting connection between frontend and mobile development; hybrid application development. Original hybrid app frameworks made use of WebViews to port web applications to mobile. These applications were slow and did not provide a native experience for users, although they had the advantage of building and maintaining a single codebase for the frontend and mobile applications. More modern frameworks like React Native while using web technologies and tools, provide an implementation outside of WebViews to give a truly native experience. This means developers can maintain a core codebase and target web, iOS, and Android, with modifications made for parts of the application specific to the individual platforms.

The answer to the question of which approach to take, native or hybrid, will be provided by examining some varying concerns; the size of a company's development team, the kind of services being deployed, and the preferred development time.

Some mobile applications are just a variation of the frontend application, built to take advantage of hardware unique to mobile devices. These kinds of mobile applications usually have expanded functionality like bio-metric authentication, using fingerprint and iris scanning, or geolocation and geotagging using GPS. Then, there are applications built to target mobile platforms from the start. These kind of applications might get dumbed-down web versions later down the line.

## Conclusion

For new developers just starting out who are wondering what all this is about, understanding what these specializations comprise of and how they each tie-in together can help to inform on what track(s) to choose.

So, how do the different software development specializations tie-in together? The answer is in the interactions of the server-side and client-side. The server-side serves as a _single source of truth_ for the various client-side applications. This means user data is the same across platforms. This also means any communications between client-side platforms is mediated by the backend. The backend is the glue that holds the pieces together. 
