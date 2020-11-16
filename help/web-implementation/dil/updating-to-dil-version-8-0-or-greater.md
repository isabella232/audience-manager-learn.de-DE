---
title: Aktualisieren auf Adobe Audience Manager DIL Version 8.0 (oder höher)
description: In diesem Artikel finden Sie Anweisungen und Empfehlungen zur Aktualisierung von Adobe Audience Manager (AAM) Data Integration Library (DIL)-Code auf Version 8.0 oder höher. Hierbei handelt es sich um eine clientseitige DIL-Implementierung, nicht um die serverseitige Weiterleitung von Adobe Analytics-Daten, und umfasst DTM-, Launch by Adobe- und Implementierungen ohne Adobe Tag Manager-Lösung.
feature: dil implementation
topics: null
audience: implementer
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1841
translation-type: tm+mt
source-git-commit: dfd549508cc223714bdb07ac6fd2aa31e6ca5586
workflow-type: tm+mt
source-wordcount: '1149'
ht-degree: 1%

---


# Aktualisieren auf Adobe Audience Manager DIL Version 8.0 (oder höher) {#updating-to-adobe-audience-manager-s-dil-version-or-greater}

In diesem Artikel finden Sie Anweisungen und Empfehlungen zur Aktualisierung von Adobe Audience Manager (AAM) [!DNL Data Integration Library] (DIL)-Code auf Version 8.0 oder höher. Hierbei handelt es sich um eine clientseitige DIL-Implementierung, nicht um die serverseitige Weiterleitung von Adobe Analytics-Daten, und umfasst DTM-, Launch by Adobe- und Implementierungen ohne Adobe Tag Manager-Lösung.

## Überblick {#overview}

