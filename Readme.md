# Remote meetings planning

This project is used in a course on the *ops* part at the [University of Rennes](https://www.univ-rennes1.fr/), France. It is a kind of doodle clone developed in so-called "native cloud" technologies in order to allow students to work on a continuous deployment chain in a containerized environment. Among the feature, the application automatically initializes a pad for the meeting and a chat room for the meeting participants.

- The [back](https://github.com/barais/doodlestudent/tree/main/api) is developed using the [quarkus.io](https://quarkus.io/) framework. 
- The [front](https://github.com/barais/doodlestudent/tree/main/front) is developed in [angular](https://angular.io/) using the [primeng](https://www.primefaces.org/primeng/)  angular UI component library and the [fullcalendar](https://fullcalendar.io/) graphical component.

A demo of the application is available [here](https://doodle.diverse-team.fr/).

Three videos (in french) are available. They present:
- the [main application feature](https://drive.google.com/file/d/1GQbdgq2CHcddTlcoHqM5Zc8Dw5o_eeLg/preview), 
- its [architecture](https://drive.google.com/file/d/1l5UAsU5_q-oshwEW6edZ4UvQjN3-tzwi/preview) 
- and a [short code review](https://drive.google.com/file/d/1jxYNfJdtd4r_pDbOthra360ei8Z17tX_/preview) .

For french native speaker that wants to follow the course. The course web page is available [here](https://hackmd.diverse-team.fr/s/SJqu5DjSD).

# Schema explicatif

![schema](https://github.com/kimohmd/images/blob/master/tlcSchema.png?raw=true)

L'application est constitué de 6 services, chacun tourne dans un docker container:

- Base de données Mysql : container db à partir de l'image mysql
- Serveur de mail : container mail à partir de l'image bytemark/smtp 
- Backend quarkus: container doodleback à partir de l'image construite du Dockerfile se trouvant dans ./api
- Pad : conainer etherpad à partir de l'image etherpad/etherpad:stable
- phpmyadmin : container myadmin à partir de l'image phpmyadmin 
- Frontend angular : container doodlefront à partir de l'image construite du Dockerfile se trouvant dans ./front/  (à partir de l'image bunkerity/bunkerized-nginx)

accessible en http sur ahammad.diverse-team.fr à défaut d'une erreur lors de la tentative de bunkerized nginx d'installer les certificat letsencrypt (donc pas de connexion sécurisée en https).

les services : phpmyadmin et le pad ne sont pas accessible car sous-domaines non ajoutés, cependant la configuration a bien été mise en place dans le fichier ./server-confs/api.conf  

##### REMARQUE
seules les questions 1 --> 4 ont été faites
