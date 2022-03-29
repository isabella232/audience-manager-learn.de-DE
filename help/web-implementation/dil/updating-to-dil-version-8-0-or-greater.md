---
title: Aktualisierung auf Adobe Audience Manager DIL Version 8.0 (oder höher)
description: In diesem Artikel erfahren Sie, wie Sie den Adobe Audience Manager (AAM) Data Integration Library-Code (DIL) auf Version 8.0 oder höher aktualisieren. Dies bezieht sich auf die "Client-seitige"DIL-Implementierung, nicht auf die serverseitige Weiterleitung von Adobe Analytics-Daten und umfasst DTM-, Launch by Adobe- und Implementierungen ohne Adobe-Tag-Manager-Lösung.
feature: DIL Implementation
topics: null
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1841
role: Developer, Data Engineer
level: Intermediate
exl-id: 8c1e6ed5-0f21-427b-a681-0ecb020a0e60
source-git-commit: 62b43b5627dabf754cf821f974a56c60989ef7ef
workflow-type: tm+mt
source-wordcount: '1122'
ht-degree: 1%

---

# Aktualisierung auf Adobe Audience Manager-DIL-Version 8.0 (oder höher) {#updating-to-adobe-audience-manager-s-dil-version-or-greater}

In diesem Artikel erhalten Sie Schritte und Empfehlungen zur Aktualisierung von Adobe Audience Manager (AAM). [!DNL Data Integration Library] (DIL) Code auf Version 8.0 oder höher. Dies bezieht sich auf die &quot;Client-seitige&quot;DIL-Implementierung, nicht auf die serverseitige Weiterleitung von Adobe Analytics-Daten und umfasst DTM-, Launch by Adobe- und Implementierungen ohne Adobe-Tag-Manager-Lösung.

## Überblick {#overview}

Audience Manager [!DNL Data Integration Library] (DIL)-Code ermöglicht die Implementierung von AAM auf Ihrer Website*. Bei der Implementierung früherer Versionen von DIL war es nicht erforderlich, den Experience Cloud ID Service (ECID) von Adobe ebenfalls implementieren zu lassen (obwohl dies eine sehr gute Idee war). Ab DIL-Version 8.0 besteht eine starke Abhängigkeit von ECID-Version 3.3 oder höher. Wenn Sie DIL 8.0 oder höher ohne ECID 3.3 oder mit einer früheren Version implementieren, wird ein Fehler ausgegeben, der nicht funktioniert. Da Sie AAM auf verschiedene Weise implementieren können, haben wir diese Seite erstellt, um Ihnen einige Schritte sowie einige Empfehlungen zu unterbreiten. Unten finden Sie diese Schritte und Empfehlungen aufgeschlüsselt nach Plattform-/Implementierungsmethode. Weitere Informationen über DIL finden Sie im [Dokumentation](https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/dil-overview.html?lang=en).

* Wie in der Beschreibung dieser Seite angegeben, betrifft dies nur Client-seitige DIL-Implementierungen, die von AAM Kunden verwendet werden, die nicht über Adobe Analytics verfügen. Wenn Sie über Adobe Analytics verfügen, sollten Sie die serverseitige Weiterleitungsmethode zur Implementierung von AAM verwenden. Diese Methode wird im Abschnitt [Dokumentation](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/server-side-forwarding/ssf.html).

## Duplizieren und veraltete Elemente und Methoden {#duplicate-and-deprecated-elements-and-methods}

In früheren Versionen von DIL und ECID gab es duplizierende Methoden (Methoden, die dieselbe Funktion sowohl bei DIL als auch bei ECID anwenden), was zu Verwirrung darüber führte, welche verwendet werden sollte. In der Regel mussten Sie beide verwenden und sie miteinander verknüpfen, und diese Nachricht wurde unseren Kunden nicht gut kommuniziert. Ab DIL 8.0 sind diese doppelten Methoden und Elemente in DIL nicht mehr enthalten. Es wird empfohlen, die ECID-Version zu verwenden.

