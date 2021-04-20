---
title: Verwenden von Best Practices für SPA Seiten beim Senden von Daten an AAM
description: In diesem Dokument beschreiben wir einige Best Practices, die Sie befolgen sollten und die Sie kennen sollten, wenn Sie Daten von Einzelseitenanwendungen (SPA) an Adobe Audience Manager (AAM) senden. Dieses Dokument konzentriert sich auf die Verwendung von Launch by Adobe, der empfohlenen Implementierungsmethode.
feature: Implementation Basics
topics: spa
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1390
topic: SPA
role: "Developer, Data Engineer"
level: Experienced
translation-type: tm+mt
source-git-commit: a7dc335e75697a7b1720eccdadbb9605fdeda798
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---


# Verwenden von Best Practices auf SPA Seiten beim Senden von Daten an AAM {#using-best-practices-on-spa-pages-when-sending-data-to-aam}

In diesem Dokument beschreiben wir einige Best Practices, die Sie befolgen sollten und die Sie kennen sollten, wenn Sie Daten von [!UICONTROL Single Page Applications] (SPA) nach Adobe Audience Manager (AAM) senden. Dieses Dokument konzentriert sich auf die Verwendung von [!UICONTROL Experience Platform Launch], der empfohlenen Implementierungsmethode.

## Anfängliche Hinweise

* Die folgenden Elemente gehen davon aus, dass Sie [!DNL Platform Launch] zur Implementierung auf Ihrer Site verwenden. Wenn Sie [!DNL Platform Launch] nicht verwenden, müssen Sie diese jedoch an Ihre Implementierungsmethode anpassen.
* Alle SPA sind unterschiedlich, daher müssen Sie möglicherweise einige der folgenden Elemente anpassen, um Ihren Anforderungen am besten gerecht zu werden, aber wir wollten einige Best Practices mit Ihnen teilen. Dinge, über die Sie nachdenken müssen, wenn Sie Daten von SPA Seiten an Audience Manager senden.

## Einfaches Arbeitsdiagramm mit SPA und AAM in Experience Platform Launch {#simple-diagram-of-working-with-spas-and-aam-in-experience-platform-launch}

![spa in  [!DNL launch]](assets/spa_for_aam_in_launch.png)

>[!NOTE]
>Wie angegeben, ist dies ein vereinfachtes Diagramm, wie SPA Seiten in einer Adobe Audience Manager-Implementierung (ohne Adobe Analytics) mit [!DNL Platform Launch] verarbeitet werden. Wie Sie sehen können, ist es ziemlich unkompliziert, mit der großen Entscheidung, wie Sie eine Ansicht ändern (oder eine Aktion) zu [!DNL Platform Launch].

## Auslösen von [!DNL Launch] von der SPA Seite {#triggering-launch-from-the-spa-page}

Zwei der gängigeren Methoden zum Auslösen einer Regel in [!DNL Platform Launch] (und somit zum Senden von Daten an Audience Manager) sind:

* Festlegen benutzerdefinierter JavaScript-Ereignis (siehe Beispiel [HERE](https://helpx.adobe.com/analytics/kt/using/spa-analytics-best-practices-feature-video-use.html) mit Adobe Analytics)
* Verwenden eines [!UICONTROL Direct Call Rule]

In diesem Audience Manager verwenden wir ein [!UICONTROL Direct Call rule] in [!DNL Launch], um den Treffer in Audience Manager Trigger. Wie Sie in den nächsten Abschnitten sehen werden, ist dies wirklich nützlich, wenn Sie [!UICONTROL Data Layer] auf einen neuen Wert setzen, damit dieser von [!UICONTROL Data Element] in [!DNL Platform Launch] aufgenommen werden kann.

## Demo-Seite {#demo-page}

Wir haben eine kleine Demo-Seite erstellt, die zeigt, wie Sie einen Wert im [!DNL data layer] ändern und ihn an AAM senden, wie Sie es auf einer SPA Seite tun können. Diese Funktion kann für detailliertere Änderungen modelliert werden. Sie finden diese Demo-Seite [HIER](https://aam.enablementadobe.com/SPA-Launch.html).

## Durch Einstellung der [!DNL data layer] {#setting-the-data-layer}

Wie bereits erwähnt, muss beim Laden von neuen Inhalten auf der Seite oder beim Durchführen einer Aktion auf der Site das [!DNL data layer] dynamisch im Kopf der Seite eingestellt werden, BEVOR [!DNL Launch] aufgerufen wird und das [!UICONTROL rules] ausgeführt wird, damit [!DNL Platform Launch] die neuen Werte aus dem [!DNL data layer] abrufen und in den Audience Manager verschieben kann.

Wenn Sie die oben aufgeführte Demo-Site aufrufen und sich die Seitenquelle ansehen, sehen Sie:

* Das [!DNL data layer] befindet sich im Kopf der Seite vor dem Aufruf von [!DNL Platform Launch]
* Das JavaScript im simulierten SPA ändert den [!UICONTROL Data Layer]- und DANN den [!DNL Platform Launch]-Aufruf (der _satellite.track()-Aufruf). Wenn Sie benutzerdefinierte JavaScript-Ereignis anstelle von [!UICONTROL Direct Call Rule] verwenden, ist die Lektion die gleiche. Ändern Sie zuerst die [!DNL data layer] und rufen Sie dann [!DNL Launch] auf.

>[!VIDEO](https://video.tv.adobe.com/v/23322/?quality=12)

## Zusätzliche Ressourcen {#additional-resources}

* [SPA über die Adobe](https://forums.adobe.com/thread/2451022)
* [Referenzarchitektur-Sites, die zeigen, wie SPA in Launch by Adobe implementiert werden](https://helpx.adobe.com/experience-manager/kt/integration/using/launch-reference-architecture-SPA-tutorial-implement.html)
* [Bewährte Verfahren bei der Verfolgung von SPA in Adobe Analytics](https://helpx.adobe.com/analytics/kt/using/spa-analytics-best-practices-feature-video-use.html)
* [Demo-Site für diesen Artikel](https://aam.enablementadobe.com/SPA-Launch.html)
