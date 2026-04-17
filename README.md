#mohammed-amine hmich readme 
README – LAB 18 : FireStorm
🎯 Objectif
Ce laboratoire consiste à récupérer un mot de passe caché dans une application Android.
Ce mot de passe permet de se connecter à une base de données Firebase et d’obtenir un flag (la solution du challenge).
Le mot de passe est généré par une fonction qui n’est jamais utilisée dans l’application normale. Il faut donc la forcer à s’exécuter.
________________________________________
🛠️ Ce que j’ai utilisé
•	Jadx : pour lire le code de l’application (reverse engineering)
•	Frida : pour exécuter la fonction cachée sans modifier l’application
•	Python : pour se connecter à Firebase et récupérer le flag
•	Pyrebase : une bibliothèque Python pour communiquer avec Firebase
 <img width="980" height="536" alt="image" src="https://github.com/user-attachments/assets/4194710f-b26e-400f-b02c-3d4ff133ef95" />

Lancemant d’umulateur : cd Mobile-Security-Framework-MobSF    
 adb install FireStorm.apk
 <img width="980" height="612" alt="image" src="https://github.com/user-attachments/assets/849f0439-b68e-4297-9aca-74303d16dc73" />

________________________________________
📋 Étapes réalisées
Ouverture de firestorm sur jadx 
 
 <img width="980" height="336" alt="image" src="https://github.com/user-attachments/assets/c6c83a12-6ec5-419b-a5fa-74b5b2c63bd6" />
<img width="980" height="152" alt="image" src="https://github.com/user-attachments/assets/c778a8cd-efa6-4ae3-b80d-a38cff706818" />

→ J’ai aussi trouvé les informations Firebase (clé API, projet, etc.) dans un fichier strings.xml.
Tourner Frida Server sur mon émulateur.
 <img width="980" height="499" alt="image" src="https://github.com/user-attachments/assets/5aa423e1-a9ed-41c2-88b3-fe5414f322d3" />

1.	ADB détecte l’émulateur.
2.	Tu passes en root.
3.	Tu échoues à pousser un fichier qui n’existe pas.
4.	Tu finis par pousser le bon fichier : frida-server.1-android-x86_64.
5.	Tu le rends exécutable.
6.	Tu le lances en arrière plan.
Donc Frida Server tourne maintenant sur ton émulateur.

1.	Exécution forcée de la fonction avec Frida
→ J’ai écrit un petit script Frida qui appelle la fonction cachée.
 
<img width="980" height="577" alt="image" src="https://github.com/user-attachments/assets/b8987674-e8ee-460a-b219-b4e88310b006" />

→ Le script m’a affiché le mot de passe généré.
 
<img width="980" height="346" alt="image" src="https://github.com/user-attachments/assets/d0fec880-b9f4-48c1-9b72-c78e737d33d3" />

2.	Connexion à Firebase avec Python
→ J’ai utilisé le mot de passe trouvé pour m’authentifier sur Firebase.
→ Une fois connecté, j’ai récupéré le flag.
 <img width="980" height="496" alt="image" src="https://github.com/user-attachments/assets/43d07065-c51e-434b-bb20-87a25a6dd06c" />

________________________________________
🧠 Ce que j’ai appris
•	Comment analyser une application Android sans l’exécuter
•	Comment exécuter du code caché avec Frida
•	Comment interagir avec Firebase depuis l’extérieur
•	Qu’une fonction inutilisée peut être une faille de sécurité
________________________________________
⚠️ Difficultés rencontrées
•	Pyrebase n’était pas installé → je l’ai installé avec la commande pip install pyrebase4
•	J’ai tapé import dans PowerShell pip install pyrebae4→ ce n’est pas possible, il faut taper python d’abord pour entrer dans l’environnement Python
 <img width="980" height="398" alt="image" src="https://github.com/user-attachments/assets/af2766b3-32d6-4595-b797-7fa2bcb892fc" />

________________________________________
🏁 Résultat final
PWNSEC{C0ngr4ts_Th4t_w45_4N_345y_P4$$w0rd_t0_G3t!!!_0R_!5_!t???}
<img width="1186" height="159" alt="image" src="https://github.com/user-attachments/assets/e0cde784-d581-40f1-9e48-1c078ff714f3" />
