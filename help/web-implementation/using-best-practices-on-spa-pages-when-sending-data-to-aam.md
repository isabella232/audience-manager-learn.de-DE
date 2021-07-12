---
title: Verwenden von Best Practices für SPA Seiten beim Senden von Daten an AAM
description: In diesem Dokument werden wir verschiedene Best Practices beschreiben, die Sie befolgen und kennen sollten, wenn Sie Daten von Single Page Applications (SPA) an Adobe Audience Manager (AAM) senden. Dieses Dokument konzentriert sich auf die Verwendung von Launch by Adobe, der empfohlenen Implementierungsmethode.
feature: Implementierungsgrundlagen
topics: spa
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1390
topic: SPA
role: Developer, Data Engineer
level: Experienced
exl-id: 99ec723a-dd56-4355-a29f-bd6d2356b402
source-git-commit: 4b91696f840518312ec041abdbe5217178aee405
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# Verwenden von Best Practices für SPA Seiten beim Senden von Daten an AAM {#using-best-practices-on-spa-pages-when-sending-data-to-aam}

In diesem Dokument werden wir verschiedene Best Practices beschreiben, die Sie befolgen und kennen sollten, wenn Sie Daten von [!UICONTROL Single Page Applications] (SPA) an Adobe Audience Manager (AAM) senden. Dieses Dokument konzentriert sich auf die Verwendung von [!UICONTROL Experience Platform Launch], der empfohlenen Implementierungsmethode.

## Anfängliche Hinweise

* Bei den folgenden Elementen wird davon ausgegangen, dass Sie [!DNL Platform Launch] zur Implementierung auf Ihrer Site verwenden. Wenn Sie [!DNL Platform Launch] nicht verwenden, gibt es weiterhin Überlegungen. Sie müssen diese jedoch an Ihre Implementierungsmethode anpassen.
* Alle SPA unterscheiden sich, sodass Sie möglicherweise einige der folgenden Elemente anpassen müssen, um Ihren Anforderungen am besten zu entsprechen. Wir wollten jedoch einige Best Practices mit Ihnen teilen. Dinge, die Sie beim Senden von Daten von SPA Seiten an Audience Manager beachten müssen.

## Einfaches Diagramm zum Arbeiten mit SPA und AAM im Experience Platform Launch {#simple-diagram-of-working-with-spas-and-aam-in-experience-platform-launch}

![spa in  [!DNL launch]](assets/spa_for_aam_in_launch.png)

>[!NOTE]
>Wie angegeben, ist dies ein vereinfachtes Diagramm dazu, wie SPA Seiten in einer Adobe Audience Manager-Implementierung (ohne Adobe Analytics) mit [!DNL Platform Launch] verarbeitet werden. Wie Sie sehen können, ist es recht unkompliziert, wobei die große Entscheidung darin besteht, wie Sie eine Änderung der Ansicht (oder eine Aktion) an [!DNL Platform Launch] kommunizieren.

## Auslösen von [!DNL Launch] von der SPA {#triggering-launch-from-the-spa-page}

Zwei der gängigeren Methoden zum Auslösen einer Regel in [!DNL Platform Launch] (und somit zum Senden von Daten an Audience Manager) sind:

* Festlegen benutzerdefinierter JavaScript-Ereignisse (siehe Beispiel [HERE](https://helpx.adobe.com/analytics/kt/using/spa-analytics-best-practices-feature-video-use.html) mit Adobe Analytics)
* Verwenden eines [!UICONTROL Direct Call Rule]

In diesem Audience Manager verwenden wir [!UICONTROL Direct Call rule] in [!DNL Launch], um den Treffer in den Audience Manager Trigger. Wie Sie in den nächsten Abschnitten sehen werden, ist dies wirklich nützlich, wenn Sie den [!UICONTROL Data Layer] auf einen neuen Wert setzen, damit er von [!UICONTROL Data Element] in [!DNL Platform Launch] aufgenommen werden kann.

## Demoseite {#demo-page}

Wir haben eine kleine Demoseite erstellt, die zeigt, wie Sie einen Wert im [!DNL data layer] ändern und ihn wie auf einer SPA an AAM senden. Diese Funktion kann für detailliertere Änderungen modelliert werden, die erforderlich sind. Sie finden diese Demoseite [HIER](https://aam.enablementadobe.com/SPA-Launch.html).

## Durch Einstellung der [!DNL data layer] {#setting-the-data-layer}

Wie bereits erwähnt, muss beim Laden neuer Inhalte auf der Seite oder beim Ausführen einer Aktion auf der Site [!DNL data layer] dynamisch im Seitenkopf eingestellt werden, BEVOR [!DNL Launch] aufgerufen wird und das [!UICONTROL rules] ausgeführt wird, damit [!DNL Platform Launch] die neuen Werte aus dem [!DNL data layer] übernehmen und in den Audience Manager übertragen kann.

Wenn Sie die oben aufgeführte Demosite aufrufen und sich die Seitenquelle ansehen, sehen Sie:

* Der [!DNL data layer] befindet sich im Kopf der Seite, vor dem Aufruf von [!DNL Platform Launch]
* Das JavaScript im simulierten SPA-Link ändert den [!UICONTROL Data Layer]-Aufruf und DANN den Aufruf [!DNL Platform Launch] (der Aufruf _satellite.track() ). Wenn Sie benutzerdefinierte JavaScript-Ereignisse anstelle dieses [!UICONTROL Direct Call Rule]-Elements verwendet haben, ist die Lektion die gleiche. Ändern Sie zunächst [!DNL data layer] und rufen Sie dann [!DNL Launch] auf.

>[!VIDEO](https://video.tv.adobe.com/v/23322/?quality=12)

## Zusätzliche Ressourcen {#additional-resources}

* [SPA über die Adobe](https://forums.adobe.com/thread/2451022)
* [Referenzarchitektur-Sites , auf denen gezeigt wird, wie SPA in Launch by Adobe implementiert werden](https://helpx.adobe.com/experience-manager/kt/integration/using/launch-reference-architecture-SPA-tutorial-implement.html)
* [Verwenden von Best Practices beim SPA in Adobe Analytics](https://helpx.adobe.com/analytics/kt/using/spa-analytics-best-practices-feature-video-use.html)
* [Für diesen Artikel verwendete Demosite](https://aam.enablementadobe.com/SPA-Launch.html)
