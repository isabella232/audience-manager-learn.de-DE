---
title: Migration vom Tracking-Server zur serverseitigen Weiterleitung auf Report Suite-Ebene
description: In diesem Artikel und Video erfahren Sie, wie Sie die serverseitige Weiterleitung von Analytics-Daten an den Audience Manager auf Report Suite-Ebene und nicht auf Tracking-Server-Ebene aktivieren.
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
source-git-commit: 4d4c12e9f9a33760a89460258c3802fcf3a4e22b
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 0%

---

# Migration von [!UICONTROL Tracking Server] zu [!UICONTROL Report Suite]-Level [!UICONTROL Server-Side Forwarding] {#migrating-from-tracking-server-to-report-suite-level-server-side-forwarding}

Dieser Artikel und dieses Video zeigen Ihnen, wie Sie [!UICONTROL server-side forwarding] von [!DNL Analytics] Daten für den Audience Manager auf einer [!UICONTROL report suite]-Ebene aktivieren können, anstatt auf einer [!UICONTROL tracking server]-Ebene.

## Einführung {#introduction}

Wenn Sie über Adobe Audience Manager UND Adobe Analytics verfügen, können Sie &quot;[!UICONTROL Server-side Forwarding]&quot;der [!DNL Analytics]-Daten in Audience Manager implementieren. Anstatt also zwei Treffer auf Ihrer Seite zu senden (einen an [!DNL Analytics] und einen an den Audience Manager), kann einfach ein Treffer an [!DNL Analytics] gesendet werden. [!DNL Analytics] leitet diese Daten an den Audience Manager weiter. Wenn Sie dies bereits eingerichtet haben und vor Oktober 2017 aktiviert/implementiert haben, basiert Ihr [!UICONTROL server-side forwarding] möglicherweise auf Ihrem &quot;[!UICONTROL Tracking Server]&quot;, das von der Kundenunterstützung oder Adobe Consulting von Adobe aktiviert werden musste. Ab Oktober 2017 können Sie [!UICONTROL server-side forwarding] jetzt selbst konfigurieren und auf einer [!UICONTROL Report Suite]-Ebene ausführen (Weiterleitung pro [!UICONTROL Report Suite]). Dies hat erhebliche Vorteile, die nachfolgend erörtert werden.

## [!UICONTROL Tracking Server] Weiterleitung {#tracking-server-forwarding}

Ihr [!UICONTROL tracking server] ist der Ort, an den Sie Ihre [!DNL Analytics]-Daten senden, sowie die Domäne, in die die Bildanforderung und das Cookie geschrieben werden. Sie sollte in DTM oder [!DNL Experience Platform Launch] oder in der Datei [!DNL AppMeasurement.js] festgelegt werden und sieht in der Regel wie folgt aus, wobei Ihr Site- oder Geschäftsname &quot;mysite&quot;ersetzt:

`s.trackingServer = "mysite.sc.omtrdc.net";`

Wenn [!UICONTROL server-side forwarding] für die Weiterleitung auf der Ebene [!UICONTROL tracking server] eingerichtet ist, werden alle Treffer, die an diesen gesendet werden [!UICONTROL tracking server] (WENN der Experience Cloud-ID-Dienst ebenfalls aktiviert ist), an Audience Manager weitergeleitet. Dies musste durch die Kundenunterstützung oder Adobe Consulting von Adobe aktiviert werden. Es sind auch diejenigen, die es deaktivieren können, nachdem Sie auf [!UICONTROL report suite] Weiterleitung umgestellt haben, wie unten beschrieben.

Wenn Sie sich nicht sicher sind, ob [!DNL tracking server forwarding] für Sie aktiviert ist, wenden Sie sich an die Kundenunterstützung von Adobe oder an Adobe Consulting. Diese sollte Ihnen Bescheid geben können.

## [!UICONTROL Report Suite]-Ebene [!UICONTROL Server-Side Forwarding] {#report-suite-level-server-side-forwarding}

Einer der größten Vorteile beim Wechsel zur [!UICONTROL report suite]-Weiterleitung von der [!UICONTROL tracking server]-Weiterleitung besteht darin, dass Sie jetzt &quot;Audience Analytics&quot;verwenden können. Dies ist die Möglichkeit, Audience Manager [!UICONTROL segments] zur detaillierten [!UICONTROL segment]-Analyse zurück an Adobe Analytics zu leiten. Diese großartige Funktion wird NICHT unterstützt, wenn Sie noch mit der [!UICONTROL tracking server]-Weiterleitung und nicht mit der [!UICONTROL report suite] Weiterleitung arbeiten. Weitere Informationen zum Audience Analytics finden Sie in der [Dokumentation](https://experienceleague.adobe.com/docs/analytics/integration/audience-analytics/mc-audiences-aam.html).

>[!VIDEO](https://video.tv.adobe.com/v/23701/?quality=12)

## Wichtiger Tipp {#additional-resources}

Wie im obigen Video angegeben, sollten Sie sich an die Kundenunterstützung von Adobe oder Adobe Consulting wenden und die [!UICONTROL tracking server]-Weiterleitung deaktivieren, sobald Sie alle [!UICONTROL report suites]-Einstellungen festgelegt haben, um die Weiterleitung an den Audience Manager weiterzuleiten. Dies ist kein Notfall für Sie, da sowohl die [!UICONTROL tracking server] Weiterleitung als auch die [!UICONTROL report suite] Weiterleitung NICHT zu doppelten Treffern führen. Es empfiehlt sich jedoch, nur [!UICONTROL report suite] Weiterleitung zu verwenden. Wenn Sie die Weiterleitung von [!UICONTROL tracking server] aktivieren, werden möglicherweise nicht nur Daten von [!UICONTROL report suites] weitergeleitet, die Sie nicht weiterleiten möchten. In Zukunft werden Sie, nachdem Sie (und alle Mitarbeiter in Ihrem Unternehmen) vergessen haben, dass die [!UICONTROL tracking server]-Weiterleitung aktiviert ist, möglicherweise glauben, dass Daten nicht für ein bestimmtes [!UICONTROL report suite] weitergeleitet werden (da sie nicht auf Report Suite-Ebene aktiviert ist). Die Daten werden jedoch trotzdem weitergeleitet, weil [!UICONTROL tracking server]. Dann verschwenden Sie Zeit und Geld, um herauszufinden, warum es weiterleitet und auch für AAM Server-Aufrufe bezahlt, die Sie nicht erwartet haben. Daher ist es nur eine gute Idee, die [!UICONTROL tracking server] Weiterleitung zu deaktivieren, sobald Sie alle [!UICONTROL report suites] für die Weiterleitung eingerichtet haben, die für Ihre geschäftlichen Anforderungen sinnvoll sind.
