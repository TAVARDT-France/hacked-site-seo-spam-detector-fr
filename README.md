<p align="center">
  <a href="https://ag.tavardt.com/fr/">
    <img src="https://ag.tavardt.com/img/tavardt-banner.png" alt="TAVARDT" width="1024" />
  </a>
</p>

# Détecteur de Sites Piratés et Spam SEO

[![Detecteur Spam SEO](https://img.shields.io/badge/TAVARDT-Antispam%20SEO-5b3cf5.svg)](https://tools.tavardt.com/fr/detecteur-spam-seo-site-pirate/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

Le **TAVARDT Détecteur de Sites Piratés et Spam SEO** assure l'inspection médico-légale des applications web afin de détecter le cloaking à destination des moteurs, les injections masquées de liens pharmaceutiques ou de casino, les iframes non autorisées et les charges utiles obscurcies en France.

***

## Architecture de Détection et Matrice Forensique des Vecteurs

Le cloaking et les injections de liens cachés trompent les robots d'indexation tout en restant invisibles aux yeux des visiteurs. Cette compromission entraîne un déclassement immédiat sur Google, l'exclusion de l'index et une dégradation durable de l'autorité de domaine.

Cet outil diagnostique compare les divergences de contenu entre User-Agents, audite les conteneurs CSS dissimulés et isole les vecteurs malveillants sans aucune dépendance logicielle externe.

Le moteur d'analyse évalue l'intégrité du DOM, les variations de volume des réponses et les signatures de scripts suspects à partir d'un score de base de 100 points :

<table>
  <thead>
    <tr>
      <th>Vecteur de Compromission</th><th>Logique de Détection</th><th>Déduction</th><th>Impact sur l'Intégrité</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Cloaking Différentiel</strong></td><td>Compare le User-Agent standard avec le Googlebot officiel. Détecté si le ratio de divergence en octets > 0,40 et le delta absolu > 1000 octets.</td><td>-30 pts</td><td>Risque critique de pénalité algorithmique et de désindexation sur les moteurs.</td>
    </tr>
    <tr>
      <td><strong>Injection de Spam Dissimulé</strong></td><td>Analyse les blocs stylisés avec <code>display:none</code>, <code>opacity:0</code> ou marges négatives contenant des termes de casino et médicaments.</td><td>-35 pts</td><td>Preuve irréfutable de compromission de base de données ou de fichiers templates.</td>
    </tr>
    <tr>
      <td><strong>iframes Invisibles Suspectes</strong></td><td>Repère les iframes de dimension nulle ou cachées ne figurant pas sur la liste blanche des tiers de sécurité agréés.</td><td>-20 pts</td><td>Vecteur potentiel de redirection frauduleuse, de drive-by download ou de vol d'identifiants.</td>
    </tr>
    <tr>
      <td><strong>Code Obscurci</strong></td><td>Identifie les motifs répétés d'exécution dynamique tels que <code>eval()</code>, <code>unescape()</code> et <code>base64_decode</code> (>2 occurrences).</td><td>-15 pts</td><td>Comportement caractéristique des droppers et scripts de maintien d'accès malveillants.</td>
    </tr>
    <tr>
      <td><strong>Échec de Connexion</strong></td><td>Expiration du délai de requête ou échec de négociation TLS/HTTP.</td><td>-20 pts</td><td>Inaccessibilité de l'hôte empêchant la réalisation de l'audit forensique complet.</td>
    </tr>
  </tbody>
</table>

### Échelle d'Intégrité et Niveaux d'Alerte

L'utilitaire calcule un score global d'intégrité catégorisant la sécurité de l'application :

* <strong>85 à 100 (CLEAN)</strong> : Aucun indicateur de compromission détecté ; intégrité du DOM et cohérence des réponses vérifiées.
* <strong>60 à 84 (SUSPICIOUS)</strong> : Présence d'anomalies de mise en page CSS, iframes suspectes ou variations demandant un audit approfondi.
* <strong>0 à 59 (COMPROMISED)</strong> : Preuve avérée de cloaking, injection de spam ou scripts obscurcis exigeant une remédiation urgente.

***

## Installation et Exécution

Conçu exclusivement avec les modules standards de Python 3.8+ sans dépendances externes.

```bash
git clone https://github.com/TAVARDT-France/hacked-site-seo-spam-detector-fr.git
cd hacked-site-seo-spam-detector-fr
```

### Exécution Standard CLI

```bash
python seo_spam_detector.py exemple.fr
```

### Sortie Structurée pour Pipelines en JSON

```bash
python seo_spam_detector.py exemple.fr -j
```

### Configuration du Délai d'Attente

```bash
python seo_spam_detector.py exemple.fr -j -t 15
```

***

## Conformité ANSSI et Résilience des Applications Web

Cette suite diagnostique répond aux exigences de sécurité de l'**Agence nationale de la sécurité des systèmes d'information (ANSSI)** pour les applications web. Identifier rapidement les altérations de code non autorisées permet de préserver l'intégrité des données.

Les entreprises doivent intégrer des audits réguliers de cloaking et de détection de spam dans leurs processus de surveillance pour maintenir la confiance numérique.

***

## Questions Fréquentes Techniques

### Comment fonctionne l'algorithme de détection de cloaking différentiel ?

L'outil émet deux requêtes HTTP successives vers le domaine cible, l'une avec le User-Agent d'un navigateur moderne et l'autre simulant le Googlebot. Si l'écart relatif en octets dépasse 0,40 et que la différence absolue surpasse 1000 octets, l'anomalie de cloaking est signalée avec une déduction de 30 points.

### Quels critères qualifient une iframe invisible de suspecte ?

Toute balise iframe configurée avec une largeur nulle, une hauteur nulle ou un style <code>display:none</code> qui n'émane pas d'un service de confiance répertorié (comme Cloudflare, Google reCAPTCHA, Google Tag Manager ou hCaptcha) est jugée suspecte et pénalisée de 20 points.

### Quels termes de spam sont ciblés dans les blocs CSS masqués ?

Le scanner ausculte les conteneurs rendus invisibles via <code>display:none</code>, <code>visibility:hidden</code>, <code>opacity:0</code> ou coordonnées hors écran pour localiser des termes tels que viagra, cialis, casino, payday loan, replica watch, poker, roulette, baccarat, vape et ketamine, infligeant 35 points de pénalité.

### Pourquoi les fonctions eval et unescape sont-elles sanctionnées ?

Dans un environnement applicatif propre, l'usage d'<code>eval()</code> ou <code>unescape()</code> est prohibé. Plus de deux occurrences de ces fonctions suggèrent l'exécution dynamique de charges malveillantes injectées, entraînant une déduction de 15 points.

### Comment intégrer les résultats dans des plateformes de supervision ?

L'exécution du script avec le paramètre court <code>-j</code> produit une sortie JSON structurée directement sur stdout, prête à être ingérée par des tableaux de bord SIEM ou des pipelines CI/CD.

***

## Réponse aux Incidents et Désinfection Web

Pour un assainissement post-piratage et une mise en conformité avec les exigences Recommandations ANSSI et Intégrité Web, contactez **TAVARDT**.

***

## Liens Utiles

* **Portail Institutionnel:** https://ag.tavardt.com/fr/
* **Suite de Diagnostic:** https://tools.tavardt.com/fr/
* **Contact Technique:** https://ag.tavardt.com/fr/contact/

***

### Licence
Distribué sous la licence MIT.

***

© 2026 TAVARDT. Tous droits réservés.
