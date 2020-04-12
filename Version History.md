# Version History

### 2.x
Version 2 was built by Colin Paxton and later maintained by Lee Stone. It was written in PHP and used a MySQL database 
ue to the limitations of hosting the site on the university's "personal home page" server. This site was well used by 
the membership and was continually improved by Lee and other interested members.

### 3.x
While Version 3 was never released it did exist in various stages of planning. This would use the same structure and 
hosting as Version 2 but would introduce several new features.

### 4.x
Due to its age Version 2 made use of numerous outdated or deprecated features and the process of continuous improvement 
had produced a file structure that was very difficult to manage and keep updated. The site also mixed HTML and PHP 
making updating the style difficult.

Version 4.0 did not introduce much additional functionality; instead it involved a re-write of Version 2 from the ground 
up, using a framework to promote modularity and aid with future development. This also enabled the creation of a 
responsive and "modern" design.

Version 4 also led the move of the server to a VPS, full use of the Backstage domain ([bts-crew.com](http://www.bts-crew.com)) 
and the use of git and GitLab to manage version control.

This development is led by [Ben Jones](http://github.com/bnjns) and is built on PHP 7, MySQL 5.6 and Laravel 6.0 and 
utilises Bootstrap 3.

### 5.x

Being developed as a Proof of Concept, version 5 aims to further improve the maintainability of the code-base, and 
modernise the tech stack.

Version 5 will move away from a Multi-Page Application and will instead utilise an Application Programming Interface (API) 
built with Kotlin and Quarkus, with a separate front-end Single-Page Application (SPA) built with Vue.js and TypeScript. 

Deployment of both the API and SPA will utilise Docker images.
