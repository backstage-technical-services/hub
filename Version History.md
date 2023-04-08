# Version History

**Current version:** [v4.x](#4x)

### 2.x

Version 2 was built by Colin Paxton and later maintained by Lee Stone. It was written in PHP and used a MySQL database
ue to the limitations of hosting the site on the university's "personal home page" server. This site was well used by
the membership and was continually improved by Lee and other interested members.

### 3.x

While Version 3 was never released it did exist in various stages of planning. This would use the same structure and
hosting as Version 2 but would introduce several new features.

### 4.x

Due to its age Version 2 made use of numerous outdated or deprecated features, and the process of continuous improvement
had produced a file structure that was very difficult to manage and keep updated. The site also mixed HTML and PHP
making updating the style difficult.

Version 4.0 did not introduce much additional functionality; instead it involved a re-write of Version 2 from the ground
up, using a framework to promote modularity and aid with future development. This also enabled the creation of a
responsive and "modern" design.

Version 4 also led the move of the server to a VPS, full use of the Backstage domain ([bts-crew.com][domain]) and the
use of git and GitHub to manage version control.

This development is led by [Ben Jones][github-bnjns] and is built on PHP 7, MySQL 5.6 and Laravel and utilises Bootstrap
3.

### 5.x

Despite the modernisations and decoupling of application logic from the presentation layer, the general organisation of
the Laravel framework made the application difficult to maintain as its size and complexity grew.

As the lead developer also changed language and framework for their career, development on the site became increasingly
more difficult and quickly became sporadic, leading many to believe that development had stopped.

After a period [collecting feedback][v5-rfc] it was agreed to move the site to a separate API (to handle the business
logic) and SPA (to handle the presentation layer), using languages and frameworks the lead developer was more familiar
with. The API is built in Kotlin and uses the Quarkus framework, backed by Keycloak for authorisation and authentication
and a PostgreSQL database. The SPA is built in TypeScript and uses the Vue.js framework, using Bootstrap 4.

Version 5 also uses of Docker images for to simplify the deployment process, and will likely move hosting to Bath SU on-premises servers.

> **Note:** We aim to move to v5 in the long term; for now we will still be developing on v4.

[domain]: https://www.bts-crew.com
[github-bnjns]: https://github.com/bnjns
[v5-rfc]: https://github.com/backstage-technical-services/hub/issues/112
