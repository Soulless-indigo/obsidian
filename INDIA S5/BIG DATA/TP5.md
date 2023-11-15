
Cet exercice couvre plusieurs aspects fondamentaux de l'utilisation de Hadoop, HDFS (Hadoop Distributed File System), et MapReduce. Voici un résumé de chaque étape, expliquant ce qu'elle implique :

1. **Lister le contenu de la racine HDFS :**
   - Utilisation de `hadoop fs -ls /` ou `hdfs dfs -ls /` pour lister les fichiers et répertoires dans la racine du HDFS.

2. **Créer un dossier sur la machine virtuelle HDFS :**
   - Utilisation de `hdfs dfs -mkdir /user/input` pour créer un nouveau dossier dans HDFS.

3. **Copier des fichiers du système de fichiers local vers HDFS :**
   - Utilisation de `hdfs dfs -copyFromLocal <local-path>\*.txt /user/input` pour copier des fichiers .txt depuis le système de fichiers local vers le dossier spécifié dans HDFS.

4. **Afficher le contenu du dossier HDFS :**
   - Utilisation de `hdfs dfs -ls /user/input` pour lister les fichiers dans le dossier `/user/input` du HDFS.

5. **Afficher le contenu d'un fichier spécifique :**
   - Utilisation de `hdfs dfs -cat /user/input/notice.txt` pour afficher le contenu du fichier `notice.txt`.

6. **Afficher la taille d'un fichier :**
   - Utilisation de `hdfs dfs -du /user/input/notice.txt` pour voir la taille du fichier `notice.txt`.

7. **Visualisation des fichiers via une interface web :**
   - Accès à `http://localhost:50070/explorer.html#/input` pour visualiser les fichiers dans le navigateur web.

8. **Récupérer la taille d'un bloc HDFS :**
   - Utilisation de `hdfs getconf -confKey dfs.blocksize` pour connaître la taille de bloc par défaut dans HDFS.

9. **Récupérer le facteur de réplication :**
   - Utilisation de `hdfs getconf -confKey dfs.replication` pour connaître le facteur de réplication par défaut.

10. **Utiliser `hdfs fsck` pour un rapport détaillé :**
    - Utilisation de `hdfs fsck /input` pour obtenir un rapport détaillé sur l'état des fichiers dans le dossier `/input` de HDFS, y compris le nombre de fichiers, blocs, blocs corrompus, le facteur de réplication par défaut, le nombre de data-nodes, et le nombre de racks.

11. **Modifier le facteur de réplication d'un fichier :**
    - Utilisation de `hadoop fs -setrep -w 2 /input/notice.txt` ou `hdfs dfs -setrep -w 2 /input/notice.txt` pour changer le facteur de réplication du fichier `notice.txt` à 2.

12. **Utiliser `hdfs fsck` pour un rapport après modification :**
    - Exécution de `hdfs fsck /user/input` pour un rapport détaillé sur le dossier `/user/input` après la modification du facteur de réplication.

13. **Compter le nombre total de mots avec MapReduce :**
    - Exécution d'une tâche MapReduce pour compter les mots dans les fichiers .txt du répertoire `/user/input`, en utilisant la commande `hadoop jar <Hadoop-Home>/share/hadoop/mapreduce/hadoop-mapreduce-examples-2.9.2.jar wordcount /user/input/*.txt /output`.

14. **Vérifier les résultats de MapReduce :**
    - Utilisation de `hadoop fs -ls /output` et `hadoop fs -cat /output/part-r-00000` pour lister et afficher les résultats du traitement MapReduce.

Cet exercice est un excellent moyen d'apprendre les bases de Hadoop, HDFS, et MapReduce, y compris la manipulation de fichiers dans HDFS, l'exécution de tâches MapReduce, et la compréhension des concepts clés comme la réplication et la taille des blocs.