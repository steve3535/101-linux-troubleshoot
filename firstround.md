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


