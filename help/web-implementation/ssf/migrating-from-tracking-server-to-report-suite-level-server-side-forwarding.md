---
title: Migration vom Tracking-Server zum serverseitigen Weiterleiten auf Report Suite-Ebene
description: Dieser Artikel und dieses Video zeigen Ihnen, wie Sie die serverseitige Weiterleitung von Analytics-Daten an Audience Manager auf Report Suite-Ebene und nicht auf Tracking-Server-Ebene aktivieren können.
product: audience manager, analytics
feature: integration with analytics
topics: null
audience: implementer
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1776
translation-type: tm+mt
source-git-commit: dfd549508cc223714bdb07ac6fd2aa31e6ca5586
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 0%

---


# Migration von [!UICONTROL Tracking Server] zu [!UICONTROL Report Suite]-Level [!UICONTROL Server-Side Forwarding] {#migrating-from-tracking-server-to-report-suite-level-server-side-forwarding}

Dieser Artikel und dieses Video zeigen Ihnen, wie [!UICONTROL server-side forwarding] von [!DNL Analytics] Daten für den Audience Manager auf einer [!UICONTROL report suite]-Ebene anstatt auf einer [!UICONTROL tracking server]-Ebene aktiviert werden können.

## Einführung {#introduction}

Wenn Sie über Adobe Audience Manager UND Adobe Analytics verfügen, können Sie &quot;[!UICONTROL Server-side Forwarding]&quot;der [!DNL Analytics]-Daten in Audience Manager implementieren. Das bedeutet, dass statt Ihrer Seite zwei Treffer (ein nach [!DNL Analytics] und ein Treffer nach Audience Manager) einfach ein Treffer an [!DNL Analytics] gesendet werden kann und [!DNL Analytics] diese Daten an Audience Manager weiterleitet. Wenn Sie diese Funktion bereits in Betrieb haben und sie vor Oktober 2017 aktiviert/implementiert haben, können Sie [!UICONTROL server-side forwarding] auf der Grundlage Ihrer &quot;[!UICONTROL Tracking Server]&quot;-Funktion verwenden, die von der Adobe Customer Care oder Adobe Consulting aktiviert werden musste. Ab Oktober 2017 können Sie [!UICONTROL server-side forwarding] selbst konfigurieren und auf [!UICONTROL Report Suite]-Ebene (Weiterleitung PER [!UICONTROL Report Suite]) ausführen. Dies hat erhebliche Vorteile, die nachfolgend erörtert werden.

## [!UICONTROL Tracking Server] Weiterleitung  {#tracking-server-forwarding}

Ihr [!UICONTROL tracking server] ist der Ort, an den Sie Ihre [!DNL Analytics]-Daten senden, sowie die Domäne, in der die Bildanforderung und das Cookie geschrieben werden. Es sollte in DTM oder [!DNL Experience Platform Launch] oder in der [!DNL AppMeasurement.js]-Datei eingestellt werden und sieht in der Regel wie folgt aus, wobei Ihr Site- oder Geschäftsname &quot;mysite&quot;ersetzt:

`s.trackingServer = "mysite.sc.omtrdc.net";`

Wenn [!UICONTROL server-side forwarding] auf der [!UICONTROL tracking server]-Ebene für die Weiterleitung eingerichtet ist, werden alle Treffer, die an dieses [!UICONTROL tracking server] gesendet werden (sofern der Experience Cloud-ID-Dienst ebenfalls aktiviert ist), an Audience Manager weitergeleitet. Dies musste durch die Adobe Kundenunterstützung oder Adobe Consulting aktiviert werden. Sie sind auch diejenigen, die es deaktivieren können, nachdem Sie auf [!UICONTROL report suite] Weiterleitung umgestellt haben, wie unten beschrieben.

Wenn Sie sich nicht sicher sind, ob [!DNL tracking server forwarding] für Sie aktiviert ist, wenden Sie sich an den Kundendienst oder die Adobe Consulting-Abteilung der Adobe, die Sie darüber informieren sollte.

## [!UICONTROL Report Suite]-Ebene  [!UICONTROL Server-Side Forwarding] {#report-suite-level-server-side-forwarding}

Einer der größten Vorteile beim Umstieg auf [!UICONTROL report suite]-Weiterleitung von [!UICONTROL tracking server] ist, dass Sie jetzt &quot;Audience Analytics&quot; verwenden können. Dies ist die Möglichkeit, Audience Manager [!UICONTROL segments] für eine detaillierte [!UICONTROL segment]-Analyse zurück nach Adobe Analytics zu leiten. Diese großartige Funktion wird NICHT unterstützt, wenn Sie noch mit [!UICONTROL tracking server] Weiterleitung und nicht mit [!UICONTROL report suite] Weiterleitung arbeiten. Weitere Informationen zu Audience Analytics finden Sie in der [Dokumentation](https://marketing.adobe.com/resources/help/en_US/analytics/audiences/).

>[!VIDEO](https://video.tv.adobe.com/v/23701/?quality=12)

## Wichtiger Tipp {#additional-resources}

Wie im Video oben angegeben, sollten Sie sich an die Adobe Customer Care oder Adobe Consulting wenden und die [!UICONTROL tracking server]-Weiterleitung deaktivieren lassen, sobald Sie alle [!UICONTROL report suites] eingestellt haben, um die Weiterleitung an den Audience Manager weiterzuleiten. Dies ist kein Notfall für Sie, da sowohl die [!UICONTROL tracking server] Weiterleitung als auch die [!UICONTROL report suite] Weiterleitung NICHT zu Duplikat-Treffern führen. Es empfiehlt sich jedoch, nur [!UICONTROL report suite] Weiterleitung zu haben. Wenn Sie die [!UICONTROL tracking server]-Weiterleitung fortsetzen, können Sie nicht nur Daten von [!UICONTROL report suites] weiterleiten, die Sie nicht weiterleiten möchten, sondern in Zukunft, nachdem Sie (und alle an Ihrer Firma) vergessen haben, dass die [!UICONTROL tracking server] Weiterleitung aktiviert ist, können Sie denken, dass Daten für ein bestimmtes [!UICONTROL report suite] nicht weitergeleitet werden (da sie nicht auf Report Suite-Ebene aktiviert ist), die Daten jedoch trotzdem weitergeleitet werden, da sie weitergeleitet werden, da des [!UICONTROL tracking server] Dann verschwenden Sie Zeit und Geld, um herauszufinden, warum es weiterleitet und auch für AAM Server-Aufrufe bezahlt, die Sie nicht erwartet haben. Es empfiehlt sich daher, die [!UICONTROL tracking server]-Weiterleitung zu deaktivieren, sobald Sie alle [!UICONTROL report suites]-Vorbereitungen abgeschlossen haben, die für Ihre geschäftlichen Anforderungen sinnvoll sind.
