---
title: IAB TCF 2.0-Unterstützung für Audience Manager
description: Adobe bietet Ihnen die Möglichkeit, die Datenschutzentscheidungen Ihrer Benutzer über die Opt-in-Funktion und über das Audience Manager-Plug-in zur Unterstützung von IAB Transparency and Consent Framework 2.0 (TCF 2.0) zu verwalten und zu kommunizieren. Dieser Artikel arbeitet mit der Dokumentation zusammen, um Ihnen zu helfen, das Audience Manager-Plug-in für die IAB-TCF zu verstehen und zu verstehen, wie es mit dem Opt-in-Objekt der Adobe und Ihrem Consent Management Provider (CMP) funktioniert.
feature: "Data Governance & Privacy"
activity: implement
doc-type: technical video
team: Technical Marketing
thumbnail: 26434.jpg
kt: 5027
role: Developer, Data Engineer, Architect
level: Experienced
exl-id: 04b4e786-0457-4dcc-bcf9-a79eda67bb2e
translation-type: tm+mt
source-git-commit: 256edb05f68221550cae2ef7edaa70953513e1d4
workflow-type: tm+mt
source-wordcount: '1126'
ht-degree: 0%

---

# IAB TCF 2.0-Unterstützung in Audience Manager {#iab-tcf-support-in-audience-manager}

