# SPA vs. MPA
SPA stands for single-page application. As the name implies, it is less of a website and more of a web application that lives entirely on one page. Instead of making calls to a server to re-render the page, different parts of the page are selectively re-rendered, making it seem like nothing is loading or refreshing at all.

MPA stands for multi-page application but pretty much just refers to a normal website. The server renders different pages for different URLs and every new page and its assets must be loaded in by the browser.

## Pros and Cons of SPA
SPAs are useful when you want a webpage with a lot of functionality, like an app. If a lot of components are reused, a SPA is incredibly useful since it can selectively re-render only what needs to change. SPAs can be much quicker can MPAs because there is only one initial load and then everything is already in the browser.

SPAs are less useful when you are looking to make a more static website because they can complicate what should be a simple task. If lots of different pages are needed, SPAs can further bog down the process. Since there is only one actual HTML page, the back button can often break a SPA website unless precautions have been taken. This lack of HTML files also weakens SPAs for search engine optimization, and the initial load can potentially take a very long time since everything must be loaded at once.

## Pros and Cons of MPA
MPAs are useful when you need to make a website with a lot of different pages and you don't need to micromanage a lot of your functionality. They are generally easier to make since there is less Javascript involved and they do well with SEO, accessibility, and the back button will actually do what it is supposed to do.

MPAs can have annoying load times if each page must load separately, and there is less ability to make an application out of an MPA.

## Structure of SPA vs MPA
An SPA is based around a client-side framework like Vue or Angular, meaning it uses a lot of Javascript. These frameworks have a view library to create UI components, and to simulate different pages, there is typically a router library. A state management library can be used as a data store for the web app. With all of this, an SPA can function entirely on the client, with no need for a server. A server is only needed if the app needs to interact with a custom database; for this, the server implements a RESTful API only.

An MPA is typically (not not always) based around a server-side framework like Laravel or Django and follows the MVC design architecture. The server-side language is used to return different HTML pages (which contain their own CSS/JS if necessary) based on the URL and communicates with a database for the website. All of the rendering of pages is pretty much done by the server.

### Summary
**SPA**
- Frontend: Javascript framework (views, routes, states)
- Backend: RESTful API server
- Database

**MPA**
- Frontend: HTML, CSS, and Javascript
- Backend: MVC framework
- Database

### Examples of SPA and MPA projects
**MERN (SPA)**
- Frontend: React.js, react-router, Redux
- Backend: Node.js + Express.js
- Database: MongoDB

**FMAP (SPA)**
- Frontend: Angular
- Backend: Python + Flask
- Database: MariaDB

**LAMP (MPA)**
- Frontend: HTML/CSS/JS
- Backend: Apache web server + PHP
- Database: MySQL

**Ruby on Rails (MPA)**
- Frontend: HTML/CSS/JS
- Backend: Ruby + Rails
- Database: PostgreSQL