Beispiel:

* Bei Verwendung von [!DNL DIL.create], wurden einige Elemente veraltet und sollten stattdessen die ECID-Elemente verwenden. Diese Elemente werden im Abschnitt [[!DNL DIL.create] Dokumentation](https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/class-level-dil-methods/dil-create.html).
* Die [!DNL idSync] Die Methode auf Instanzebene wird ebenfalls nicht mehr unterstützt, wie in der Methode [Dokumentation](https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/dil-instance-methods.html).

## ID-Synchronisierung mit einer Kunden-ID {#id-syncing-with-a-customer-id}

In AAM können Sie Ihre UUID (anonyme eindeutige Benutzer-ID) auf dem Computer mit einer Kunden-ID synchronisieren, sodass Sie Offline-Daten zu diesem Kunden hochladen und mit seinem Online-Verhalten verknüpfen können, um ein besseres Verständnis Ihrer Kunden zu erhalten. In der Vergangenheit wurde dies auf zwei Arten durchgeführt:

* Die [!DNL idSync] Methode auf Instanzebene
* Die [!DNL declaredId] Element in [!DNL DIL.create]

Wenn Sie eine dieser älteren Methoden zur Synchronisierung mit einer Kunden-ID verwendet haben, wird dringend empfohlen, das Update auf [!DNL setCustomerIDs] -Methode, die Teil des ECID-Dienstes ist. Weitere Informationen [!DNL setCustomerIDs] ist im [Dokumentation](https://experienceleague.adobe.com/docs/id-service/using/id-service-api/methods/setcustomerids.html).

**Quick Tipp:** Wenn Sie zuvor eine der oben genannten Methoden verwendet haben, haben Sie auf die AAM verwiesen [!UICONTROL Data Source] mit dem [!UICONTROL Data Source] ID (AKA die &quot;DPID&quot;). Beim Aktualisieren auf [!DNL setCustomerIDs], müssen Sie die AAM [!UICONTROL Data Source]s &quot;[!UICONTROL Integration Code]&quot;. Er weist immer noch auf dasselbe hin [!UICONTROL Data Source] aber ist nur eine andere Kennung. Dies wird im Video unten gezeigt.

>[!VIDEO](https://video.tv.adobe.com/v/23873/?quality=12)

In den folgenden Abschnitten finden Sie Schritte und Empfehlungen für die Aktualisierung auf DIL 8.0 basierend auf Ihrer Implementierungsmethode:

## Aktualisieren auf DIL 8.0 in Adobe Experience Platform-Tags {#updating-to-dil-in-experience-platform-launch}

Grundlegende Schritte für die Aktualisierung auf DIL 8.0

1. Wenn Sie DIL vor dem Upgrade vor Version 8.0 verwenden, gehen Sie in die DIL-Konfiguration in der AAM-Erweiterung und beachten Sie alle erweiterten Optionen, die Sie verwenden (die in einem nachfolgenden Schritt verwendet werden sollen).
1. Aktualisieren Sie Ihre AAM-Erweiterung auf Version 8.0 oder höher.
1. Stellen Sie sicher, dass die Experience Cloud ID Service-Erweiterung Version 3.3.0 oder höher ist.
1. Für alle veralteten Methoden/Elemente (wie `disableIDSyncs`), die sich in Ihrer Erweiterung vor 8.0 AAM oder in benutzerdefiniertem Code für DIL befanden, aktivieren Sie die ECID-Methoden in der ECID-Erweiterung.

   1. (DIL) `disableDestinationPublishingIframe` -> (ECID) `disableIdSyncs`
   1. (DIL) `disableIDSyncs` -> (ECID) `disableIdSyncs`
   1. (DIL) `iframeAkamaiHTTPS` -> (ECID) `dSyncSSLUseAkamai`
   1. (DIL) `declaredId` -> (ECID) `setCustomerIDs`

1. Veröffentlichen Sie die Änderungen.

>[!VIDEO](https://video.tv.adobe.com/v/23874/?quality=12)

## Aktualisierung auf DIL 8.0 in Adobe DTM {#updating-to-dil-in-adobe-dtm}

1. Aktualisieren Sie Ihr AAM-Tool auf Version 8.0 oder höher. Diese Versionseinstellung befindet sich im Abschnitt &quot;Allgemein&quot;des AAM Tools.
1. Für alle veralteten Methoden/Elemente (wie `disableIDSyncs`), die sich im benutzerdefinierten Code Ihres AAM-Tools vor 8.0 für das DIL befanden, notieren Sie sich diese (damit Sie sie zum ECID-Tool hinzufügen können) und entfernen Sie sie dann aus dem benutzerdefinierten [!DNL DIL code] im AAM Tool.
1. Aktualisieren Sie Ihre Experience Cloud ID Service-Erweiterung auf Version 3.3.0 oder höher.
1. Fügen Sie dem ECID-Tool die erweiterten Optionen hinzu, die Sie aus dem benutzerdefinierten Code des AAM Tools entfernt haben.
1. Veröffentlichen der Änderungen

## Aktualisierung auf DIL 8.0 ohne Adobe Tag Management-Lösung {#additional-resources}

Wenn Sie Ihren Code direkt auf der Seite aktualisieren, können Sie nur ältere Elemente durch neuere Elemente ersetzen, außer wenn Sie, wie oben erläutert, Methoden/Elemente von DIL in ECID verschieben müssen. In diesem Fall ersetzen Sie einfach die alte Methode/das alte Element am DIL-Speicherort durch die ECID-Methode/-Element am ECID-Speicherort.

Dasselbe gilt für Tag-Manager ohne Adobe. Ersetzen Sie die alten Versionen in dieser Tag-Management-Lösung durch den neuen Code, wie in den folgenden Schritten beschrieben.

1. Aktualisieren Sie Ihre DIL-Bibliothek auf die neueste Version (8.0 oder höher) - Sie müssen den neuesten DIL-Code von Adobe Consulting oder der Adobe-Kundenunterstützung erhalten, da er derzeit nicht an einem öffentlichen Speicherort verfügbar ist. Ersetzen Sie dann einfach den alten DIL-Bibliotheks-Code durch den neuen DIL-Bibliothekscode und fahren Sie mit dem nächsten Schritt fort (stoppen Sie nicht jetzt, oder Sie werden auf Probleme stoßen, ha).
1. Installieren [!DNL ECID Service] oder aktualisieren Sie Ihre vorhandene Version auf 3.3.0 oder höher. Sie können die neueste Version des Experience Cloud ID-Diensts herunterladen [von unserer GitHub-Seite](https://github.com/Adobe-Marketing-Cloud/id-service/releases). Wenn Sie dabei Hilfe benötigen, lesen Sie den Abschnitt [Dokumentation](https://experienceleague.adobe.com/docs/id-service/using/home.html) oder wenden Sie sich an einen Adobe Consultant.

1. Stellen Sie sicher, dass alle veralteten Methoden oder Elemente, die sich in Ihrem benutzerspezifischen Code für die DIL befinden, in die ECID-Methoden verschoben werden:

   1. (DIL) `disableDestinationPublishingIframe` -> (ECID) `disableIdSyncs`

      [Dokumentation](https://experienceleague.adobe.com/docs/id-service/using/id-service-api/configurations/disableidsync.html)

   1. (DIL) `disableIDSyncs` -> (ECID) `disableIdSyncs`

      [Dokumentation](https://experienceleague.adobe.com/docs/id-service/using/id-service-api/configurations/disableidsync.html)

   1. (DIL) `iframeAkamaiHTTPS` -> (ECID) `idSyncSSLUseAkamai`

      [Dokumentation](https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/class-level-dil-methods/dil-create.html)

   1. (DIL) `declaredId` -> (ECID) `setCustomerIDs`

      [Dokumentation](https://experienceleague.adobe.com/docs/id-service/using/id-service-api/methods/setcustomerids.html)