Adobe bietet Ihnen die Möglichkeit, die Datenschutzentscheidungen Ihrer Benutzer über die Opt-in-Funktion und über das Audience Manager-Plug-in zur Unterstützung von IAB Transparency and Consent Framework 2.0 (TCF 2.0) zu verwalten und zu kommunizieren. Dieser Artikel arbeitet mit der Dokumentation zusammen, um Ihnen zu helfen, das Audience Manager-Plug-in für die IAB-TCF zu verstehen und zu verstehen, wie es mit dem Opt-in-Objekt der Adobe und Ihrem Consent Management Provider (CMP) funktioniert. Weitere Informationen zum IAB finden Sie auf der Website unter [https://www.iabeurope.eu/](https://www.iabeurope.eu/).

## Erster Schritt: ECID-Teilnahme{#first-step-understand-ecid-s-opt-in}

Um zu verstehen, wie Sie mit der IAB-TCF arbeiten, müssen Sie zunächst die [!DNL Opt-in]-Funktionalität verstehen, die Teil der ECID-Bibliothek (Experience Cloud ID Service) ist. Wenn Sie mit der Funktionsweise von Opt-in nicht vertraut sind, lesen Sie [diesen hilfreichen Artikel](https://docs.adobe.com/content/help/en/core-services-learn/tutorials/id-service/use-opt-in-to-control-experience-cloud-activities-based-on-user-consent.html) zuerst. Sie sollten auch die Einstiegsoption [Dokumentation](https://docs.adobe.com/content/help/de-DE/id-service/using/implementation/opt-in-service/optin-overview.html) lesen. Sobald Sie diese Ressourcen durchlaufen haben, kehren Sie zu dieser Seite zurück und fahren Sie fort.

## Das Audience Manager-Plug-In für IAB TCF {#the-audience-manager-plug-in-for-iab-tcf}

Jetzt, da Sie mindestens ein grundlegendes Verständnis haben, wie der Opt-in-Dienst funktioniert, kann Audience Manager [!DNL IAB Transparency and Consent Framework (TCF)]-Unterstützung auf ihn übertragen, was über ein Plug-in in das Opt-in-Objekt erfolgt.

Das Audience Manager-Plug-in für die IAB TCF erweitert die Funktionalität von Opt-in und ermöglicht AAM Kunden, Entscheidungen zum Schutz der Privatsphäre der Nutzer gemäß IAB TCF zu bewerten, zu berücksichtigen und an nachgeschaltete Partner weiterzuleiten. Es bietet einen Standard für Datencontroller (d. h. Sie als Adobe-Kunde) und Anbieter (DMPs, DSP, SSPs, Anzeigenserver usw.) kann verwenden, um die Zustimmung im gesamten Zustimmungsgebiet zu verstehen.

## Aktivieren der IAB-TCF {#enabling-iab-tcf}

Die Aktivierung des Audience Manager-Plug-ins für die IAB TCF ist bei Verwendung von Adobe Experience Platform Launch einfach, da es sich um ein einfaches Kontrollkästchen handelt, wie im kurzen Video unten gezeigt:

>[!VIDEO](https://video.tv.adobe.com/v/26433/?quality=12)

Wenn Sie Launch nicht verwenden, können Sie `isIabContext=true` auch verwenden, um es zu aktivieren, wenn Sie den Experience Cloud-Besucher instanziieren. Dadurch wird der IAB-TCF-Fluss initiiert, d. h. es wird ein weiterer Schritt zur Einwilligungserfassung hinzugefügt, wobei die IAB-TCF zur Abfrage für die IAB-TC-Zeichenfolge verwendet wird, und sie wird an Opt-in zurückgegeben, das wiederum mit den Experience Cloud-Lösungen kommuniziert.

## IAB-TC-Zeichenfolge {#iab-tcf-consent-string}

Eine der Standards, die IAB bietet, ist eine &quot;Zustimmungszeichenfolge&quot; (auch bekannt als &quot;DaisyBit&quot;), die wirklich zwei Listen zusammengesetzt ist:

1. Zweck: **Was** wird die Zustimmung erteilt?
1. Anbieter: **Wem wird die Zustimmung erteilt?**

### Zweck {#purposes}

Mit dem IAB TCF 2.0 gibt es zehn &quot;Zwecke&quot;, für die eine Zustimmung eingeholt werden kann (was Anbieter mit den Daten des Besuchers tun können). Adobe Audience Manager benötigt nicht alle zehn, sondern nur die Zustimmung zu folgenden Zwecken zusätzlich zur Zustimmung des Anbieters:

* **Zweck 1:** Speichern und/oder Zugreifen auf einem Gerät;
* **Zweck 10:** Entwicklung und Verbesserung von Produkten;
* **Sonderzweck 1:** Sicherstellen der Sicherheit, Verhinderung von Betrug und Debuggen.

Dies ist der erste Teil der IAB-TC-Zeichenfolge und wird nur als 1 s und 0 s aufgezeichnet, wobei angegeben wird, ob dieser Zweck/diese Aktivität genehmigt wurde oder nicht.

>[!NOTE]
>
>Gemäß IAB-Bestimmungen wird dem Sonderzweck 1 (Sicherheit, Betrugsbekämpfung und Debugging sicherstellen) immer zugestimmt, und die Benutzer können keine Einwände dagegen erheben.

### Anbieter {#vendors}

Ein weiterer Teil der IAB-TC-Zeichenfolge ist eine lange Liste von mehreren hundert Anbietern, sodass den Besuchern eine Liste von Anbietern angezeigt werden kann, die Tags auf der Site haben und entscheiden können, welche Anbieter verwendet werden sollen. Anbieter behalten ihre Position an der Liste bei. Die Händlernummer von Adobe Audience Manager auf dieser Liste ist beispielsweise 565. Wenn diese Nummer in der Liste eine &quot;1&quot;hat, kann der Audience Manager die genehmigten Aufgaben von der Vorderseite der Liste aus durchführen. Wenn AAM Spot den Wert &quot;0&quot;hat, kann er nichts mit den Daten machen.

**Damit Audience Manager eine Benutzeroberfläche bereitstellen können, über die die IAB-TCF zur Auswahl dieser Zwecke und Anbieter oder zur Genehmigung/Ablehnung aller Aktivitäten verwendet werden kann, müssen Sie einen CMP-Partner verwenden, der bei IAB TCF registriert ist oder einen Partner aufbaut, der IAB TCF unterstützt und bei der IAB TCF registriert ist.**

## Teilnahme: Übersetzung zwischen IAB und Adobe Solutions {#opt-in-translating-between-iab-and-adobe-solutions}

Einer der Vorteile der Verwendung der IAB-TCF besteht darin, dass die oben aufgeführten Standardziele dem Endbenutzer wahrscheinlich mehr eine Vorstellung davon geben, was er genehmigt, als eine Liste von Adoben-Lösungen. Endbenutzer wissen möglicherweise nicht, was es bedeutet, Audience Manager zu genehmigen oder [!DNL Target], aber &quot;Store and/or access information on a device&quot; oder &quot;Entwickeln und verbessern&quot; ist wahrscheinlich einfacher für sie zu verstehen und zu akzeptieren.

Damit der Audience Manager genehmigt werden kann (d. h. um die Übersetzung von IAB-Zwecken für die Teilnahme an der AAM mit &quot;Ja&quot; abstimmen zu können), müssen die oben genannten Zwecke 1 und 10 vom Endnutzer genehmigt werden. Wenn eine dieser beiden Optionen nicht genehmigt ist oder ein Anbieter nicht genehmigt wurde, führen AAM keine Pixelfeuerlöse aus oder setzen keine Cookies. Es ist auch gut zu wissen, dass viele Kunden sich einfach entscheiden, dem Endbenutzer eine &quot;alles oder nichts&quot;-Benutzeroberfläche zur Verfügung zu stellen, die natürlich die Verwendung von Audience Manager (und anderen Experience Cloud-Lösungen) erlauben oder ablehnen würde.

Es gibt einige großartige Informationen in der [Dokumentation](https://marketing.adobe.com/resources/help/en_US/aam/aam-iab-plugin.html) darüber, wie das Audience Manager-Plug-In für die IAB-TCF-Flussfunktion sowohl für Publisher- als auch für Advertiser-Anwendungsfälle angewendet wird.

## IAB: Zustimmung nach unten senden {#iab-sending-consent-downstream}

Wenn das Audience Manager-Plug-in für die IAB-TCF verwendet wird, werden die Benutzereinwilligungsentscheidungen auch an die ID-Syncs auf Plattformebene (Drittanbieter) für Partner gesendet, die auf der Global Vendor-Liste vertreten sind, sodass der Partner über die Benutzereinwilligungsinformationen verfügt und auch darauf reagieren kann. Diese Informationen werden in zwei Variablen gesendet:

* gdpr = 1
* gdpr_approval = [kodierte Zustimmungszeichenfolge]

Der Vorbehalt besteht darin, dass Audience Manager, wenn sich der Nutzer im IAB-Kontext befindet und keine Einwilligung gibt (oder keine negative Einwilligung gibt), die IAB-TC-Zeichenfolge überhaupt nicht erfassen kann und daher die Aufrufe fallen lassen. In diesem Fall also... keine Zustimmung nachgelagert.

## Demo{#demo}

Im folgenden Video sehen Sie, wie Cookies und Beacons von ECID und Lösungen von der Auswahl der IAB-Benutzer beeinflusst werden.

>[!VIDEO](https://video.tv.adobe.com/v/26434/?quality=12)

Ausführlichere Informationen zum Audience Manager-Plug-In für IAB TCF 2.0, einschließlich der Implementierung und des Testens, Anwendungsfälle und Arbeitsablaufs, finden Sie in der [Dokumentation](https://docs.adobe.com/content/help/en/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html).
