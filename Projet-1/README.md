# Projet 1 - Cosmétiques de la Mer 🌊🧴

## Introduction & contexte
### Présentation du projet de data analyse 📈 :
L’entreprise Cosmétiques de la Mer est une marque de produits cosmétiques bio vendus en parapharmacie et en ligne sur leur propre site internet. L’entreprise nous a missionné pour analyser le comportement d’achat et la valeur dépensée par leurs consommateurs. 

### Contexte du projet dans l'entreprise :
L’entreprise a effectué une refonte de son site internet en septembre 2023. Cette refonte comprend des changements au niveau du design, de l’expérience utilisateur et du contenu proposé sur le site. 

### Objectifs du projet :
L’entreprise cherche à évaluer l’impact de cette refonte sur le comportement d’achat et la valeur des consommateurs sur le site. Elle souhaite mesurer comment les changements apportés au site ont influencé le comportement des visiteurs en termes d'achats, de navigation, de conversion. L'objectif est de déterminer si la refonte a été bénéfique en termes de résultats commerciaux et d'expérience utilisateur, et éventuellement d'identifier les aspects qui pourraient encore être améliorés. L’objectif a également été de segmenter les consommateurs du site en différentes typologies de clients. 

### Méthodologie utilisée :
Afin d’évaluer l’impact de la refonte du site internet, nous avons choisi de comparer les données sur deux périodes : de septembre 2023 à fin février 2024 vs l’année précédente. 
Nous avons tout d’abord effectué une overview des résultats sur ces deux périodes puis nous avons effectué une analyse RFM (Récence, Fréquence, Montant). Ces résultats nous ont permis de segmenter les consommateurs en différents groupes de clients et d’observer les différents comportements par typologies de clients et d’évaluer l’impact de la refonte sur chacune des typologies. 

## Méthodologie :

### Les étapes suivies pour mener l'analyse des données :
Tout d’abord, nous avons dû collecter les données, les nettoyer, les traiter, faire les jointures nécessaires via différents outils. 
Nous avons pu ensuite sortir des résultats sur les visiteurs du site internet sur les deux périodes et les comparer entre eux, puis en entonnoir, nous avons analysé les résultats des acheteurs du site internet sur les deux périodes. 
Nous avons ensuite à partir de différentes caractéristiques (Récence, Fréquence, Montant), utiliser la méthode du clustering afin de déterminer le nombre et les caractéristiques des différentes typologies de clients. Nous avons ensuite comparé les typologies entre elles, et évaluer l’impact de la refonte sur leur comportement et leur valeur.

### Collecte et préparation des données :
Nous avons collecté les données concernant les visiteurs du site en extrayant des tables via l’API Google Analytics 4 et Google Analytics 3 avec Python. Nous nous sommes ensuite concentrés sur les visiteurs devenus des acheteurs en extrayant les données sur Prestashop.
A partir de ces deux sources de données nous avons créé plusieurs tables que nous avons ensuite nettoyé, nous avons créé des colonnes de calculs et créé les jointures nécessaires sur Google Big Query avec SQL. 
Voici un aperçu de quelques tables créées :

Table visiteurs : date, nombre de visiteurs uniques, taux de rebond, transaction et un champ calculé taux de conversion.

Tables acheteurs : 
  -	Table paniers
  -	Table consommateurs
  -	Table commandes
  -	Table fréquence d’achat / réachat

### Analyse exploratoire des données :
Ensuite, nous avons voulu utiliser la méthode du clustering avec Python sur Google Colab. L’idée était de déterminer s’il existait plusieurs typologies de clients aux comportements différents. Nous avons utilisé la méthode Elbow et l’algorithme K-means. Il nous est ressorti 4 clusters différents que nous avons appelé :
-	Les clients VIP
-	Les très bons clients
-	Les bons clients
-	Les clients occasionnels
  
Nous avons ensuite créé une nouvelle table avec pour chaque cluster la fréquence d’achat moyenne, le montant ht moyen dépensé sur le site, le délai moyen entre deux commandes, le panier moyen, le pourcentage d’hommes et de femmes, l’âge moyen, le pourcentage de réachat. Nous avons sorti les données sur les deux périodes étudiées (septembre 2023 – février 2024 et septembre 2022 – février 2023) afin de les comparer ensemble. 

