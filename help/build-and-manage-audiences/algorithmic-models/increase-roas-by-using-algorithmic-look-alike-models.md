---
title: Erhöhung der ROAS durch Verwendung algorithmischer (Look-Alike) Modelle im Audience Manager
description: Die wahre Stärke des Look-alike Modelings von Audience Manager liegt darin, dass Sie Ihre Ausgangsergebnisse gegenüber einer hochwertigen, ganz neuen Benutzergruppe aus 2nd- und 3rd-Party-Datenquellen erweitern möchten. In diesem Lernprogramm erfahren Sie, wie Sie anhand dieser Daten ein Modell erstellen.
feature: Algorithmische Modelle
topics: null
activity: use
doc-type: feature video
team: Technical Marketing
thumbnail: 25188.jpg
kt: 1849
role: '"Business Practitioner, Entwickler, Dateningenieur, Architekt, Data Architect, Administrator, Leader"'
level: Zwischenschaltung
translation-type: tm+mt
source-git-commit: a7dc335e75697a7b1720eccdadbb9605fdeda798
workflow-type: tm+mt
source-wordcount: '873'
ht-degree: 0%

---


# ROAS durch Verwendung von Algorithmus (Look-Alike) [!UICONTROL Models] in Audience Manager {#increase-roas-by-using-algorithmic-look-alike-models-in-audience-manager} erhöhen

Die wahre Stärke von Audience Managers Look-alike [!UICONTROL Modeling] kommt, wenn Sie versuchen, Ihre Baseline-Audience gegen eine Qualität zu erweitern, ganz neue Benutzergruppe von [!UICONTROL second party] und [!UICONTROL third party] [!UICONTROL data sources]. In diesem Lernprogramm erfahren Sie, welche Schritte zum Erstellen eines [!UICONTROL model] aus diesen Daten erforderlich sind.

## [!UICONTROL Second Party]- oder [!UICONTROL Third Party]-Datenströme aus dem Audience Marketplace {#enable-2nd-or-3rd-party-data-streams-from-the-audience-marketplace} aktivieren

Um [!UICONTROL second party]- und [!UICONTROL third party]-Daten in einem Alias [!UICONTROL model] zu verwenden, müssen wir diese Daten zunächst in Ihrer Audience Manager-Oberfläche aktivieren. Adobe verfügt über eine große Anzahl von [!UICONTROL second party]- und [!UICONTROL third party]-Datenanbietern, aus denen Sie auswählen können. Diese sind für Sie in einer Self-Service-Schnittstelle in AAM, über das Audience Marketplace verfügbar. Navigieren Sie zum Audience Marketplace und durchsuchen Sie die Möglichkeiten. Das folgende Video zeigt Ihnen, wie Sie dies tun können, einschließlich der Aktivierung kostenloser Streams, die Sie vor dem Kauf ausprobieren, sodass Sie die Daten einbinden können, die für Ihr Unternehmen am nützlichsten sind, bevor Sie sich zu den Preisen des Datenanbieters verpflichten.

