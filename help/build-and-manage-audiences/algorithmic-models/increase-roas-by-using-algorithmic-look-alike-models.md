---
title: ROAS durch Verwendung algorithmischer (Look-alike) Modelle in Audience Manager erhöhen
description: Die wahre Stärke der Look-alike-Modellierung von Audience Manager liegt darin, dass Sie versuchen, Ihre Grundzielgruppe gegenüber einer qualitativ hochwertigen, brandneuen Benutzergruppe aus 2nd- und Drittanbieter-Datenquellen zu erweitern. In diesem Tutorial erfahren Sie, wie Sie anhand dieser Daten ein Modell erstellen.
feature: Algorithmische Modelle
topics: null
activity: use
doc-type: feature video
team: Technical Marketing
thumbnail: 25188.jpg
kt: 1849
role: User, Developer, Data Engineer, Architect, Data Architect, Admin, Leader
level: Intermediate
exl-id: 6626ae11-8709-4302-9e03-0d55878d2409
source-git-commit: 4b91696f840518312ec041abdbe5217178aee405
workflow-type: tm+mt
source-wordcount: '862'
ht-degree: 0%

---

# ROAS durch Verwendung von algorithmischer (Look-alike) [!UICONTROL Models] im Audience Manager erhöhen {#increase-roas-by-using-algorithmic-look-alike-models-in-audience-manager}

Die wahre Stärke von Audience Manager Look-alike [!UICONTROL Modeling] kommt, wenn Sie versuchen, Ihre Grundzielgruppe mit einer hochwertigen, brandneuen Benutzergruppe aus [!UICONTROL second party] und [!UICONTROL third party] [!UICONTROL data sources] zu erweitern. In diesem Tutorial lernen Sie die Schritte kennen, die zum Erstellen eines [!UICONTROL model] aus diesen Daten erforderlich sind.

## Aktivieren Sie [!UICONTROL Second Party] oder [!UICONTROL Third Party] Daten-Streams aus dem Audience Marketplace {#enable-2nd-or-3rd-party-data-streams-from-the-audience-marketplace}

Um [!UICONTROL second party] und [!UICONTROL third party] Daten in einem Look-alike [!UICONTROL model] zu verwenden, müssen wir diese Daten zunächst in Ihrer Audience Manager-Oberfläche aktivieren. Adobe verfügt über eine große Anzahl von [!UICONTROL second party] und [!UICONTROL third party] Datenanbietern, von denen Sie wählen können. Diese sind für Sie in einer Self-Service-Oberfläche in AAM über das Audience Marketplace verfügbar. Navigieren Sie zum Audience Marketplace und durchsuchen Sie die Möglichkeiten. Im folgenden Video erfahren Sie, wie Sie dies tun, einschließlich der Aktivierung kostenloser Streams vom Typ &quot;try before you buy&quot;, sodass Sie die Daten einbinden können, die für Ihre Organisation am nützlichsten sind, bevor Sie sich zu den Preisen des Datenanbieters verpflichten.