Une fois ces tables créées, nous avons pu les analyser sur Looker Studio. Nous avons dans un premier temps créé un tableau de bord à destination du client. Le tableau de bord se présente comme ceci :
-	Overview de l’audience (nombre de visiteurs, taux de conversion, taux de rebond, etc.)
-	Overview des acheteurs (chiffres d’affaires, nombre de commande, panier moyen, etc.)
-	Overview du comportement d’achat (fréquence d’achat, taux de réachat, type de paiement, taux de paniers abandonnés)
-	Overview informations démographiques (infos précédentes par genre)
-	Top produits (Top 5 en volume et en valeur)
-	Présentations des différents clusters
-	Une page par cluster présentant plusieurs KPIs importants (panier moyen, chiffres d’affaires moyen, taux de rachat, fréquence d’achat, délai moyen entre deux commandes, âge moyen) ainsi que le poids du cluster sur le total des acheteurs en valeur et en volume. Nous avons également fait apparaître l’évolution entre les deux périodes afin d’évaluer l’impact de la refonte sur les différents clusters. 

Nous avons ensuite présenté les résultats sur Canva lors des Demoday Le Wagon devant plus d’une centaine de personnes.

## Résultats :

### Principales conclusions de l'analyse des données :
Au global, on constate une baisse de la fréquentation du site mais un meilleur taux de conversion, c’est-à-dire que les visiteurs ont été plus nombreux à acheter. Le chiffre d’affaires a également baissé ainsi que le nombre de commandes. 

Nous avons répertorié 4 typologies de consommateurs : les clients VIP, les très bons clients, les bons clients et les clients occasionnels.

Pour les consommateurs occasionnels, qui représentent 2/3 des acheteurs, la refonte a eu un impact positif, en effet, tous les indicateurs sont à la hausse, le panier moyen et le chiffre d’affaires augmentent. En revanche, le délai entre deux commandes s’allonge, il faut donc pour cette catégorie accroître la fréquence des commandes.
Pour les bons clients, les données entre les deux périodes sont assez stables avec une légère baisse du panier moyen, tout comme les consommateurs occasionnels, le délai entre deux commandes s’allonge.
Pour les très bons clients les données sont assez stables entre les deux périodes.
Et pour les clients VIP, les résultats sont également positifs puisque la fréquence d’achat a augmenté ainsi que le chiffre d’affaires. 

Les résultats apportés répondent bien à la problématique et aux objectifs du projet. La demande de l’entreprise était d’avoir les caractéristiques des 4 typologies de clients et les évolutions entre les deux périodes avant et après refonte. 
 
## Limites rencontrées pendant l’analyse :

Les limites rencontrées pendant l’étude sont le fait de n’avoir eu que 2 semaines pour réaliser l’étude ce qui ne nous a pas permis d’aller creuser certains points plus en profondeur. 
Ensuite, le fait d’étudier deux périodes de 6 mois mais de ne pas avoir le scope d’une année entière ne permet pas de prendre en compte les effets de saisonnalité. En effet, Cosmétiques de la Mer vend énormément sur la période de l’été étant donné que leur top produits sont les produits solaires, or nous étudions la période septembre – février. 
Enfin, le fait de ne pas avoir pu échanger en direct avec l’entreprise pour comprendre certains résultats. 

## Conclusion & recommandations :

Au niveau du comportement d’achat, un nombre de visiteurs unique en baisse pouvant être expliqué par un moins bon référencement étant donné la refonte du site, mais un taux de conversion qui augmentent donc des consommateurs plus intéressés par l’achat de produits Cosmétiques de la Mer.
Au niveau des achats, des chiffres au global en baisse à la suite de la refonte portés principalement par un allongement du temps entre deux commandes, puisque l’on voit qu’un indicateur comme le panier moyen reste stable. 
Quatre typologies de consommateurs identifiés qui vont pouvoir aider l’entreprise à cibler ses campagnes. 

Voici les recommandations que nous avons formulé auprès du client en deux phases : 
-	Tout d’abord, faire évoluer les clients occasionnels en bons clients et les très bons clients en clients VIP. Cela passe par une augmentation de la fréquence d’achat et une augmentation du panier moyen. Pour cela nous préconisons des campagnes marketing ciblées (newsletters, promotion des nouveaux produits, suggestion de routine, etc.)
-	Ensuite, quand la part de bons clients et de VIP auront augmenté nous souhaitons les fidéliser. Pour cela, nous proposons un programme de fidélité qui peut se décomposer en plusieurs phases : cadeau offert à la première commande, système de point qui permet de gagner des cadeaux ou des codes promo.



