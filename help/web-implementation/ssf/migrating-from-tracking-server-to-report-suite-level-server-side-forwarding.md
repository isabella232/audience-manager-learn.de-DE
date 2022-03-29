---
title: Migration vom Tracking-Server zur serverseitigen Weiterleitung auf Report Suite-Ebene
description: Erfahren Sie, wie Sie die serverseitige Weiterleitung von Adobe Analytics-Daten an den Audience Manager auf Report Suite-Ebene und nicht auf Tracking-Server-Ebene aktivieren.
product: audience manager
feature: Adobe Analytics Integration
topics: null
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1776
role: Developer, Data Engineer
level: Intermediate
exl-id: 08b81e52-a28a-43e4-a284-df2460a43016
source-git-commit: 4adaade180545bcf5f911b7453a7e9939e2ed178
workflow-type: tm+mt
source-wordcount: '586'
ht-degree: 0%

---

# Migration vom Tracking-Server zur serverseitigen Weiterleitung auf Report Suite-Ebene {#migrating-from-tracking-server-to-report-suite-level-server-side-forwarding}

In diesem Artikel und Video erfahren Sie, wie Sie die serverseitige Weiterleitung von [!DNL Analytics] Daten an Audience Manager zu einem [!UICONTROL report suite] anstatt auf einer [!UICONTROL tracking server] Ebene.

## Einführung {#introduction}

Wenn Sie über Adobe Audience Manager UND Adobe Analytics verfügen, können Sie die serverseitige Weiterleitung der [!DNL Analytics] Daten an Audience Manager weitergeleitet werden. Das bedeutet, dass Ihre Seite statt zwei Treffer (einen zu [!DNL Analytics] und 1 zu Audience Manager), kann ein Treffer an gesendet werden. [!DNL Analytics]und [!DNL Analytics] leitet diese Daten an Audience Manager weiter.

Wenn Sie dies bereits ausgeführt haben und vor Oktober 2017 aktiviert/implementiert haben, basiert Ihre serverseitige Weiterleitung möglicherweise auf Ihrer [!UICONTROL Tracking Server], die von der Adobe-Kundenunterstützung oder Adobe Consulting aktiviert werden musste. Ab Oktober 2017 können Sie jetzt die serverseitige Weiterleitung selbst konfigurieren und sie auf Report Suite-Ebene (Weiterleitung pro Report Suite) durchführen. Dies hat erhebliche Vorteile, die im Folgenden erläutert werden.

## [!UICONTROL Tracking server] Weiterleitung {#tracking-server-forwarding}

Ihre [!UICONTROL tracking server] ist der Ort, an den Sie Ihre [!DNL Analytics] -Daten sowie die Domäne, in der die Bildanforderung und das Cookie geschrieben werden. Sie sollte in DTM oder [!DNL Experience Platform Launch]oder im [!DNL AppMeasurement.js] -Datei und wird in der Regel wie folgt aussehen, wobei Ihre Site oder Ihr Geschäftsname &quot;mysite&quot;ersetzt:

`s.trackingServer = "mysite.sc.omtrdc.net";`

Wenn die serverseitige Weiterleitung für die Weiterleitung auf der [!UICONTROL tracking server] Ebene, jeden Treffer, der an diesen gesendet wird [!UICONTROL tracking server] (WENN der Experience Cloud-ID-Dienst ebenfalls aktiviert ist) wird an Audience Manager weitergeleitet. Dies musste durch die Kundenunterstützung oder Adobe Consulting von Adobe aktiviert werden. Sie sind auch diejenigen, die sie deaktivieren können, nachdem Sie auf [!UICONTROL report suite] Weiterleitung, wie unten beschrieben.

Wenn Sie sich nicht sicher sind, ob [!DNL tracking server forwarding] für Sie aktiviert ist, wenden Sie sich an die Kundenunterstützung von Adobe oder an Adobe Consulting und sie sollten Ihnen Bescheid geben können.

## [!UICONTROL Report-suite]-Level der serverseitigen Weiterleitung {#report-suite-level-server-side-forwarding}

Einer der größten Vorteile bei der Umstellung auf [!UICONTROL report suite] Weiterleitung von [!UICONTROL tracking server] Weiterleitung bedeutet, dass Sie jetzt &quot;Audience Analytics&quot;verwenden können, was die Möglichkeit bietet, Audience Manager weiterzuleiten [!UICONTROL segments] zurück in Adobe Analytics zur detaillierten Segmentanalyse. Diese großartige Funktion wird NICHT unterstützt, wenn Sie noch auf [!UICONTROL tracking server] Weiterleitung und nicht [!UICONTROL report suite] Weiterleitung. Weitere Informationen zu Audience Analytics finden Sie im Abschnitt [Dokumentation](https://experienceleague.adobe.com/docs/analytics/integration/audience-analytics/mc-audiences-aam.html).

>[!VIDEO](https://video.tv.adobe.com/v/23701/?quality=12)

## Wichtiger Tipp {#additional-resources}

Wie im Video oben angegeben, sobald Sie alle [!UICONTROL report suites] Sie sollten sich an die Kundenunterstützung oder Adobe Consulting von Adobe wenden und diese bitten, die [!UICONTROL tracking server] Weiterleitung. Dies ist kein Notfall für Sie, denn beide [!UICONTROL tracking server] Weiterleitung und [!UICONTROL report suite] Die Weiterleitung führt nicht zu doppelten Treffern. Es ist jedoch Best Practice, nur [!UICONTROL report suite] Weiterleitung an.

Wenn Sie gehen [!UICONTROL tracking server] Weiterleitung von Daten, nicht nur Weiterleiten von [!UICONTROL report suites] dass Sie nicht weiterleiten möchten, aber in Zukunft, nachdem Sie (und alle in Ihrem Unternehmen) vergessen hat, dass [!UICONTROL tracking server] Die Weiterleitung ist aktiviert. Möglicherweise glauben Sie, dass Daten für eine bestimmte [!UICONTROL report suite]. Dies liegt daran, dass sie nicht auf Report Suite-Ebene aktiviert ist, die Daten jedoch trotzdem weitergeleitet werden, weil die [!UICONTROL tracking server]. Dann verschwenden Sie Zeit und Geld, um herauszufinden, warum es weiterleitet und auch für AAM Server-Aufrufe bezahlt, die Sie nicht erwartet haben. Daher ist es empfehlenswert, die [!UICONTROL tracking server] Weiterleitung, sobald Sie alle [!UICONTROL report suites] die für Ihre geschäftlichen Anforderungen sinnvoll sind.
