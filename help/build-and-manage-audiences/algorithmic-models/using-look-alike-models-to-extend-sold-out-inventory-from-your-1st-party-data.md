---
title: Verwenden von Look-Alike-Modellen zum Erweitern des ausverkauften Bestands aus Ihren Erstanbieter-Daten
description: In diesem Lernprogramm gehen wir durch die Schritte, die Sie unternehmen sollten, um Look-Alike-Modelle einzurichten und zu verwenden, damit Sie neue Look-Alike-Audiencen erstellen und diese als Erweiterung Ihres Konvertierungssegments verkaufen können.
feature: Algorithmische Modelle
topics: null
audience: all
activity: use
doc-type: feature video
team: Technical Marketing
thumbnail: 23523.jpg
kt: 1688
translation-type: tm+mt
source-git-commit: ba76f9437e5d8f0495e4f2dfafb90cbf2da6454f
workflow-type: tm+mt
source-wordcount: '827'
ht-degree: 0%

---


# Verwenden von Look-Alike [!UICONTROL Models] zum Erweitern des ausverkauften Bestands aus Ihren [!UICONTROL First Party]-Daten {#using-look-alike-models-to-extend-sold-out-inventory-from-your-st-party-data}

In diesem Lernprogramm gehen wir durch die Schritte, die Sie unternehmen sollten, um Look-Alike [!UICONTROL Models] einzurichten und zu verwenden, sodass Sie neue Look-like-Audiencen erstellen und diese als Erweiterung Ihrer Umrechnung [!UICONTROL segment] verkaufen können.

## Verwendungsfalldetails {#use-case-details}

Sie sind Herausgeber von Inhalten. Wenn Sie bereits Lagerbestand für Konverter auf Ihrer Site ausverkauft haben, können Sie denken, dass Ihre Gelegenheit dort endet. Geben Sie AAM Look-Alike [!UICONTROL Models] ein. Mit dieser Funktion können Sie den ausverkauften Bestand weiter ausdehnen und auch Audiencen von Personen verkaufen, die vielleicht noch nicht konvertiert haben, aber wie Menschen aussehen/handeln, die konvertiert haben. Diese Audience [!UICONTROL segment] würde in der Regel für weniger als die eigentlichen Konverter verkauft, ermöglicht Ihnen jedoch, Ihren Gewinn zu erhöhen, indem Sie eine zusätzliche Audience für Werbetreibende bereitstellen, die Anzeigen auf Ihrer Site platzieren möchten. Der zusätzliche Vorteil dieses Anwendungsfalls besteht darin, dass es Sie nicht kostet, dieses Modell auf Ihren Erstanbieterdaten auszuführen.

Die Schritte in diesem Lernprogramm lauten wie folgt:

1. Identifizieren/Erstellen eines idealen Benutzers (Konversion) [!UICONTROL trait] oder [!UICONTROL segment]
1. Erstellen Sie ein [!UICONTROL model] mit dieser Konversion [!UICONTROL trait]/[!UICONTROL segment] als Basiselement
1. Wählen Sie [!UICONTROL First party] die Datenquelle(n) in [!UICONTROL model] und führen Sie [!UICONTROL model] aus.
1. Erstellen Sie einen Algorithmus [!UICONTROL Trait] aus den [!UICONTROL model] Ergebnissen und fügen Sie das [!UICONTROL trait] zu einem [!UICONTROL segment] hinzu.
1. Angebot Sie die [!UICONTROL segment] an interessierte Advertisers, um die Umrechnung [!UICONTROL segment]-Verkäufe zu verlängern.

## Identifizieren/Erstellen Sie einen idealen Benutzer (Konversion) [!UICONTROL trait] oder [!UICONTROL segment] {#identify-create-an-ideal-user-conversion-trait-or-segment}

Was versuchen Sie, Leute zu bewegen, auf Ihrer Site zu tun? Was ist Ihr Umrechnungs-Ereignis? Natürlich gibt es viele verschiedene Antworten auf diese Frage, je nach Site-Typ/Vertikal und Ihren organisatorischen Zielen. In jedem Fall ist es in AAM üblich, ein [!UICONTROL trait] für Besucher zu erstellen, die diese Kriterien erfüllt haben.

In diesem Fall wird dies bereits angenommen, weil Sie den Bestand für Personen, die Konverter sind, ausverkauft haben. Für die Zwecke dieses Tutorials ist es jedoch gut, ihn als Referenz für den Rest des Anwendungsfalls zu diskutieren.

Wenn Sie Ereignis verwenden, um [!UICONTROL traits] zu erstellen, müssen Sie außerdem ein Hauptmerkmal beachten, damit Sie nicht mehr Benutzer sammeln, als Sie in [!UICONTROL trait] aufnehmen sollten. Sehen Sie sich das folgende Video für die große Offenbarung an. :)