Mit dem [!DNL Data Integration Library] (DIL-)Code des Audience Managers können Sie AAM auf Ihrer Website implementieren*. Bei der Implementierung früherer Versionen von DIL war es nicht erforderlich, dass der Experience Cloud-ID-Dienst (ECID) von Adobe ebenfalls implementiert wurde (auch wenn dies eine sehr gute Idee war). Ab DIL Version 8.0 besteht eine feste Abhängigkeit von ECID Version 3.3 oder höher. Wenn Sie DIL 8.0 oder höher ohne ECID 3.3 oder mit einer früheren Version implementieren, wird ein Fehler ausgegeben, der nicht funktioniert. Da es mehrere Möglichkeiten gibt, AAM zu implementieren, haben wir diese Seite erstellt, um Ihnen einige Schritte zu beschreiben, sowie einige Empfehlungen. Nachfolgend finden Sie die Schritte und Empfehlungen, die nach Plattform-/Implementierungsmethode aufgeschlüsselt werden. Weitere Informationen zum DIL finden Sie in der [Dokumentation](https://marketing.adobe.com/resources/help/en_US/aam/c_dil.html).

* Wie in der Beschreibung dieser Seite angegeben, betrifft dies nur clientseitige DIL-Implementierungen, die von AAM Kunden verwendet werden, die nicht über Adobe Analytics verfügen. Wenn Sie über Adobe Analytics verfügen, sollten Sie die serverseitige Weiterleitungsmethode zur Implementierung von AAM verwenden. Diese Methode wird in der [Dokumentation](https://marketing.adobe.com/resources/help/en_US/reference/ssf.html)beschrieben.

## Duplikat und veraltete Elemente und Methoden {#duplicate-and-deprecated-elements-and-methods}

In früheren Versionen von DIL und ECID gab es duplizierte Methoden (Methoden, die sowohl in DIL als auch in ECID dieselbe Funktion erfüllen), was zu Verwirrung darüber führte, welche Methode verwendet werden sollte. Normalerweise mussten Sie beide verwenden und sie zusammenführen, und diese Nachricht wurde unseren Kunden nicht gut mitgeteilt. Ab DIL 8.0 sind diese Duplikat-Methoden und -Elemente im DIL nicht mehr unterstützt. Es wird empfohlen, die ECID-Version zu verwenden.

Beispiel:

* Bei der Verwendung [!DNL DIL.create]wurden einige Elemente nicht mehr unterstützt und Sie sollten stattdessen die ECID-Elemente verwenden. Diese Elemente werden in der [[!DNL DIL.create] Dokumentation](https://marketing.adobe.com/resources/help/en_US/aam/r_dil_create.html)aufgeführt.
* Die Methode auf [!DNL idSync] Instanzebene wurde ebenfalls nicht mehr unterstützt, wie in der [Dokumentation](https://marketing.adobe.com/resources/help/en_US/aam/r_dil_idsync.html)der Methode ausgeführt.

## ID-Synchronisierung mit einer Kunden-ID {#id-syncing-with-a-customer-id}

In AAM können Sie Ihre UUID (anonyme eindeutige Benutzer-ID) auf dem Computer mit einer Kunden-ID synchronisieren, sodass Sie Offline-Daten zu diesem Kunden hochladen und mit deren Online-Verhalten verbinden können, um ein besseres Verständnis Ihrer Kunden zu erhalten. In der Vergangenheit wurde dies auf zweierlei Weise getan:

* Die Methode auf [!DNL idSync] Instanzebene
* Das [!DNL declaredId] Element in [!DNL DIL.create]

Wenn Sie eine dieser älteren Methoden zur Synchronisierung mit einer Kunden-ID verwendet haben, wird dringend empfohlen, dass Sie die [!DNL setCustomerIDs] Methode, die Teil des ECID-Dienstes ist, aktualisieren. Weitere Informationen [!DNL setCustomerIDs] finden Sie in der [Dokumentation](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid_setcustomerids.html)der Methode.

**QuickInfo:** Wenn Sie zuvor eine der oben genannten Methoden verwendet haben, haben Sie auf die AAM [!UICONTROL Data Source] mit der [!UICONTROL Data Source] ID (AKA die &quot;DPID&quot;) verwiesen. Bei der Aktualisierung auf müssen Sie [!DNL setCustomerIDs]stattdessen das &quot; [!UICONTROL Data Source][!UICONTROL Integration Code]&quot;der AAM verwenden. Es verweist immer noch auf das gleiche [!UICONTROL Data Source] aber ist nur ein anderer Bezeichner. Dies wird im folgenden Video gezeigt.

>[!VIDEO](https://video.tv.adobe.com/v/23873/?quality=12)

In den folgenden Abschnitten werden Listen und Empfehlungen für die Aktualisierung auf DIL 8.0 basierend auf Ihrer Implementierungsmethode aufgeführt:

## Aktualisieren auf DIL 8.0 in Adobe Experience Platform Launch {#updating-to-dil-in-experience-platform-launch}

Grundlegende Schritte für die Aktualisierung auf DIL 8.0

1. Wenn Sie DIL vor der Aktualisierung vor Version 8.0 verwenden, gehen Sie zur DIL-Konfiguration in der AAM-Erweiterung und notieren Sie sich die von Ihnen verwendeten erweiterten Optionen (die in einem nachfolgenden Schritt verwendet werden sollen)
1. Aktualisieren Sie Ihre AAM-Erweiterung auf Version 8.0 oder höher.
1. Überprüfen Sie, ob Ihre Experience Cloud-ID-Diensterweiterung Version 3.3.0 oder höher ist.
1. Aktivieren Sie für alle nicht mehr unterstützten Methoden/Elemente (z. B. &quot;[!DNL disableIDSyncs]&quot;), die sich in Ihrer Erweiterung vor 8.0 AAM oder im benutzerdefinierten Code für die DIL befanden, die ECID-Methoden in der ECID-Erweiterung.

   1. (DIL) disableDestinationPublishingIframe -> (ECID) disableIdSyncs
   1. (DIL) disableIDSyncs -> (ECID) disableIdSyncs
   1. (DIL) iframeAkamaiHTTPS -> (ECID) dSyncSSLUseAkamai
   1. (DIL) displayedId -> (ECID) setCustomerIDs

1. Änderungen veröffentlichen

>[!VIDEO](https://video.tv.adobe.com/v/23874/?quality=12)

## Aktualisieren auf DIL 8.0 in Adobe DTM {#updating-to-dil-in-adobe-dtm}

1. Aktualisieren Sie Ihr AAM auf Version 8.0 oder höher. Diese Versionseinstellung befindet sich im Abschnitt &quot;Allgemein&quot;des AAM.
1. Notieren Sie alle nicht mehr unterstützten Methoden/Elemente (z. B. &quot;disableIDSyncs&quot;), die im benutzerspezifischen Code des Tools vor 8.0 AAM enthalten waren, diese (damit Sie sie dem ECID-Tool hinzufügen können) und entfernen Sie sie dann [!DNL DIL code] im AAM.
1. Aktualisieren Sie Ihre Experience Cloud-ID-Diensterweiterung auf Version 3.3.0 oder höher.
1. hinzufügen Sie die erweiterten Optionen zum ECID-Tool, die Sie aus dem benutzerdefinierten Code des AAM entfernt haben.
1. Änderungen veröffentlichen

## Aktualisierung auf DIL 8.0 ohne Adobe Tag Management Solution {#additional-resources}

Wenn Sie Ihren Code direkt auf der Seite aktualisieren, können Sie ältere Elemente einfach durch neue Elemente ersetzen, es sei denn, Sie müssen Methoden/Elemente von der DIL in die ECID verschieben, wie oben beschrieben. In diesem Fall ersetzen Sie einfach die alte Methode/das alte Element am Speicherort der DIL durch die ECID-Methode/das Element am ECID-Speicherort.

Dasselbe gilt auch für Tagmanager ohne Adobe. Ersetzen Sie die alten Versionen dieser Tag-Management-Lösung durch den neuen Code, wie in den folgenden Schritten beschrieben.

1. Aktualisieren Sie Ihre DIL-Bibliothek auf die neueste Version (8.0 oder höher) - Sie benötigen den neuesten DIL-Code von Adobe Consulting oder der Adobe Customer Care, da er derzeit nicht an einem öffentlichen Speicherort verfügbar ist. Ersetzen Sie dann einfach den alten DIL-Bibliothekscode durch den neuen DIL-Bibliothekscode und fahren Sie mit dem nächsten Schritt fort (halten Sie jetzt nicht auf oder Sie werden Probleme ausführen, ha).
1. Installieren [!DNL ECID Service] oder aktualisieren Sie Ihre vorhandene Version auf 3.3.0 oder höher. Sie können die neueste Version des Experience Cloud ID Service [von unserer GitHub-Seite](https://github.com/Adobe-Marketing-Cloud/id-service/releases)herunterladen. Wenn Sie dabei Hilfe benötigen, lesen Sie die [Dokumentation](https://marketing.adobe.com/resources/help/de_DE/mcvid/) oder sprechen Sie mit einem Adobe Consultant.

1. Vergewissern Sie sich, dass alle nicht mehr unterstützten Methoden oder Elemente, die sich in Ihrem benutzerspezifischen Code für die DIL befinden, in die ECID-Methoden verschoben werden:

   1. (DIL) disableDestinationPublishingIframe -> (ECID) disableIdSyncs

      [Dokumentation](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-disableidsync.html)

   1. (DIL) disableIDSyncs -> (ECID) disableIdSyncs

      [Dokumentation](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-disableidsync.html)

   1. (DIL) iframeAkamaiHTTPS -> (ECID) idSyncSSLUseAkamai

      [Dokumentation](https://marketing.adobe.com/resources/help/en_US/aam/r_dil_create.html)

   1. (DIL) displayedId -> (ECID) setCustomerIDs

      [Dokumentation](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid_setcustomerids.html)