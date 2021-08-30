---
title: Verwendung Look-alike-Modelle zum Erweitern des ausverkauften Bestands aus Ihren Erstanbieterdaten
description: In diesem Tutorial führen wir Sie durch die Schritte, die Sie unternehmen sollten, um Look-alike-Modelle einzurichten und zu verwenden, sodass Sie neue Look-alike-Zielgruppen erstellen und diese als Erweiterung für Ihr Konversionssegment verkaufen können.
feature: Algorithmic Models
topics: null
activity: use
doc-type: feature video
team: Technical Marketing
thumbnail: 23523.jpg
kt: 1688
role: User, Developer, Data Engineer, Architect, Data Architect, Admin, Leader
level: Intermediate
exl-id: 6820528e-3211-4a1d-be05-50f1292179d2
source-git-commit: 4d4c12e9f9a33760a89460258c3802fcf3a4e22b
workflow-type: tm+mt
source-wordcount: '822'
ht-degree: 0%

---

# Verwendung von Look-alike [!UICONTROL Models] zum Erweitern des ausverkauften Bestands von Ihren [!UICONTROL First Party]-Daten {#using-look-alike-models-to-extend-sold-out-inventory-from-your-st-party-data}

In diesem Tutorial führen wir Sie durch die Schritte, die Sie zur Einrichtung und Verwendung von Look-Alike [!UICONTROL Models] unternehmen sollten, damit Sie neue Look-alike-Zielgruppen erstellen und diese als Erweiterung Ihrer Konversion verkaufen können [!UICONTROL segment].

## Anwendungsfalldetails {#use-case-details}

Sie sind ein Herausgeber von Inhalten. Wenn Sie bereits Inventar für Konverter auf Ihrer Site ausverkauft haben, können Sie denken, dass Ihre Chance dort endet. Geben Sie AAM Look-Alike [!UICONTROL Models] ein. Mit dieser Funktion können Sie den ausverkauften Bestand weiter erweitern und auch Zielgruppen von Personen verkaufen, die vielleicht noch nicht konvertiert sind, aber wie konvertierte Personen aussehen/handeln. Diese Zielgruppe [!UICONTROL segment] würde in der Regel für weniger als die tatsächlichen Konverter verkauft. Sie können jedoch Ihrem Geschäftsergebnis hinzufügen, indem Sie eine zusätzliche Zielgruppenoption für Advertiser bereitstellen, die Anzeigen auf Ihrer Site platzieren möchten. Der zusätzliche Vorteil dieses Anwendungsbeispiels besteht darin, dass es Sie nicht kostet, dieses Modell auf Ihren Erstanbieterdaten auszuführen.

Die Schritte in diesem Tutorial lauten wie folgt:

1. Identifizieren/Erstellen eines idealen Benutzers (Konversion) [!UICONTROL trait] oder [!UICONTROL segment]
1. Erstellen Sie ein [!UICONTROL model] mit dieser Konvertierung [!UICONTROL trait]/[!UICONTROL segment] als Basiselement
1. Wählen Sie die [!UICONTROL First party]-Datenquelle(n) im [!UICONTROL model] aus und führen Sie [!UICONTROL model] aus.
1. Erstellen Sie einen algorithmischen [!UICONTROL Trait] aus den [!UICONTROL model] Ergebnissen und fügen Sie den [!UICONTROL trait] zu einem [!UICONTROL segment] hinzu.
1. Stellen Sie den [!UICONTROL segment] interessierten Werbetreibenden bereit, die Konversion der [!UICONTROL segment]-Verkäufe zu erweitern.

## Identifizieren/Erstellen eines idealen Benutzers (Konversion) [!UICONTROL trait] oder [!UICONTROL segment] {#identify-create-an-ideal-user-conversion-trait-or-segment}

Was versuchen Sie, Menschen dazu zu bringen, auf Ihrer Site zu tun? Was ist Ihr Konversionsereignis? Natürlich gibt es viele verschiedene Antworten auf diese Frage, abhängig von Ihrem Site-Typ/Ihrer Vertikale und Ihren Organisationszielen. In jedem Fall ist es in AAM üblich, [!UICONTROL trait] für Besucher zu erstellen, die diese Kriterien erfüllt haben.

In diesem Anwendungsfall wird dies bereits angenommen, da Sie den Bestand für Konverter verkauft haben. Für die Zwecke dieses Tutorials ist es jedoch gut, es als Referenz für den restlichen Anwendungsfall zu diskutieren.

