---
title: Verwenden von Look-Alike-Modellen zum Erweitern des ausverkauften Bestands aus Ihren Erstanbieter-Daten
description: In diesem Lernprogramm gehen wir durch die Schritte, die Sie unternehmen sollten, um Look-Alike-Modelle einzurichten und zu verwenden, damit Sie neue Look-Alike-Audiencen erstellen und diese als Erweiterung Ihres Konvertierungssegments verkaufen können.
feature: algorithmic models
topics: null
audience: all
activity: use
doc-type: feature video
team: Technical Marketing
kt: 1688
translation-type: tm+mt
source-git-commit: dfd549508cc223714bdb07ac6fd2aa31e6ca5586
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 0%

---


# Verwenden von Look-Alike [!UICONTROL Models] zum Erweitern des ausverkauften Bestands aus Ihren [!UICONTROL First Party] Daten {#using-look-alike-models-to-extend-sold-out-inventory-from-your-st-party-data}

In diesem Tutorial gehen wir durch die Schritte, die Sie unternehmen sollten, um Look-Alike einzurichten und zu verwenden [!UICONTROL Models], sodass Sie neue Look-Alike-Audiencen erstellen und sie als Erweiterung Ihrer Konvertierung verkaufen können [!UICONTROL segment].

## Verwendungsfalldetails {#use-case-details}

Sie sind Herausgeber von Inhalten. Wenn Sie bereits Lagerbestand für Konverter auf Ihrer Site ausverkauft haben, können Sie denken, dass Ihre Gelegenheit dort endet. Geben Sie AAM Look-Alike ein [!UICONTROL Models]. Mit dieser Funktion können Sie den ausverkauften Bestand weiter ausdehnen und auch Audiencen von Personen verkaufen, die vielleicht noch nicht konvertiert haben, aber wie Menschen aussehen/handeln, die konvertiert haben. Diese Audience [!UICONTROL segment] würde in der Regel für weniger als die eigentlichen Konverter verkauft, ermöglicht Ihnen jedoch, Ihren Gewinn zu erhöhen, indem Sie eine zusätzliche Audience für Werbetreibende bereitstellen, die Anzeigen auf Ihrer Site platzieren möchten. Der zusätzliche Vorteil dieses Anwendungsfalls besteht darin, dass es Sie nicht kostet, dieses Modell auf Ihren Erstanbieterdaten auszuführen.

Die Schritte in diesem Lernprogramm lauten wie folgt:

1. Identifizieren/Erstellen Sie einen idealen Benutzer (Konversion) [!UICONTROL trait] oder [!UICONTROL segment]
1. Erstellen Sie eine [!UICONTROL model] mit dieser Konversion [!UICONTROL trait]/[!UICONTROL segment] als Basiselement
1. Wählen Sie [!UICONTROL First party] die Datenquelle(n) in der [!UICONTROL model] und führen Sie die [!UICONTROL model]
1. Erstellen Sie einen Algorithmus [!UICONTROL Trait] aus den [!UICONTROL model] Ergebnissen und fügen Sie ihn [!UICONTROL trait] einem [!UICONTROL segment]
1. Angebot der [!UICONTROL segment] an interessierte Werbetreibende zur Erweiterung des Umrechnungsverkaufs [!UICONTROL segment]

## Identifizieren/Erstellen Sie einen idealen Benutzer (Konversion) [!UICONTROL trait] oder [!UICONTROL segment] {#identify-create-an-ideal-user-conversion-trait-or-segment}

Was versuchen Sie, Leute zu bewegen, auf Ihrer Site zu tun? Was ist Ihr Umrechnungs-Ereignis? Natürlich gibt es viele verschiedene Antworten auf diese Frage, je nach Site-Typ/Vertikal und Ihren organisatorischen Zielen. Auf jeden Fall ist es in AAM üblich, einen [!UICONTROL trait] für Besucher zu erstellen, die diese Kriterien erfüllt haben.

In diesem Fall wird dies bereits angenommen, weil Sie den Bestand für Personen, die Konverter sind, ausverkauft haben. Für die Zwecke dieses Tutorials ist es jedoch gut, ihn als Referenz für den Rest des Anwendungsfalls zu diskutieren.

Wenn Sie Ereignis zum Erstellen verwenden, [!UICONTROL traits]müssen Sie außerdem ein wichtiges Thema beachten, damit Sie nicht mehr Benutzer sammeln, als Sie sollten, in die [!UICONTROL trait]. Sehen Sie sich das folgende Video für die große Offenbarung an. :)