Um Ihnen bei der Suche und Entscheidung, welcher Datenanbieter verwendet werden soll, zu helfen, ist eine großartige Ressource die [[!DNL Adobe Audience Finder]](https://www.adobe-audience-finder.com/).

>[!VIDEO](https://video.tv.adobe.com/v/25188/?quality=12)

## Identifizieren/Erstellen Sie einen idealen Benutzer (Konversion) [!UICONTROL trait] oder [!UICONTROL segment] {#identify-create-an-ideal-user-conversion-trait-or-segment}

Was versuchen Sie, Leute zu bewegen, auf Ihrer Site zu tun? Was ist Ihr Umrechnungs-Ereignis? Natürlich gibt es viele verschiedene Antworten auf diese Frage, je nach Site-Typ/Vertikal und Ihren organisatorischen Zielen. In jedem Fall ist es in AAM üblich, ein [!UICONTROL trait] für Besucher zu erstellen, die diese Kriterien erfüllt haben.

In dem folgenden Video werde ich Ihnen zeigen, wie Sie eine Konvertierung [!UICONTROL trait] erstellen, die Sie haben möchten, während Sie diese Übung fortsetzen und ein Look-like [!UICONTROL model] erstellen.

Wenn Sie Adobe Analytics-Ereignis verwenden, um [!UICONTROL traits] zu erstellen, müssen Sie außerdem ein Hauptmerkmal beachten, damit Sie nicht mehr Benutzer sammeln, als Sie in [!UICONTROL trait] aufnehmen sollten. Sehen Sie sich das folgende Video für die große Offenbarung an. :)

>[!VIDEO](https://video.tv.adobe.com/v/23431/?quality=12)

**HINWEIS:** Im obigen Video wird bei dem gezeigten Beispiel davon ausgegangen, dass Sie über Adobe Analytics verfügen. Das ist offensichtlich nicht der Fall. Wenn Sie Google Analytics (GA) haben, haben wir ein Modul, mit dem Sie Daten an AAM senden können (siehe [Dokumentation](https://marketing.adobe.com/resources/help/en_US/aam/dil-google-universal-analytics.html)). Wenn Ihre Konversions-Aktivität auf Ihrer Site von GA an AAM gesendet wird, können Sie Ihre Konvertierung [!UICONTROL trait] daraus erstellen. Wenn Sie über eine andere Analyselösung (oder keine Analyselösung) verfügen, können Sie trotzdem Daten über unseren DIL-Code und die `submit`-Funktion usw. an AAM senden. (siehe [Dokumentation](https://marketing.adobe.com/resources/help/en_US/aam/c_dil.html)). Erstellen Sie dann die Konversion [!UICONTROL trait] basierend auf den Daten, die gesendet werden, wenn die Konvertierungsfunktion auf der Site ausgeführt wird.

## Erstellen Sie einen Look-Alike [!UICONTROL Model] aus [!UICONTROL Second Party] oder [!UICONTROL Third Party] Data {#create-a-look-alike-model-from-2nd-or-3rd-party-data}

Nach Abschluss der oben genannten Schritte können wir nun einen Algorithmus (Look-alike) [!UICONTROL Model] erstellen. Während wir die [!UICONTROL model] einrichten, verwenden wir die Konversion [!UICONTROL trait] als Basis [!UICONTROL trait] (wichtige Besucher, die wir Duplikat wünschen), und wir werden den aktivierten [!UICONTROL third party]-Datenstrom als unseren Personenkollektiv verwenden, aus dem wir uns abrufen können.

>[!VIDEO](https://video.tv.adobe.com/v/25190/?quality-12)

## Eine wichtige Best Practice {#an-important-best-practice}

Beim Erstellen des Algorithmus [!UICONTROL model] in Audience Manager möchten wir natürlich, dass das [!UICONTROL model] so effektiv wie möglich ist. Da das [!UICONTROL model] alle [!UICONTROL traits]-Elemente berücksichtigt, zu denen die Mitglieder Ihrer Basis [!UICONTROL trait]/[!UICONTROL segment] gehören, hilft es dem [!UICONTROL model] nicht, wenn sich ALLE Personen in einem [!UICONTROL trait]/[!UICONTROL segment] befinden. Wenn Sie also über ein super generisches [!UICONTROL traits] verfügen (wie jeder, der Ihre Site besucht hat, oder jeder, der eine Anzeige von Ihnen erhalten hat usw.), stellen Sie sicher, dass das [!UICONTROL data source], zu dem sie gehören, NICHT in der [!UICONTROL data sources] in Ihrer [!UICONTROL model]-Datei enthalten ist. Im Verwendungsfall dieses Artikels ist es unwahrscheinlich, dass Sie das tun würden, da wir uns darauf konzentrieren, [!UICONTROL third party] Daten für unsere neuen Look-Alikes zu betrachten, es lohnt sich jedoch, auf jeden Fall zu erwähnen und gilt für ALLE Ihre algorithmischen [!UICONTROL models].

## Erstellen eines Algorithmus [!UICONTROL Trait] {#creating-an-algorithmic-trait}

Als Nächstes müssen wir einen Algorithmus [!UICONTROL Trait] erstellen, damit die Ergebnisse von [!UICONTROL model] verwendet werden können. Ohne Erstellen eines [!UICONTROL trait] ist das Modell nutzlos. Nachdem [!UICONTROL model] ausgeführt wird, sollten Sie in das [!UICONTROL trait]-Dialogfeld gehen und eine algorithmische [!UICONTROL Trait] erstellen. Das folgende Video zeigt einige Tipps.

>[!VIDEO](https://video.tv.adobe.com/v/25191/?quality=12)

## [!UICONTROL Segment] aus den [!UICONTROL Model]-Daten erstellen und sie an DSP {#creating-a-segment-from-the-model-data-and-sending-it-to-dsps} senden

Nachdem Sie ein Algorithmus [!UICONTROL Trait] erstellt haben, können Sie ein neues [!UICONTROL segment] erstellen, um es einzufügen, sodass Sie die Daten aktivieren können (Sie können kein [!UICONTROL trait] aktivieren, sondern stattdessen ein neues [!UICONTROL trait] [!UICONTROL segment] [!UICONTROL Trait] mit dem Algorithmus  erstellen, damit Sie das [!UICONTROL segment] aktivieren (verwenden) können.

Nachdem Sie ein [!UICONTROL segment] aus diesem Algorithmus [!UICONTROL trait] erstellt haben, haben Sie eine Audience potenzieller Kunden, die aussehen wie Personen, die bereits auf Ihrer Site konvertiert wurden. Jetzt können Sie [!UICONTROL segment] einem Ihrer DSP [!UICONTROL destinations] in Audience Manager zuordnen. Sie können Ihr Marketing auf diese Look-Alikes Zielgruppe haben, die mit größerer Wahrscheinlichkeit auf Ihrer Site umgerechnet werden als nur die normale Öffentlichkeit, was Ihre Rendite aus Werbeausgaben erhöht. Viel Glück!
