# xss
explication d'une  attaque xss

Pour réaliser  l'attaque XSS par réflexion il suffit de laisser un lien qui aura pour paramètre le code
malveillant.

http://www.forum-vulnérable.com/recherche.php?parametre=<script>alert(‘attaque
XSS’)</script>
 Exemple de lien malveillant exploitant une faille XSS
En cliquant sur ce lien, la victime lancera la recherche. Puis le moteur de recherche affichera
le paramètre « <script>alert(‘attaque XSS’)</script> » qui sera exécuté par le navigateur.

 L'attaque XSS stockée injecte du code malveillant dans la base de données. 
exemple de code
<?php
//recuperation des parametres
$numsujet=$_GET['searchsujet'];
//generation de la requete
$requeteSQL = "SELECT * FROM messages WHERE numerosujet=$numsujet order by id";
//execution de la requete
$reponse = mysql_query($requeteSQL);
//affichage du resultat
echo "<tr><td> Sujet $numsujet</td><td>";
while($resultat = mysql_fetch_assoc($reponse)) {
 echo $resultat['redacteur'] . " : " . $resultat['message'] . "<br>";
}
echo "</td></tr>";
?>

Lorsque des utilisateurs afficheront le fil des messages, le message frauduleux sera
automatiquement envoyé aux navigateurs et interprété créant une attaque XSS.
