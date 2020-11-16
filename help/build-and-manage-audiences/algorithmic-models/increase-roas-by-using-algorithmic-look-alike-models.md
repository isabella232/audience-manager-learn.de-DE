---
title: Erhöhung der ROAS durch Verwendung algorithmischer (Look-Alike) Modelle im Audience Manager
description: Die wahre Stärke des Look-alike Modelings von Audience Manager liegt darin, dass Sie Ihre Ausgangsergebnisse gegenüber einer hochwertigen, ganz neuen Benutzergruppe aus 2nd- und 3rd-Party-Datenquellen erweitern möchten. In diesem Lernprogramm erfahren Sie, wie Sie anhand dieser Daten ein Modell erstellen.
feature: algorithmic models
topics: null
audience: all
activity: use
doc-type: feature video
team: Technical Marketing
kt: 1849
translation-type: tm+mt
source-git-commit: a108c51fdad66f4e7974eb96609b6d8f058cb6ff
workflow-type: tm+mt
source-wordcount: '860'
ht-degree: 0%

---


# ROAS durch Verwendung von Algorithmus (Look-Alike) [!UICONTROL Models] im Audience Manager erhöhen {#increase-roas-by-using-algorithmic-look-alike-models-in-audience-manager}

Die wahre Stärke des Look-Alias des Audience Managers [!UICONTROL Modeling] liegt darin, dass Sie Ihre Grundlinie-Audience gegenüber einer qualitativ hochwertigen, brandneuen Gruppe von Benutzern aus [!UICONTROL second party] und [!UICONTROL third party] [!UICONTROL data sources]zu erweitern suchen. In diesem Lernprogramm erfahren Sie, wie Sie eine [!UICONTROL model] anhand dieser Daten erstellen können.

## Aktivieren [!UICONTROL Second Party] oder [!UICONTROL Third Party] Aktivieren von Datenströmen aus dem Audience Marketplace {#enable-2nd-or-3rd-party-data-streams-from-the-audience-marketplace}

Um die Daten in einem aussehenden Format zu verwenden [!UICONTROL second party] und zu [!UICONTROL third party] verarbeiten, müssen wir diese Daten zunächst in Ihre Audience Manager-Oberfläche aktivieren [!UICONTROL model]. Adobe verfügt über eine große Anzahl von [!UICONTROL second party] und [!UICONTROL third party] Datenanbietern, aus denen Sie wählen können. Diese sind für Sie in einer Self-Service-Schnittstelle in AAM, über das Audience Marketplace verfügbar. Navigieren Sie zum Audience Marketplace und durchsuchen Sie die Möglichkeiten. Das folgende Video zeigt Ihnen, wie Sie dies tun können, einschließlich der Aktivierung kostenloser Streams, die Sie vor dem Kauf ausprobieren, sodass Sie die Daten einbinden können, die für Ihr Unternehmen am nützlichsten sind, bevor Sie sich zu den Preisen des Datenanbieters verpflichten.