>[!VIDEO](https://video.tv.adobe.com/v/23431/?quality=12)

**HINWEIS:** In dem oben gezeigten Video wird davon ausgegangen, dass Sie über Adobe Analytics verfügen. Das ist offensichtlich nicht der Fall. Wenn Sie Google Analytics (GA) haben, haben wir ein Modul, mit dem Sie Daten an AAM senden können (siehe [Dokumentation](https://marketing.adobe.com/resources/help/en_US/aam/dil-google-universal-analytics.html)), und wenn Ihre Konversions-Aktivität auf Ihrer Site von GA an AAM gesendet wird, können Sie Ihre Konversionseigenschaft daraus erstellen. Wenn Sie über eine andere Analyselösung (oder keine Analyselösung) verfügen, können Sie trotzdem Daten über unseren DIL-Code und die `submit` Funktion an AAM senden. (siehe [Dokumentation](https://marketing.adobe.com/resources/help/en_US/aam/c_dil.html)). Erstellen Sie dann erneut die Konversionseigenschaft basierend auf den Daten, die gesendet werden, wenn die Konvertierungsfunktion auf der Site ausgeführt wird.

## Erstellen eines Look-Alike [!UICONTROL Model] aus [!UICONTROL First Party] Daten {#creating-a-look-alike-model-from-first-party-data}

In diesem Schritt werden wir eine [!UICONTROL First Party] Look-Alike erstellen [!UICONTROL Model]. Das bedeutet, dass wir nicht nur eine [!UICONTROL first party] Konversion [!UICONTROL trait]/[!UICONTROL segment] für unsere Basis [!UICONTROL trait]/[!UICONTROL segment] (das wäre ohnehin normal) verwenden werden, sondern auch nur in den Pool von [!UICONTROL models] [!UICONTROL first party] Daten für mehr Leute, die wie die Konverter aussehen. Wir werden uns keine Daten ansehen [!UICONTROL second party] oder [!UICONTROL third party] nicht.

In diesem Fall ist dies wichtig, weil wir versuchen, eine Reihe [!UICONTROL segment] von Benutzern auf unserer Site zu erstellen, die wie Konverter aussehen, aber noch nicht konvertiert wurden, sodass wir diese Aussehen-wie- [!UICONTROL segment] zu interessierten Werbetreibenden verkaufen können.

>[!VIDEO](https://video.tv.adobe.com/v/23504/?quality-12)

## Erstellen eines Algorithmus [!UICONTROL Trait] {#creating-an-algorithmic-trait}

Als Nächstes müssen wir einen Algorithmus erstellen, [!UICONTROL Trait]damit die Ergebnisse des [!UICONTROL model] Berichts verwendet werden können. Ohne eine [!UICONTROL trait]zu erstellen, ist die [!UICONTROL model] nutzlos. Nach der [!UICONTROL model] Ausführung sollten Sie in den [!UICONTROL trait] Dialog gehen und einen Algorithmus erstellen [!UICONTROL Trait]. Im folgenden Video werden einige Tipps gezeigt.

>[!VIDEO](https://video.tv.adobe.com/v/23523/?quality=12)

## Algorithmus [!UICONTROL Segment] für Werbetreibende anbieten {#offering-the-algorithmic-segment-to-advertisers}

Nachdem Sie einen Algorithmus erstellt haben, [!UICONTROL Trait]können Sie einen neuen erstellen, [!UICONTROL segment] um ihn einzufügen, sodass Sie die Daten aktivieren können (Sie können einen [!UICONTROL trait]nicht aktivieren, sondern einen neuen erstellen,[!UICONTROL trait] mit dem Algorithmus [!UICONTROL segment] darin, sodass Sie den [!UICONTROL Trait] [!UICONTROL segment]aktivieren (verwenden) können.

Nachdem Sie eine Reihe [!UICONTROL segment] von [!UICONTROL first party] Besuchern erstellt haben, die im Aussehen gleich hoch abgeschnitten haben [!UICONTROL model] (d. h. diejenigen, die wie Konverter aussehen, aber noch nicht konvertiert wurden), können Sie dies [!UICONTROL segment] an Werbetreibende auf Ihrer Site Angebot haben, auch nachdem Sie Ihren gesamten Bestand an tatsächlichen Konvertern auf Ihrer Site ausverkauft haben. Dies ist eine großartige Möglichkeit, diese Audience zu erweitern und weitere Umsätze durch Verwendung von Look-Alike [!UICONTROL Models] in Audience Manager zu sehen.