Um Ihnen bei der Suche und Auswahl des Datenanbieters zu helfen, ist eine großartige Ressource die [[!DNL Adobe Audience Finder]](https://www.adobe-audience-finder.com/).

>[!VIDEO](https://video.tv.adobe.com/v/25188/?quality=12)

## Identifizieren/Erstellen eines idealen Benutzers (Konversion) [!UICONTROL trait] oder [!UICONTROL segment] {#identify-create-an-ideal-user-conversion-trait-or-segment}

Was versuchen Sie, Menschen dazu zu bringen, auf Ihrer Site zu tun? Was ist Ihr Konversionsereignis? Natürlich gibt es viele verschiedene Antworten auf diese Frage, abhängig von Ihrem Site-Typ/Ihrer Vertikale und Ihren Organisationszielen. In jedem Fall ist es in AAM üblich, [!UICONTROL trait] für Besucher zu erstellen, die diese Kriterien erfüllt haben.

Im folgenden Video zeige ich Ihnen, wie Sie eine Konversion [!UICONTROL trait] erstellen, die Sie während des gesamten Tutorials erhalten und ein Look-alike [!UICONTROL model] erstellen möchten.

Wenn Sie Adobe Analytics-Ereignisse zum Erstellen von [!UICONTROL traits] verwenden, müssen Sie außerdem einen wichtigen Fallschirm beachten, damit Sie nicht mehr Benutzer erfassen, als Sie für [!UICONTROL trait] benötigen. Sehen Sie sich das folgende Video für die große Anzeige an. :)

>[!VIDEO](https://video.tv.adobe.com/v/23431/?quality=12)

**HINWEIS:** Im obigen Video geht das angezeigte Beispiel davon aus, dass Sie über Adobe Analytics verfügen. Das ist offensichtlich nicht der Fall. Wenn Sie Google Analytics (GA) haben, können Sie mit einem Modul Daten an AAM senden (siehe [Dokumentation](https://marketing.adobe.com/resources/help/en_US/aam/dil-google-universal-analytics.html)). Wenn Ihre Konversionsaktivität auf Ihrer Site von GA an AAM gesendet wird, können Sie daraus Ihre Konversionsrate [!UICONTROL trait] erstellen. Wenn Sie über eine andere Analyselösung (oder keine Analyselösung) verfügen, können Sie weiterhin Daten über unseren DIL-Code und die `submit`-Funktion an AAM senden. (siehe [Dokumentation](https://marketing.adobe.com/resources/help/en_US/aam/c_dil.html)). Erstellen Sie dann die Konvertierung [!UICONTROL trait] basierend auf den Daten, die gesendet werden, wenn die Konversionsaktivität auf der Site durchgeführt wird.

## Erstellen Sie einen Look-alike [!UICONTROL Model] aus [!UICONTROL Second Party] oder [!UICONTROL Third Party] Daten {#create-a-look-alike-model-from-2nd-or-3rd-party-data}

Nach Abschluss der obigen Schritte können wir nun einen algorithmischen (Look-alike) [!UICONTROL Model] erstellen. Während wir [!UICONTROL model] einrichten, verwenden wir die Konversion [!UICONTROL trait] als Basis [!UICONTROL trait] (wichtige Besucher, die wir duplizieren möchten) und verwenden den aktivierten [!UICONTROL third party]-Datenstrom als unseren Personenpool, aus dem wir abrufen können.

>[!VIDEO](https://video.tv.adobe.com/v/25190/?quality-12)

## Eine wichtige Best Practice {#an-important-best-practice}

Beim Erstellen des algorithmischen [!UICONTROL model] in Audience Manager möchten wir natürlich, dass das [!UICONTROL model] so effektiv wie möglich ist. Da das [!UICONTROL model] alle [!UICONTROL traits] berücksichtigt, zu denen die Mitglieder Ihrer Basis [!UICONTROL trait]/[!UICONTROL segment] gehören, hilft es dem [!UICONTROL model] nicht, wenn sich alle Personen in einem [!UICONTROL trait]/[!UICONTROL segment] befinden. Wenn Sie also über ein Super-generisches [!UICONTROL traits] verfügen (wie alle, die Ihre Site besucht haben, oder alle, die eine Anzeige von Ihnen erhalten haben, usw.), stellen Sie sicher, dass das [!UICONTROL data source], zu dem sie gehören, NICHT im [!UICONTROL data sources] in Ihrem [!UICONTROL model] enthalten ist. Im Anwendungsfall dieses Artikels ist es unwahrscheinlich, dass Sie dies tun, da wir uns darauf konzentrieren, [!UICONTROL third party]-Daten für unsere neuen Look-alikes zu betrachten. Es lohnt sich jedoch, auf jeden Fall zu erwähnen, und gilt für all Ihre algorithmischen [!UICONTROL models].

## Erstellen eines Algorithmus [!UICONTROL Trait] {#creating-an-algorithmic-trait}

Als Nächstes müssen wir einen algorithmischen [!UICONTROL Trait] erstellen, damit die Ergebnisse von [!UICONTROL model] verwendet werden können. Ohne Erstellen eines [!UICONTROL trait] ist das Modell nutzlos. Nachdem [!UICONTROL model] ausgeführt wird, stellen Sie sicher, dass Sie in das Dialogfeld [!UICONTROL trait] gehen und einen algorithmischen [!UICONTROL Trait] erstellen. Das folgende Video führt Sie durch und zeigt einige Tipps.

>[!VIDEO](https://video.tv.adobe.com/v/25191/?quality=12)

## Erstellen von [!UICONTROL Segment] aus den [!UICONTROL Model]-Daten und Senden an DSP {#creating-a-segment-from-the-model-data-and-sending-it-to-dsps}

Nachdem Sie ein algorithmisches [!UICONTROL Trait] erstellt haben, können Sie ein neues [!UICONTROL segment] erstellen, um es einzufügen, damit Sie die Daten aktivieren können (Sie können ein [!UICONTROL trait] nicht aktivieren, sondern ein neues [!UICONTROL trait] [!UICONTROL segment] mit dem Algorithmus [!UICONTROL Trait] erstellen, damit Sie das [!UICONTROL segment] aktivieren (verwenden) können.)

Nachdem Sie ein [!UICONTROL segment] aus diesem algorithmischen [!UICONTROL trait] erstellt haben, werden Sie eine Zielgruppe potenzieller Kunden haben, die aussehen wie Personen, die bereits auf Ihrer Site konvertiert sind. Jetzt können Sie dieses [!UICONTROL segment] jedem Ihrer DSP [!UICONTROL destinations] im Audience Manager zuordnen. Sie können Ihr Marketing auf die Look-alikes ausrichten, die auf Ihrer Site mit höherer Wahrscheinlichkeit als nur die normale Öffentlichkeit konvertieren und so Ihren Return on Ad Spend steigern. Viel Glück!
