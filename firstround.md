## Linux
1. I have evidence of recurring execution of a job but couldn't find the corresponding cron.  
   * how do we pull with certainty all cron jobs on a system ?  
   * what of a scenario with remote scheduled cron ?  
   * Think of some users that are service accounts with home directory not in /home  
   * Think of checking the logs of the cron system (not present by default on ubuntu systems ?) 
   * **solution in my case**:
     * journalctl --since="20220602 20:00" et un search de cron --> montre assez bien les infos, commandes et meme des paths de fichiers contenant des pass
 
2. example of asynchronous vs synchronous process under LInux  
   le process de boot Linux apres letape du kernel load, lorsque ca deorule les services en train detre démarrés:  
   sil y en a un qui plante, le systeme lattend avant de poursuivre  
   sous Ubuntu, en plus, ya pas de limite au temps dattente / sous rhel: 3 min.
   *Existe-t-il un moyen de skip - que c e soit en realtime ou par config en avance - ?*
   
3. exemple de commande utilisant un dictionnaire: locate  
   * contrairement a find
   * justement il ya une base de données à initialiser avant dutiliser la commande  

4. la commande awk permet de calculer  
   * Oui ca on le savait déjà
   * mais ce qui me frappe est que il extrait lui meme le digit d'un field alphanumerique  
   * exemple concret: je cheche a sommer la taille de certain fichiers dans le cadre dun cleanup systeme  
     `du -sh * | grep G | awk 'BEGIN{sum=0} {sum+=$1} END{print sum}` 
     
5. un souci avec des sites en https  
   * g récemment renouvellé des certif dun site exposé par apache2 sous ubuntu
   * evidemment jai pris soin de mettre les fichiers cert a la place qui etait pointée dans la conf sous sites-enabled  
   * je me rends compte que en réalité les certifs que jai mis ne correspondaient pas (niveau date et serial number)  
     et dans mon cas specifique, il savere quil montrait autre choses carrement: que le site netait pas valide depuis une centaine de jours  
   * en fait, il faut distinguer pour le meme site, lacces via le reseau interne et lacces depuis lexterieur   
   * pourquoi ca se manifeste now ? c parceque apparemment Chrome et certains utilitaires tolerent 117 jours apres lexpiration dun certif  
     `date -d "now -117 days" == 06/02/2022` --> date qui aparait en externe sur le certif invalide    
   * au final je soupconne quil ya ce certif pourri sur le F5 ou le Oalto  
   * NB: vu que tomcat tournait egalement sur le meme serveur, je me suis demandé si Java netait pas mêlé au souci TLS  
     * voici comment jai procédé
     * check du log catalina pour voir sil ya des erreurs SSL
     * jen ai pas trouvé: netstat -atulpen | grep LISTEN --> seul Apache ecoute sur un port "https related"  
     * ca ma rassuré sur le fait que Java netait pas impliqué, sinon: on peut toujours fouiller dans les keystores (avec tout ce qui est cacerts)  


 6. creer 2 microservices en Flask, sur le meme host, avec un appelant lautre (API) avec la methode request 
    mettre un proxy sur le host ...

 7. un cache avec ssh lorske plusieurs clés de déploiement sont utilisées avec git ??

 8. setup du proxy lorske pour git on utilise git protocol et non https (exemple dnas le cas dun push)
 9. try not to EXPOSE a port in Dockerfile ... the http call will connect ..but returns nothing
    
     
