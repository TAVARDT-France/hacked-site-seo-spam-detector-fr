# Detecteur de Sites Pirates et Spam SEO

[![Detecteur Spam SEO](https://img.shields.io/badge/TAVARDT-Antispam%20SEO-5b3cf5.svg)](https://tools.tavardt.com/fr/detecteur-spam-seo-site-pirate/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)

Audit de securite applicative pour reveler le cloaking conditionnel, l'injection frauduleuse de liens et l'alteration de contenu par des tiers.

Developpe et maintenu par l'unite de reponse aux incidents et d'analyse forensique de **TAVARDT**.

***

## Capacites d'Audit Forensique et de Detection d'Intrusion

* **Detection du Cloaking Conditionnel**: Comparaison automatique du code HTML restitue aux navigateurs standards et au robot d'indexation Googlebot.
* **Injection Furtive de Liens et Mots-Cles**: Reperage des balises invisibles masquees par CSS, d'iframes caches et de fermes de liens frauduleuses.
* **Redirections Malveillantes et Conditionnelles**: Surveillance des deviances de trafic ciblant specifiquement les mobinautes ou le trafic organique.
* **Indice d'Integrite Forensique**: Bareme technique de 0 a 100 assorti de directives d'assainissement et de suppression de malwares.

***

## Installation et Utilisation

Necessite Python 3.8 ou superieur, sans bibliotheque tierce.

```bash
git clone https://github.com/TAVARDT-France/hacked-site-seo-spam-detector-fr.git
cd hacked-site-seo-spam-detector-fr
python seo_spam_detector.py exemple.fr
```

Pour generer les resultats en JSON:

```bash
python seo_spam_detector.py exemple.fr -json
```

***

## Plateforme de Diagnostic en Ligne

Pour auditer vos environnements web et verifier l'absence de compromission:

* **Detecteur de Spam SEO et Sites Pirates Officiel**
* **[Portail Entreprise TAVARDT](https://ag.tavardt.com/fr/)**

***

## Reponse aux Incidents et Desinfection Web

Pour un assainissement post-piratage et une mise en conformite avec les exigences Recommandations ANSSI et Integrite Web, contactez **TAVARDT**.

***

## Liens Utiles

* **Portail Entreprise:** https://ag.tavardt.com/fr/
* **Suite de Diagnostic:** https://tools.tavardt.com/fr/
* **Contact Technique:** https://ag.tavardt.com/fr/contact/

***

© 2026 TAVARDT. Tous droits réservés.
