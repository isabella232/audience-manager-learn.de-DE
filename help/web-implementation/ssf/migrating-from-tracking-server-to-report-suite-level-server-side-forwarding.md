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


# Migration von [!UICONTROL Tracking Server] auf [!UICONTROL Report Suite]Ebene [!UICONTROL Server-Side Forwarding] {#migrating-from-tracking-server-to-report-suite-level-server-side-forwarding}

Dieser Artikel und dieses Video zeigen Ihnen, wie Sie die Aktivierung [!UICONTROL server-side forwarding] von [!DNL Analytics] Daten für den Audience Manager auf [!UICONTROL report suite] anstatt auf einer [!UICONTROL tracking server] Ebene aktivieren können.

## Einführung {#introduction}

Wenn Sie über Adobe Audience Manager UND Adobe Analytics verfügen, können Sie &quot;[!UICONTROL Server-side Forwarding]&quot;der [!DNL Analytics] Daten für Audience Manager implementieren. Das bedeutet, dass Ihre Seite, anstatt zwei Treffer zu senden (ein Treffer zu [!DNL Analytics] und ein Treffer zu Audience Manager), einfach einen Treffer an senden kann [!DNL Analytics]und diese Daten an Audience Manager weiterleitet [!DNL Analytics] . Wenn Sie diese Funktion bereits in Betrieb haben und sie vor Oktober 2017 aktiviert/implementiert haben, [!UICONTROL server-side forwarding] können Sie auf Ihrem &quot;[!UICONTROL Tracking Server]&quot; basieren, das durch die Adobe Customer Care oder Adobe Consulting aktiviert werden musste. Ab Oktober 2017 können Sie jetzt [!UICONTROL server-side forwarding] sich selbst konfigurieren und dies auf einer [!UICONTROL Report Suite] Ebene tun (Weiterleitung pro [!UICONTROL Report Suite]). Dies hat erhebliche Vorteile, die nachfolgend erörtert werden.

## [!UICONTROL Tracking Server] Weiterleitung {#tracking-server-forwarding}

Ihr [!UICONTROL tracking server] ist der Ort, an den Sie Ihre [!DNL Analytics] Daten senden, sowie die Domäne, in der die Bildanforderung und das Cookie geschrieben werden. Es sollte in DTM oder [!DNL Experience Platform Launch]oder in der [!DNL AppMeasurement.js] Datei eingestellt werden und sieht in der Regel wie folgt aus, wobei Ihr Site- oder Geschäftsname &quot;mysite&quot;ersetzt:

`s.trackingServer = "mysite.sc.omtrdc.net";`

Wenn [!UICONTROL server-side forwarding] die Weiterleitung auf der [!UICONTROL tracking server] Ebene eingerichtet ist, werden alle Treffer, die an diesen gesendet werden [!UICONTROL tracking server] (sofern der Experience Cloud-ID-Dienst ebenfalls aktiviert ist), an den Audience Manager weitergeleitet. Dies musste durch die Adobe Kundenunterstützung oder Adobe Consulting aktiviert werden. Sie sind auch diejenigen, die es deaktivieren können, nachdem Sie auf die [!UICONTROL report suite] Weiterleitung umgestellt haben, wie unten beschrieben.

Wenn Sie sich nicht sicher sind, ob die Option für Sie aktiviert [!DNL tracking server forwarding] ist, wenden Sie sich an die Kundenunterstützung oder Adobe Consulting der Adobe, und Sie sollten davon in Kenntnis gesetzt werden können.

## [!UICONTROL Report Suite]-Ebene [!UICONTROL Server-Side Forwarding] {#report-suite-level-server-side-forwarding}

Einer der größten Vorteile für den Umstieg auf die [!UICONTROL report suite] Weiterleitung von der [!UICONTROL tracking server] Weiterleitung ist, dass Sie jetzt &quot;Audience Analytics&quot; verwenden können, was die Möglichkeit ist, Audience Manager [!UICONTROL segments] zurück nach Adobe Analytics zu leiten, um eine detaillierte [!UICONTROL segment] Analyse zu erhalten. Diese großartige Funktion wird NICHT unterstützt, wenn Sie noch [!UICONTROL tracking server] weiterleiten und nicht [!UICONTROL report suite] weiterleiten. Weitere Informationen zu Audience Analytics finden Sie in der [Dokumentation](https://marketing.adobe.com/resources/help/en_US/analytics/audiences/).

>[!VIDEO](https://video.tv.adobe.com/v/23701/?quality=12)

## Wichtiger Tipp {#additional-resources}

Wie im oben stehenden Video angegeben, sollten Sie sich an die Adobe Customer Care oder Adobe Consulting wenden, sobald Sie alle [!UICONTROL report suites] Vorkehrungen getroffen haben, um an den Audience Manager weiterzuleiten, und diese die [!UICONTROL tracking server] Weiterleitung deaktivieren lassen. Es ist kein Notfall für Sie, dies zu tun, weil sowohl [!UICONTROL tracking server] Speditions- als auch [!UICONTROL report suite] Speditionsdienste KEINEN Duplikat-Treffer verursachen. Es empfiehlt sich jedoch, nur eine Weiterleitung [!UICONTROL report suite] vorzunehmen. Wenn Sie die [!UICONTROL tracking server] Weiterleitung fortsetzen, werden möglicherweise nicht nur Daten weitergeleitet, [!UICONTROL report suites] die nicht weitergeleitet werden sollen, sondern auch in Zukunft, nachdem Sie (und alle an Ihrer Firma) vergessen haben, dass die [!UICONTROL tracking server] Weiterleitung aktiviert ist, können Sie denken, dass die Daten für eine bestimmte Person nicht weitergeleitet werden [!UICONTROL report suite] (weil sie nicht auf Report Suite-Ebene aktiviert ist), aber die Daten werden trotzdem aufgrund des [!UICONTROL tracking server]Berichts weitergeleitet. Dann verschwenden Sie Zeit und Geld, um herauszufinden, warum es weiterleitet und auch für AAM Server-Aufrufe bezahlt, die Sie nicht erwartet haben. Es ist also eine gute Idee, die [!UICONTROL tracking server] Weiterleitung zu deaktivieren, sobald Sie alle Voraussetzungen für die Weiterleitung haben, die für Ihre geschäftlichen Anforderungen sinnvoll [!UICONTROL report suites] sind.
