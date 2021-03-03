---
title: Identifizieren der Partner-ID oder Subdomäne Ihres Audience Managers
description: Bei der Implementierung einiger Experience Cloud-Funktionen müssen Sie wissen, was Ihr Audience Manager "Partner-ID"ist (auch als "Client-ID"oder "Subdomäne"bezeichnet). In diesem Video zeigen wir Ihnen zwei Orte, an denen Sie diese ID in der Benutzeroberfläche des Audience Managers abrufen können.
feature: Implementierungsgrundlagen
topics: null
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 2359
role: '"Entwickler, Dateningenieur"'
level: Zwischenschaltung
translation-type: tm+mt
source-git-commit: a7dc335e75697a7b1720eccdadbb9605fdeda798
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---


# Identifizieren der Subdomäne Ihres Audience Managers {#how-to-identify-your-audience-manager-partner-id-or-subdomain}

Bei der Implementierung einiger Experience Cloud-Funktionen müssen Sie wissen, was Ihr Audience Manager `Subdomain` ist (auch als `client ID` oder `Partner ID` bezeichnet). In diesem Video zeigen wir Ihnen zwei Orte, an denen Sie diese Informationen in der Benutzeroberfläche des Audience Managers abrufen können.

## Das Ende verraten... {#giving-away-the-ending}

Falls Sie lieber einfach einspringen und es ohne dieses kurze Video finden möchten, finden Sie Ihr `Partner Subdomain` an zwei Stellen in der Benutzeroberfläche:

1. Wenn Sie bereits eine [!UICONTROL rule-based] [!UICONTROL trait] erstellt haben, klicken Sie auf **[!UICONTROL Get Trait URL]**
   [!UICONTROL Get Trait URL] neben dem Ordner  [!UICONTROL trait] in der Liste  [!UICONTROL traits] in diesem Ordner befindet, und die URL enthält Ihre Subdomäne in der URL.
1. Wenn Sie die Schnittstelle **[!UICONTROL Tools]** > **[!UICONTROL Tags]** aufrufen und für Ihren Container auf **[!UICONTROL Get code]** klicken, wird die Subdomäne am Ende der Akamai-Linie ausgerichtet

Wenn Sie es mit diesen schnellen Referenzen nicht schnell finden können, ist das Video eine kurze Zeitverpflichtung. :)

>[!VIDEO](https://video.tv.adobe.com/v/25922/?quality=12)

>[!IMPORTANT]
>
>Jedem Kunden des Adobe Experience Cloud wird eine numerische ID zugewiesen, die oft als &quot;PID&quot;oder Partner-ID bezeichnet wird. Dies ist nicht die ID, über die wir in diesem Artikel und Video sprechen. Stattdessen handelt es sich bei der &quot;Partner-Subdomäne&quot;, die manchmal auch als Partner-ID bezeichnet wird, in der Regel um eine Version des Kundennamens und die Subdomäne des Servers, an den die Daten gesendet werden. Wenn Ihre Firma z. B. &quot;Bob&#39;s Knobs&quot; ist (alle Dinge Türklinken, natürlich haha), dann ist es wahrscheinlich, dass Ihre Partner-Subdomäne &quot;bobsknobs&quot; wäre, während die &quot;PID&quot; eher &quot;12345&quot; wäre. Normalerweise müssen Sie Ihre PID nicht kennen, aber Ihre Subdomäne ist wichtig zu wissen, damit Sie Ihre Audience Manager-Implementierung konfigurieren können.

