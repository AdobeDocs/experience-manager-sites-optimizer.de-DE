---
solution: Experience Manager
product: adobe experience manager
type: Documentation
description: Dokumentation zu AEM Sites Optimizer.
index: y
git-repo: https://github.com/AdobeDocs/experience-manager-sites-optimizer.de-DE
feature-set: Experience Manager Assets,Experience Manager Sites,Experience Manager, Experience Manager Forms, Experience Manager Cloud Manager
cloud: Experience Cloud
recommendations: noDisplay
source-git-commit: 2f4ef1c6f44d602bfe365a52eb692fe7faa7f05f
workflow-type: tm+mt
source-wordcount: '79'
ht-degree: 29%

---


# Metadaten für die interne Verwendung

Das GitHub-Authoring-System organisiert Metadaten hierarchisch und nutzt dabei die folgenden, sich ständig weiterentwickelnden Präzedenzfälle.

1. metadata.md
1. IHV
1. Artikel

Die in der Datei „metadata.md“ definierten Metadaten gelten für das gesamte Repository, können jedoch auf Inhaltsverzeichnis- und Artikelebene überschrieben werden. Das Überschreiben der Metadaten sollte auf der niedrigstmöglichen Ebene erfolgen.

Die Metadaten im `experience-manager-cloud-service.en`-Repository sind das erforderliche Minimum.

metadata.md

* `product`
* `git-repo`
* `index`
* `solution-title`
* `solution-hub-url`
* `getting-started-title`
* `getting-started-url`
* `tutorials-title`
* `tutorials-url`

IHVs

* `sub-product`
* `user-guide-title`

Artikel

* `title`
* `description`
* `contentOwner` (nur auf Asset-Kerninhalte unter `/help/assets`)

