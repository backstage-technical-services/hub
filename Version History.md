# Version History

### 2.x

Version 2 was built by Colin Paxton and later maintained by Lee Stone.
It was written in PHP and used a MySQL database ue to the limitations of
hosting the site on the university's "personal home page" server. This
site was well used by the membership and was continually improved by Lee
and other interested members.

### 3.x

While Version 3 was never released it did exist in various stages of
planning. This would use the same structure and hosting as Version 2 but
would introduce several new features.

### 4.x

Due to its age Version 2 made use of numerous outdated or deprecated
features and the process of continuous improvement had produced a file
structure that was very difficult to manage and keep updated. The site
also mixed HTML and PHP making updating the style difficult.

Version 4.0 did not introduce much additional functionality; instead it
involved a re-write of Version 2 from the ground up, using a framework
to promote modularity and aid with future development. This also enabled
the creation of a responsive and "modern" design.

Version 4 also led the move of the server to a VPS, full use of the
Backstage domain ([bts-crew.com][domain]) and the use of git and GitHub to
manage version control.

This development is led by [Ben Jones][github-bnjns] and is built on PHP 7,
MySQL 5.6 and Laravel 6.0 and utilises Bootstrap 3.

### 5.x

Although it used many modernisations and the use of MVC successfully
decoupled the application logic from the presentation layer, the general
organisation of projects made with Laravel made the application
difficult to maintain as its size and complexity grew. Coupled with the
lead developer moving languages and frameworks for their career, this
meant that development ground to a halt.

After a period [collecting feedback][v5-rfc] it was agreed to move to a
separate API, for the business logic, and SPA, for the presentation layer.

The API is built in Kotlin and uses the Quarkus framework, backed by
Keycloak for authorisation and authentication and a PostgreSQL database.

The SPA is built in TypeScript and uses the Vue.js framework, using
Bootstrap 4.

Version 5 will also make use of Docker images for deployment.

[domain]: https://www.bts-crew.com
[github-bnjns]: https://github.com/bnjns
[v5-rfc]: https://github.com/backstage-technical-services/hub/issues/112
