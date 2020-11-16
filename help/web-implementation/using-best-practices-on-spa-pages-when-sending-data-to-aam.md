---
title: Verwenden von Best Practices für SPA Seiten beim Senden von Daten an AAM
description: In diesem Dokument beschreiben wir einige Best Practices, die Sie befolgen sollten und die Sie kennen sollten, wenn Sie Daten von Einzelseitenanwendungen (SPA) an Adobe Audience Manager (AAM) senden. Dieses Dokument konzentriert sich auf die Verwendung von Launch by Adobe, der empfohlenen Implementierungsmethode.
feature: implementation basics
topics: spa
audience: implementer
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1390
translation-type: tm+mt
source-git-commit: a108c51fdad66f4e7974eb96609b6d8f058cb6ff
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 0%

---


# Verwenden von Best Practices für SPA Seiten beim Senden von Daten an AAM {#using-best-practices-on-spa-pages-when-sending-data-to-aam}

In diesem Dokument beschreiben wir einige Best Practices, die Sie befolgen sollten und die Sie kennen sollten, wenn Sie Daten von [!UICONTROL Single Page Applications] (SPA) nach Adobe Audience Manager (AAM) senden. Dieses Dokument konzentriert sich auf die Verwendung [!UICONTROL Experience Platform Launch](die empfohlene Implementierungsmethode).

## Anfängliche Hinweise

* Die folgenden Elemente gehen davon aus, dass Sie [!DNL Platform Launch] zur Implementierung auf Ihrer Site verwenden. Die Überlegungen bestehen weiterhin, wenn Sie nicht verwenden [!DNL Platform Launch], müssen sie jedoch an Ihre Implementierungsmethode anpassen.
* Alle SPA sind unterschiedlich, daher müssen Sie möglicherweise einige der folgenden Elemente anpassen, um Ihren Anforderungen am besten gerecht zu werden, aber wir wollten einige Best Practices mit Ihnen teilen. Dinge, über die Sie nachdenken müssen, wenn Sie Daten von SPA Seiten an Audience Manager senden.

## Einfaches Arbeitsdiagramm mit SPA und AAM im Experience Platform Launch {#simple-diagram-of-working-with-spas-and-aam-in-experience-platform-launch}

![spa in [!DNL launch]](assets/spa_for_aam_in_launch.png)

>[!NOTE]
>Wie angegeben, ist dies ein vereinfachtes Diagramm, wie SPA Seiten in einer Adobe Audience Manager-Implementierung (ohne Adobe Analytics) verarbeitet werden [!DNL Platform Launch]. Wie Sie sehen können, ist es ziemlich unkompliziert, mit der großen Entscheidung, wie Sie eine Ansicht ändern (oder eine Aktion) zu [!DNL Platform Launch]kommunizieren.

## Auslösen [!DNL Launch] von der SPA {#triggering-launch-from-the-spa-page}

Zwei der gängigeren Methoden zum Auslösen einer Regel in [!DNL Platform Launch] (und somit zum Senden von Daten an Audience Manager) sind:

* Festlegen benutzerdefinierter JavaScript-Ereignis (siehe Beispiel [HIER](https://helpx.adobe.com/analytics/kt/using/spa-analytics-best-practices-feature-video-use.html) mit Adobe Analytics)
* Verwenden einer [!UICONTROL Direct Call Rule]

In diesem Audience Manager-Beispiel werden wir eine verwenden, [!UICONTROL Direct Call rule] [!DNL Launch] um den Treffer auszulösen, der in den Audience Manager gelangt. Wie Sie in den nächsten Abschnitten sehen werden, ist dies wirklich nützlich, wenn Sie den Wert [!UICONTROL Data Layer] auf einen neuen Wert einstellen, damit er vom [!UICONTROL Data Element] in aufgenommen werden kann [!DNL Platform Launch].

## Demoseite {#demo-page}

Wir haben eine kleine Demo-Seite erstellt, die zeigt, wie Sie einen Wert in der ändern [!DNL data layer] und ihn an AAM senden, wie Sie es auf einer SPA Seite tun können. Diese Funktion kann für detailliertere Änderungen modelliert werden. Diese Demo-Seite finden Sie [HIER](https://aam.enablementadobe.com/SPA-Launch.html).

## Durch Einstellung der [!DNL data layer] {#setting-the-data-layer}

Wie bereits erwähnt, müssen neue Inhalte, die auf der Seite geladen werden, oder wenn jemand eine Aktion auf der Site ausführt, dynamisch im Kopf der Seite eingestellt werden, BEVOR der Aufruf und die Ausführung des Vorgangs [!DNL data layer] erfolgt [!DNL Launch] , damit die neuen Werte aus der Seite aufgenommen werden [!UICONTROL rules]können [!DNL Platform Launch] [!DNL data layer] und in den Audience Manager verschoben werden können.

Wenn Sie die oben aufgeführte Demo-Site aufrufen und sich die Seitenquelle ansehen, sehen Sie:

* Der Aufruf [!DNL data layer] befindet sich im Kopf der Seite, bevor der Aufruf von [!DNL Platform Launch]
* Das JavaScript im simulierten SPA-Link ändert den [!UICONTROL Data Layer]und der DANN-Aufruf [!DNL Platform Launch] (der Aufruf _satellite.track()). Wenn Sie benutzerdefinierte JavaScript-Ereignis anstelle dieser verwenden, [!UICONTROL Direct Call Rule]ist die Lektion die gleiche. Ändern Sie zuerst die [!DNL data layer]und rufen Sie dann an [!DNL Launch].

>[!VIDEO](https://video.tv.adobe.com/v/23322/?quality=12)

## Zusätzliche Ressourcen {#additional-resources}

* [SPA über die Adobe](https://forums.adobe.com/thread/2451022)
* [Referenzarchitektur-Sites, die zeigen, wie SPA in Launch by Adobe implementiert werden](https://helpx.adobe.com/experience-manager/kt/integration/using/launch-reference-architecture-SPA-tutorial-implement.html)
* [Bewährte Verfahren bei der Verfolgung von SPA in Adobe Analytics](https://helpx.adobe.com/analytics/kt/using/spa-analytics-best-practices-feature-video-use.html)
* [Demo-Site für diesen Artikel](https://aam.enablementadobe.com/SPA-Launch.html)