>[!VIDEO](https://video.tv.adobe.com/v/23431/?quality=12)

**HINWEIS:** Im obigen Video wird bei dem gezeigten Beispiel davon ausgegangen, dass Sie über Adobe Analytics verfügen. Das ist offensichtlich nicht der Fall. Wenn Sie Google Analytics (GA) haben, haben wir ein Modul, mit dem Sie Daten an AAM senden können (siehe [Dokumentation](https://marketing.adobe.com/resources/help/en_US/aam/dil-google-universal-analytics.html)). Wenn Ihre Konversions-Aktivität auf Ihrer Site von GA an AAM gesendet wird, können Sie Ihre Konvertierungseigenschaften daraus erstellen. Wenn Sie über eine andere Analyselösung (oder keine Analyselösung) verfügen, können Sie trotzdem Daten über unseren DIL-Code und die `submit`-Funktion usw. an AAM senden. (siehe [Dokumentation](https://marketing.adobe.com/resources/help/en_US/aam/c_dil.html)). Erstellen Sie dann erneut die Konversionseigenschaft basierend auf den Daten, die gesendet werden, wenn die Konvertierungsfunktion auf der Site ausgeführt wird.

## Erstellen eines Look-Alike [!UICONTROL Model] aus [!UICONTROL First Party] Data {#creating-a-look-alike-model-from-first-party-data}

In diesem Schritt werden wir ein [!UICONTROL First Party] Look-Alike [!UICONTROL Model] erstellen. Das bedeutet, dass wir nicht nur eine [!UICONTROL first party] Konvertierung [!UICONTROL trait]/[!UICONTROL segment] für unsere Basis [!UICONTROL trait]/[!UICONTROL segment] verwenden werden (dies wäre bei den meisten [!UICONTROL models] trotzdem normal), sondern wir werden auch nur in den Pool von [!UICONTROL first party] Daten für weitere Personen suchen, die wie die Konverter aussehen. Wir werden keine [!UICONTROL second party]- oder [!UICONTROL third party]-Daten betrachten.

In diesem Anwendungsfall ist dies wichtig, da wir versuchen, eine [!UICONTROL segment] von Benutzern auf unserer Site zu erstellen, die wie Konverter aussehen, aber noch nicht konvertiert wurden, sodass wir dieses Erscheinungsbild [!UICONTROL segment] interessierten Anbietern verkaufen können.

>[!VIDEO](https://video.tv.adobe.com/v/23504/?quality-12)

## Erstellen eines Algorithmus [!UICONTROL Trait] {#creating-an-algorithmic-trait}

Als Nächstes müssen wir einen Algorithmus [!UICONTROL Trait] erstellen, damit die Ergebnisse von [!UICONTROL model] verwendet werden können. Ohne Erstellen eines [!UICONTROL trait] ist [!UICONTROL model] nutzlos. Nachdem [!UICONTROL model] ausgeführt wird, sollten Sie in das [!UICONTROL trait]-Dialogfeld gehen und eine algorithmische [!UICONTROL Trait] erstellen. Im folgenden Video werden einige Tipps gezeigt.

>[!VIDEO](https://video.tv.adobe.com/v/23523/?quality=12)

## Angebot des Algorithmus [!UICONTROL Segment] an Werbekunden {#offering-the-algorithmic-segment-to-advertisers}

Nachdem Sie ein Algorithmus [!UICONTROL Trait] erstellt haben, können Sie ein neues [!UICONTROL segment] erstellen, um es einzufügen, sodass Sie die Daten aktivieren können (Sie können kein [!UICONTROL trait] aktivieren, sondern stattdessen ein neues [!UICONTROL trait] [!UICONTROL segment] [!UICONTROL Trait] mit dem Algorithmus  erstellen, damit Sie das [!UICONTROL segment] aktivieren (verwenden) können.

Nachdem Sie eine [!UICONTROL segment] von [!UICONTROL first party] Besuchern erstellt haben, die im Look-Alike [!UICONTROL model] einen hohen Wert erreicht haben (d. h. die wie Konverter aussehen, aber noch nicht konvertiert wurden), können Sie dieses [!UICONTROL segment] an Werbekunden auf Ihrer Site Angebot haben, auch nachdem Sie Ihren gesamten Bestand an tatsächlichen Konvertern auf Ihrer Site ausverkauft haben. Dies ist eine großartige Möglichkeit, diese Audience zu erweitern und weitere Umsätze durch Verwendung von Look-Alike [!UICONTROL Models] in Audience Manager zu sehen.