Wenn Sie Ereignisse zum Erstellen von [!UICONTROL traits] verwenden, müssen Sie außerdem einen wichtigen Fallschirm beachten, damit Sie nicht mehr Benutzer erfassen, als Sie für [!UICONTROL trait] benötigen. Sehen Sie sich das folgende Video für die große Anzeige an. :)

>[!VIDEO](https://video.tv.adobe.com/v/23431/?quality=12)

**HINWEIS:** Im obigen Video geht das angezeigte Beispiel davon aus, dass Sie über Adobe Analytics verfügen. Das ist offensichtlich nicht der Fall. Wenn Sie Google Analytics (GA) haben, können Sie mit einem Modul Daten an AAM senden (siehe [Dokumentation](https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/dil-overview.html)). Wenn Ihre Konversionsaktivität auf Ihrer Site von GA an AAM gesendet wird, können Sie daraus Ihre Konversionseigenschaft erstellen. Wenn Sie über eine andere Analyselösung (oder keine Analyselösung) verfügen, können Sie weiterhin Daten über unseren DIL-Code und die `submit`-Funktion an AAM senden. (siehe [Dokumentation](https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/dil-modules.html)). Erstellen Sie dann erneut die Konversionseigenschaft basierend auf den Daten, die gesendet werden, wenn die Konversionsaktivität auf der Site durchgeführt wird.

## Erstellen eines Look-alike [!UICONTROL Model] aus [!UICONTROL First Party] Daten {#creating-a-look-alike-model-from-first-party-data}

In diesem Schritt erstellen wir [!UICONTROL First Party] Look-Alike [!UICONTROL Model]. Das bedeutet, dass wir nicht nur eine [!UICONTROL first party] Konvertierung [!UICONTROL trait]/[!UICONTROL segment] für unsere Basis [!UICONTROL trait]/[!UICONTROL segment] verwenden werden (dies wäre für die meisten [!UICONTROL models] sowieso normal), sondern auch nur in den Pool von [!UICONTROL first party] Daten für mehr Personen suchen, die wie die Konverter aussehen. Wir werden keine [!UICONTROL second party]- oder [!UICONTROL third party]-Daten betrachten.

In diesem Anwendungsfall ist dies wichtig, da wir versuchen, eine [!UICONTROL segment] von Benutzern auf unserer Site zu erstellen, die wie Konverter aussehen, aber noch nicht konvertiert wurden, sodass wir diese Look-alike [!UICONTROL segment] an interessierte Advertiser verkaufen können.

>[!VIDEO](https://video.tv.adobe.com/v/23504/?quality-12)

## Erstellen eines Algorithmus [!UICONTROL Trait] {#creating-an-algorithmic-trait}

Als Nächstes müssen wir einen algorithmischen [!UICONTROL Trait] erstellen, damit die Ergebnisse von [!UICONTROL model] verwendet werden können. Ohne Erstellen eines [!UICONTROL trait] ist [!UICONTROL model] nutzlos. Nachdem [!UICONTROL model] ausgeführt wird, gehen Sie also in das Dialogfeld [!UICONTROL trait] und erstellen Sie ein algorithmisches [!UICONTROL Trait]. Das folgende Video führt Sie durch und zeigt einige Tipps.

>[!VIDEO](https://video.tv.adobe.com/v/23523/?quality=12)

## Angebot des algorithmischen [!UICONTROL Segment] an Advertiser {#offering-the-algorithmic-segment-to-advertisers}

Nachdem Sie ein algorithmisches [!UICONTROL Trait] erstellt haben, können Sie ein neues [!UICONTROL segment] erstellen, um es einzufügen, damit Sie die Daten aktivieren können (Sie können ein [!UICONTROL trait] nicht aktivieren, sondern ein neues [!UICONTROL trait] [!UICONTROL segment] mit dem Algorithmus [!UICONTROL Trait] erstellen, damit Sie das [!UICONTROL segment] aktivieren (verwenden) können.

Nachdem Sie einen [!UICONTROL segment] von [!UICONTROL first party] Besuchern erstellt haben, die im Look-alike [!UICONTROL model] einen hohen Wert erzielt haben (d. h. die aussehen wie Konverter, aber noch nicht konvertiert wurden), können Sie diesen [!UICONTROL segment] für Advertiser auf Ihrer Site anbieten, selbst wenn Sie Ihren gesamten Bestand an tatsächlichen Konvertern auf Ihrer Site ausverkauft haben. Dies ist eine großartige Möglichkeit, diese Zielgruppe zu erweitern und durch die Verwendung von Look-Alike [!UICONTROL Models] in Audience Manager weiterhin zusätzlichen Umsatz zu erzielen.