Um Ihnen zu helfen, zu recherchieren und zu entscheiden, welcher Datenanbieter verwendet werden soll, ist eine großartige Ressource die [[!DNL Adobe Audience Finder]](https://www.adobe-audience-finder.com/).

>[!VIDEO](https://video.tv.adobe.com/v/25188/?quality=12)

## Identifizieren/Erstellen Sie einen idealen Benutzer (Konversion) [!UICONTROL trait] oder [!UICONTROL segment] {#identify-create-an-ideal-user-conversion-trait-or-segment}

Was versuchen Sie, Leute zu bewegen, auf Ihrer Site zu tun? Was ist Ihr Umrechnungs-Ereignis? Natürlich gibt es viele verschiedene Antworten auf diese Frage, je nach Site-Typ/Vertikal und Ihren organisatorischen Zielen. Auf jeden Fall ist es in AAM üblich, einen [!UICONTROL trait] für Besucher zu erstellen, die diese Kriterien erfüllt haben.

Im folgenden Video werde ich Ihnen zeigen, wie Sie eine Konvertierung erstellen [!UICONTROL trait], die Sie möchten, während Sie durch diese Übung und erstellen Sie ein Look-like [!UICONTROL model].

Wenn Sie Adobe Analytics-Ereignis zum Erstellen verwenden, [!UICONTROL traits]müssen Sie außerdem ein wichtiges Thema beachten, damit Sie nicht mehr Benutzer sammeln, als Sie sollten, um in der [!UICONTROL trait]. Sehen Sie sich das folgende Video für die große Offenbarung an. :)

>[!VIDEO](https://video.tv.adobe.com/v/23431/?quality=12)

**HINWEIS:** In dem oben gezeigten Video wird davon ausgegangen, dass Sie über Adobe Analytics verfügen. Das ist offensichtlich nicht der Fall. Wenn Sie Google Analytics (GA) haben, haben wir ein Modul, mit dem Sie Daten an AAM senden können (siehe [Dokumentation](https://marketing.adobe.com/resources/help/en_US/aam/dil-google-universal-analytics.html)), und wenn Ihre Konversions-Aktivität auf Ihrer Site von GA an AAM gesendet wird, dann können Sie Ihre Konvertierung [!UICONTROL trait] daraus erstellen. Wenn Sie über eine andere Analyselösung (oder keine Analyselösung) verfügen, können Sie trotzdem Daten über unseren DIL-Code und die `submit` Funktion an AAM senden. (siehe [Dokumentation](https://marketing.adobe.com/resources/help/en_US/aam/c_dil.html)). Erstellen Sie dann die Konversion [!UICONTROL trait] basierend auf den Daten, die gesendet werden, wenn die Konvertierungsfunktion auf der Site ausgeführt wird.

## Look-alike [!UICONTROL Model] aus [!UICONTROL Second Party] oder [!UICONTROL Third Party] Daten erstellen {#create-a-look-alike-model-from-2nd-or-3rd-party-data}

Nach Abschluss der oben genannten Schritte können wir nun einen Algorithmus (Look-alike) erstellen [!UICONTROL Model]. Bei der Einrichtung des [!UICONTROL model]Projekts werden wir die Konversion [!UICONTROL trait] als Grundlage verwenden [!UICONTROL trait] (wichtige Besucher, die wir Duplikat wünschen) und den aktivierten [!UICONTROL third party] Datenstrom als Personengruppe verwenden, aus dem wir uns zurückziehen können.

>[!VIDEO](https://video.tv.adobe.com/v/25190/?quality-12)

## Eine wichtige Best Practice {#an-important-best-practice}

Beim Erstellen des Algorithmus [!UICONTROL model] im Audience Manager wollen wir natürlich, dass das so effektiv wie möglich [!UICONTROL model] ist. Da der [!UICONTROL model] prüft, [!UICONTROL traits] dass die Mitglieder Ihrer Basis [!UICONTROL trait]/[!UICONTROL segment] Teil sind, hilft es dem nicht, [!UICONTROL model] wenn ALLE Personen in einem [!UICONTROL trait]/[!UICONTROL segment]sind. Daher sollten Sie sicherstellen, dass die [!UICONTROL traits] Daten, zu denen Sie gehören, NICHT im [!UICONTROL data source] Abschnitt enthalten sind, wenn Sie über Super-Generika verfügen (wie alle, die Ihre Site aufriefen, oder alle, die eine Anzeige von Ihnen erhalten haben, usw.), dass die Inhalte, zu denen [!UICONTROL data sources] sie gehören, NICHT in Ihrer [!UICONTROL model]. Im Anwendungsfall dieses Artikels ist es unwahrscheinlich, dass Sie das tun würden, da wir uns darauf konzentrieren, Daten für unsere neuen Look-Alikes zu betrachten, aber es lohnt sich, auf jeden Fall zu erwähnen, und gilt für alle Ihre Algorithmen [!UICONTROL third party] [!UICONTROL models].

## Erstellen eines Algorithmus [!UICONTROL Trait] {#creating-an-algorithmic-trait}

Als Nächstes müssen wir einen Algorithmus erstellen, [!UICONTROL Trait]damit die Ergebnisse des [!UICONTROL model] Berichts verwendet werden können. Ohne Erstellung eines [!UICONTROL trait]Modells ist das Modell nutzlos. Stellen Sie also nach der [!UICONTROL model] Ausführung sicher, dass Sie in den [!UICONTROL trait] Dialog gehen und einen Algorithmus erstellen [!UICONTROL Trait]. Das folgende Video zeigt einige Tipps.

>[!VIDEO](https://video.tv.adobe.com/v/25191/?quality=12)

## Erstellen eines [!UICONTROL Segment] Formulars aus den [!UICONTROL Model] Daten und Senden an DSP {#creating-a-segment-from-the-model-data-and-sending-it-to-dsps}

Nachdem Sie einen Algorithmus erstellt haben, [!UICONTROL Trait]können Sie einen neuen erstellen, [!UICONTROL segment] um ihn einzufügen, sodass Sie die Daten aktivieren können (Sie können einen [!UICONTROL trait]nicht aktivieren, sondern stattdessen ein neues Eins-[!UICONTROL trait] mit dem Algorithmus [!UICONTROL segment] darin erstellen, sodass Sie den [!UICONTROL Trait] [!UICONTROL segment]aktivieren (verwenden) können.

Nachdem Sie eine [!UICONTROL segment] aus diesem Algorithmus erstellt haben [!UICONTROL trait], verfügen Sie über eine Audience potenzieller Kunden, die wie Personen aussehen, die bereits auf Ihrer Site konvertiert wurden. Jetzt können Sie dies [!UICONTROL segment] einem Ihrer DSP [!UICONTROL destinations] im Audience Manager zuordnen. Sie können Ihr Marketing auf diese Look-Alikes Zielgruppe haben, die mit größerer Wahrscheinlichkeit auf Ihrer Site umgerechnet werden als nur die normale Öffentlichkeit, was Ihre Rendite aus Werbeausgaben erhöht. Viel Glück!
