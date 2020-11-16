---
title: Migration der AAM-Implementierung Ihrer Site von der clientseitigen DIL zur serverseitigen Weiterleitung
description: Dieses Tutorial gilt für Sie, wenn Sie sowohl Adobe Audience Manager (AAM) als auch Adobe Analytics haben und derzeit einen Treffer von der Seite an AAM mit "DIL"(Data Integration Library)-Code senden und auch einen Treffer von der Seite an Adobe Analytics senden. Da Sie beide Lösungen verwenden und beide Teil des Adobe Experience Cloud sind, haben Sie die Möglichkeit, die bewährte Methode der Aktivierung der "serverseitigen Weiterleitung (SSF)"zu befolgen, mit der die Analytics-Datenerfassungsserver die Site-Analysedaten in Echtzeit an Audience Manager weiterleiten können, anstatt dass clientseitiger Code einen zusätzlichen Treffer von der Seite an AAM senden muss. Dieses Lernprogramm führt Sie durch die Schritte, mit denen Sie den Übergang von der älteren "clientseitigen DIL"-Implementierung zur neueren "serverseitigen Weiterleitung"-Methode vollziehen können.
product: audience manager, analytics
feature: integration with analytics
topics: null
audience: implementer
activity: implement
doc-type: tutorial
team: Technical Marketing
kt: 1778
translation-type: tm+mt
source-git-commit: 133279f589bd58aef36a980c2b7248ae00fd9496
workflow-type: tm+mt
source-wordcount: '2319'
ht-degree: 0%

---


# Migrieren der AAM Implementierung Ihrer Site von [!DNL Client-Side] DIL zu [!DNL Server-Side Forwarding] {#migrating-your-site-s-aam-implementation-from-client-side-dil-to-server-side-forwarding}

Dieses Tutorial gilt für Sie, wenn Sie sowohl Adobe Audience Manager (AAM) als auch Adobe Analytics haben und derzeit einen Treffer von der Seite an AAM mit &quot;DIL&quot;([!DNL Data Integration Library])-Code senden und auch einen Treffer von der Seite an Adobe Analytics senden. Da Sie beide Lösungen haben und beide Teil des Adobe Experience Cloud sind, haben Sie die Möglichkeit, die Best Practice der Aktivierung von &quot;[!DNL Server-Side Forwarding] [!DNL Analytics] [!DNL client-side] (SSF)&quot;zu befolgen, was es den Datenerfassungsservern ermöglicht, Site-Analysedaten in Echtzeit an den Audience Manager weiterzuleiten, anstatt dass der Code einen zusätzlichen Treffer von der Seite an die AAM sendet. In diesem Lernprogramm werden Sie durch die Schritte geführt, mit denen Sie den Übergang von der älteren &quot;[!DNL Client-Side DIL]&quot; Implementierung zur neueren &quot;[!DNL Server-Side forwarding]&quot; Methode vollziehen können.

## [!DNL Client-Side] (DIL) oder [!DNL Server-Side] {#client-side-dil-vs-server-side}

Beim Vergleich und Kontrast dieser beiden Methoden zur Erfassung von Adobe Analytics-Daten in AAM kann es hilfreich sein, sich die Unterschiede in der folgenden Abbildung vorzustellen:

![clientseitig bis serverseitig](assets/client-side_vs_server-side_aam_implementation.png)

### [!DNL Client-side] DIL-Implementierung {#client-side-dil-implementation}

Wenn Sie diese Methode zum Abrufen von Adobe Analytics-Daten in AAM verwenden, bedeutet das, dass Sie zwei Treffer von Ihren Webseiten haben: Eine gehen zu [!DNL Analytics]und eine gehen zu AAM (nachdem die [!DNL Analytics] Daten auf der Webseite kopiert. [!UICONTROL Segments] werden von AAM auf die Seite zurückgegeben, wo sie für die Personalisierung usw. verwendet werden können. Dies gilt als &quot;ältere&quot;Implementierung und wird nicht mehr empfohlen.

Neben der Tatsache, dass diese Methode nicht den Best Practices folgt, bestehen die Nachteile der Verwendung dieser Methode darin,

* Zwei Treffer, die von der Seite kommen, anstelle von nur einem
* [!UICONTROL Server-Side Forwarding] ist für die Echtzeit-Freigabe von AAM Audiencen an erforderlich [!DNL Analytics], sodass [!DNL Client-side] Implementierungen diese Funktion nicht zulassen (und möglicherweise weitere Funktionen in der Zukunft)

Es wird empfohlen, zu einer [!UICONTROL Server-Side Forwarding] Methode zur AAM Implementierung zu wechseln.

### [!UICONTROL Server-Side Forwarding]Implementierung{#server-side-forwarding-implementation}

Wie im Bild oben gezeigt, kommt ein Treffer von der Webseite nach Adobe Analytics. [!DNL Analytics] leitet diese Daten dann an AAM in Echtzeit weiter, und Besucher werden in AAM [!UICONTROL traits] und [!UICONTROL segments]so ausgewertet, als wäre der Treffer direkt von der Seite gekommen.

[!UICONTROL Segments] werden bei demselben Echtzeit-Treffer zurückgegeben, an [!DNL Analytics]den die Antwort zur Personalisierung usw. an die Webseite weitergeleitet wird.

Es gibt keinen zeitlichen Abstand zum Wechsel zur serverseitigen Weiterleitung. Wir empfehlen dringend, dass alle Personen, die sowohl über Audience Manager als auch über die [!DNL Analytics] Verwendung dieser Implementierungsmethode verfügen, diese verwenden.

## Sie haben zwei wichtige Aufgaben {#you-have-two-main-tasks}

Auf dieser Seite gibt es eine Menge Informationen, und es ist natürlich alles wichtig. Es **sind jedoch zwei Dinge erforderlich**:

1. Ändern Sie den Code von [!DNL Client-Side] DIL-Code in [!UICONTROL Server-Side Forwarding] -Code
1. Wechseln Sie den Schalter im [!DNL Analytics] Beginn [!DNL Admin Console] zur eigentlichen Datenweiterleitung (pro [!UICONTROL report suite]).

Wenn Sie eine dieser beiden Optionen überspringen, funktioniert SSF nicht ordnungsgemäß. Schritte und weitere Daten wurden zu diesem Dokument hinzugefügt, damit Sie diese beiden Schritte für Ihre Einrichtung ordnungsgemäß durchführen können.

## Implementierungsoptionen {#implementation-options}

Wenn Sie von [!DNL client-side] zu [!DNL server-side]einer der Aufgaben wechseln, ändern Sie den Code in den neuen [!UICONTROL Server-Side Forwarding] Code. Dies geschieht mit einer der folgenden Optionen:

* Adobe Experience Platform Launch - Unsere empfohlene Implementierungsoption für Webeigenschaften. Sie werden sehen, dass dies eine sehr einfache Aufgabe ist, wie auch [!DNL Launch] das ganze harte Zeug für Sie.
* Auf der Seite - Sie können den neuen SSF-Code auch direkt in die `doPlugins` Funktion in Ihrer [!DNL appMeasurement.js] Datei platzieren, wenn Sie (noch) nicht mit Adobe Launch arbeiten.
* Andere Tag-Manager - Diese können wie die vorherige Option (auf der Seite) behandelt werden, da Sie den SSF-Code immer noch darin platzieren, `doPlugins`wo immer der andere Tag-Manager den [!DNL AppMeasurement] Code speichert

Im Abschnitt zum Aktualisieren des Codes werden wir uns die folgenden Punkte ansehen.

## Implementierungsschritte {#implementation-steps}

### Schritt 0: Voraussetzung: Experience Cloud-ID-Dienst (ECID) {#step-prerequisite-experience-cloud-id-service-ecid}

Die wichtigste Voraussetzung für den Umstieg auf [!UICONTROL Server-Side Forwarding] ist die Implementierung des Experience Cloud-ID-Diensts. Dies ist am einfachsten, wenn Sie Experience Platform Launch verwenden. In diesem Fall installieren Sie einfach die ECID-Erweiterung und der Rest wird ausgeführt.

Wenn Sie ein TMS ohne Adobe oder gar kein TMS verwenden, implementieren Sie bitte ECID, das **vor** jeder anderen Adobe ausgeführt werden soll. Weitere Informationen finden Sie in der [ECID-Dokumentation](https://marketing.adobe.com/resources/help/de_DE/mcvid/) . Die einzige weitere Voraussetzung ist für die Codeversionen. Wenn Sie also einfach die neuesten Versionen des Codes in den folgenden Schritten anwenden, ist das in Ordnung.

>[!NOTE]
>
>Bitte lesen Sie das gesamte Dokument vor der Implementierung. Der Abschnitt &quot;Zeit&quot;unten enthält wichtige Informationen darüber, *wann* Sie die einzelnen Elemente implementieren sollten, einschließlich der ECID (sofern sie noch nicht implementiert ist).

### Schritt 1: Derzeit verwendete Optionen aus DIL-Code aufzeichnen {#step-record-currently-used-options-from-dil-code}

Wenn Sie sich bereit machen, von [!DNL Client-Side] DIL-Code zu [!UICONTROL Server-Side Forwarding]wechseln, besteht der erste Schritt darin, alles zu identifizieren, was Sie mit DIL-Code tun, einschließlich benutzerspezifischer Einstellungen und Daten, die an AAM gesendet werden. Zu beachten und zu erwägen sind unter anderem:

* Normale [!DNL Analytics] Variablen, mit dem [!DNL siteCatalyst.init] DIL-Modul - Sie brauchen sich keine Sorgen zu machen, weil es nur darum geht, die normalen [!DNL Analytics] Variablen zu senden, und das geschieht, weil einfach SSF aktiviert ist.
* Partner Subdomain - Notieren Sie sich in der Funktion DIL.create den `partner` Parameter. Dies wird als &quot;Partner-Subdomäne&quot;oder manchmal als &quot;Partner-ID&quot;bezeichnet und wird benötigt, wenn Sie den neuen SSF-Code platzieren.
* [!DNL Visitor Service Namespace] - Auch als &quot;[!DNL Org ID]&quot;oder &quot;[!DNL IMS Org ID]&quot;bezeichnet, benötigen Sie dies auch, wenn Sie den neuen SSF-Code einrichten. Notieren Sie sich das.
* containerNSID, uuidCookie und andere erweiterte Optionen - Notieren Sie sich alle zusätzlichen erweiterten Optionen, die Sie verwenden, damit Sie sie auch im SSF-Code festlegen können.
* Zusätzliche Seitenvariablen - Wenn andere Variablen von der Seite an AAM gesendet werden (zusätzlich zu den normalen [!DNL Analytics] Variablen, die von SiteCatalyst.init verarbeitet werden), müssen Sie sie zur Kenntnis nehmen, damit sie über SSF gesendet werden können (Spoiler-Warnung: über [!DNL contextData] Variablen).

### Schritt 2: Code aktualisieren {#step-updating-the-code}

Im oben stehenden Abschnitt &quot;Implementierungsoptionen&quot;stehen Ihnen mehrere Optionen zur Implementierung zur Verfügung [!UICONTROL Server-Side Forwarding]. Damit dieser Abschnitt effektiv sein kann, müssen wir ihn in diese Abschnitte unterteilen (zwei davon zusammen). Gehen Sie zur Methode in diesem Abschnitt, die Ihre Anforderungen am besten beschreibt.

####  zu Adobe Experience Platform Launch{#launch-by-adobe}

Sehen Sie sich das folgende Video an, um mehr über das Verschieben von Implementierungsoptionen vom [!DNL Client-Side] DIL-Code in den [!UICONTROL Server-Side Forwarding] Experience Platform Launch zu erfahren.

>[!VIDEO](https://video.tv.adobe.com/v/26310/?quality=12)

#### &quot;Auf der Seite&quot;oder &quot;Nicht-Adobe Tag Manager&quot; {#on-the-page-or-non-adobe-tag-manager}

Sehen Sie sich das folgende Video an, um zu erfahren, wie Implementierungsoptionen vom [!DNL Client-Side] DIL-Code in [!UICONTROL Server-Side Forwarding] den [!DNL AppMeasurement] Code verschoben werden, der sich entweder in einer Datei oder in einem Tag-Management-System ohne Adobe befindet.

>[!VIDEO](https://video.tv.adobe.com/v/26312/?quality=12)

### Schritt 3: Aktivieren der Weiterleitung (per [!UICONTROL Report Suite]) {#step-enabling-the-forwarding-per-report-suite}

Bisher haben wir in diesem Tutorial die ganze Zeit damit verbracht, den Code von [!DNL Client-Side DIL] Code zu [!UICONTROL Server-Side Forwarding]wechseln. Das ist in Ordnung, denn es ist der schwierigere Teil. Dieser Abschnitt, obwohl Sie sehen werden, ist sehr einfach, ist genauso wichtig wie die Aktualisierung des Codes. In diesem Video erfahren Sie, wie Sie den Switch drehen, der die tatsächliche Übertragung von Daten von Analytics an Audience Manager ermöglicht.

>[!VIDEO](https://video.tv.adobe.com/v/26355/?quality-12)

**HINWEIS:** Wie im Video angegeben, denken Sie daran, dass es bis zu 4 Stunden dauern wird, bis die Weiterleitung vollständig auf dem Experience Cloud-Backend implementiert werden kann.

## Zeit {#timing}

Zur Erinnerung: Es gibt zwei wichtige Aufgaben für den Übergang von [!DNL Client-Side DIL] zu [!UICONTROL Server-Side Forwarding]:

1. Code aktualisieren
1. Wechseln des Switches im [!DNL Analytics] [!DNL Admin Console]

Aber die Frage ist: Welches tun Sie zuerst? Ist es wichtig? Okay, Entschuldigung, das waren zwei Fragen. Aber die Antworten sind... es kommt darauf an, und ja, es *kann* wichtig sein. Wie ist das vage? Machen wir es kaputt! Aber zuerst eine zusätzliche Frage, die sich stellen kann, wenn Sie eine große Organisation mit vielen Websites sind: Muss ich alles auf einmal machen? Das ist etwas einfacher. Nein. Du kannst es Stück für Stück machen... irgendwie. :)

### Ein bisschen tiefer Tauchgang {#a-little-deeper-dive}

Der Grund, warum Timing und Bestellung wichtig sind, liegt darin, wie die Weiterleitung *wirklich *funktioniert, was in den folgenden technischen Fakten zusammengefasst werden kann:

* Wenn Sie den Experience Cloud-ID-Dienst (ECID) implementiert haben und der Switch im [!DNL Analytics] (&quot;Switch&quot;) eingeschaltet ist, werden die Daten von [!DNL Admin Console] [!DNL Analytics] zu AAM weitergeleitet, auch wenn Sie den Code noch nicht aktualisiert haben.
* Wenn Sie keine ECID implementiert haben, werden die Daten nicht weitergeleitet, auch wenn Sie den Switch aktiviert haben und den SSF-Code haben.
* Der SSF-Code (auf oder auf der Seite) verarbeitet die Antwort wirklich und ist natürlich notwendig, um die Migration abzuschließen. [!DNL Launch]
* Beachten Sie, dass der SSF-Switch durch aktiviert ist [!UICONTROL Report Suite], dass der Code jedoch von der Eigenschaft in [!DNL Launch]oder von der [!DNL AppMeasurement] Datei verarbeitet wird, wenn Sie [!DNL Launch]

### Best Practices {#best-practices}

Auf der Grundlage dieser technischen Details gibt es hier Empfehlungen für den Zeitplan &quot;Was zu tun ist, wenn&quot;:

#### Wenn Sie noch KEINE ECID implementiert haben {#if-you-do-not-have-ecid-yet-implemented}

1. Wechseln Sie den Switch [!DNL Analytics] für jede Datei, die Sie für die SSF aktivieren [!UICONTROL report suite] möchten, ein.

   1. Die Weiterleitung wird noch nicht Beginn, da Sie keine ECID haben

1. Aktualisieren Sie Ihren Code pro Site von [!DNL Client-Side DIL] [!DNL Launch] zu SSF (dies könnte sich auf oder auf der Seite befinden, wie in einem anderen Abschnitt oben erläutert).

   1. Die Weiterleitung erfolgt jetzt (wie Sie ECID hinzugefügt haben) und Sie sollten auch eine richtige JSON-Antwort auf Ihren [!DNL Analytics] Beacon erhalten (weitere Informationen finden Sie im Abschnitt Validierung und Fehlerbehebung unten)

#### Wenn Sie ECID implementiert haben {#if-you-do-have-ecid-implemented}

1. Bereiten Sie den Code von DIL auf SSF PER vor und planen Sie ihn, [!UICONTROL report suite] damit Sie ihn für SSF aktivieren können:

   1. Wechseln Sie den Switch hinein, [!DNL Analytics] um SSF zu aktivieren

      1. Weiterleiten von WILL-Beginn, da ECID aktiviert ist
   1. Aktualisieren Sie so bald wie möglich Ihren Code von [!DNL Client-Side DIL] [!DNL Launch] zu SSF (dies könnte sich auf oder auf der Seite befinden, wie in einem anderen Abschnitt oben erläutert)

      1. Sie sollten eine geeignete JSON-Antwort auf Ihren [!DNL Analytics] Beacon erhalten (weitere Informationen finden Sie im Abschnitt Validierung und Fehlerbehebung unten)


**HINWEIS 1:** Es ist wichtig, diese beiden Schritte so nahe wie möglich aufeinander abzustimmen, da zwischen den Schritten 1 und 2 eine Datenduplizierung in AAM ausgeführt wird. Mit anderen Worten, SSF hat angefangen, Daten von [!DNL Analytics] zu AAM zu senden, und da sich der DIL-Code noch auf der Seite befindet, wird es auch einen Treffer geben, der direkt von der Seite in AAM geht, was die Daten verdoppelt. Sobald Sie den Code von DIL auf SSF aktualisieren, wird dies gelindert.

**HINWEIS 2:** Wenn Sie eher eine kleine Diskrepanz bei den Daten als eine kleine Datenduplizierung haben möchten, können Sie die Reihenfolge der Schritte 1 und 2 oben ändern. Wenn Sie den Code von DIL auf SSF verschieben, wird der Datenfluss in AAM gestoppt, bis Sie den Switch umdrehen können, um den SSF für den [!UICONTROL report suite]Code zu aktivieren. Normalerweise würden die Kunden lieber eine kleine Datenverdoppelt haben, anstatt Besucher in [!UICONTROL traits] und [!UICONTROL segments]zu verpassen.

#### Migrationszeit bei vielen Sites und [!UICONTROL Report Suites] {#migration-timing-when-you-have-many-sites-and-report-suites}

Dieses Thema wird in früheren Abschnitten kurz behandelt, da die Hauptstrategie wie folgt zusammengefasst werden kann:

Migrieren Sie eine Site/[!UICONTROL report suite] (oder eine Gruppe von Websites/[!UICONTROL report suites]) gleichzeitig.

Dies kann jedoch auf der Grundlage einiger möglicher Szenarien etwas kompliziert werden:

* Sie haben eine Site, die mehrere verschiedene [!UICONTROL report suites]
* Sie haben eine [!UICONTROL report suite] , die mehrere Sites enthält (z. B. eine globale [!UICONTROL report suite])
* Sie verwenden eine [!DNL Launch] Eigenschaft, um mehrere Sites abzudecken
* Sie haben verschiedene Entwicklungsteams für verschiedene Sites

Aufgrund dieser Elemente kann es etwas kompliziert werden. Die besten Dinge, die ich vorschlagen kann, sind:

* Nehmen Sie sich etwas Zeit, um eine Strategie für die Migration zum SSF zu entwickeln, die auf den oben erläuterten Dingen basiert
* Da eine einzelne Eigenschaft in [!DNL Launch] (oder eine einzelne [!DNL AppMeasurement] [!UICONTROL report suites]Datei) normalerweise einer oder zwei verschiedenen Variablen zugeordnet wird, können Sie wahrscheinlich einen Plan erstellen, der in diesen unterschiedlichen Gruppen nacheinander funktioniert, und Ihr Unternehmen auf SSF aktualisieren.
* Wenn Sie mit Adobe Consulting arbeiten, sprechen Sie mit ihnen hinsichtlich Ihres Migrationsplans, damit sie bei Bedarf helfen können

## Validierung und Fehlerbehebung {#validation-and-troubleshooting}

Die wichtigste Möglichkeit, um zu überprüfen, ob die App aktiv [!UICONTROL Server-Side Forwarding] ist, besteht darin, die Antwort auf die von der App stammenden Adobe Analytics-Treffer zu überprüfen.

Wenn Sie keine Daten [!UICONTROL server-side forwarding] von [!DNL Analytics] zu Audience Manager machen, gibt es keine Antwort auf das [!DNL Analytics] Beacon (außer 2 x 2 Pixel). Wenn Sie jedoch SSF ausführen, gibt es Elemente, die Sie in der [!DNL Analytics] [!DNL Analytics] Anforderung und Antwort überprüfen können, die Ihnen mitteilen, dass die Kommunikation mit Audience Manager korrekt ist, den Treffer weiterleitet und eine Antwort erhält.

>[!VIDEO](https://video.tv.adobe.com/v/26359/?quality=12)

**WARNUNG:** Achten Sie auf den falschen &quot;Erfolg&quot;- Wenn es eine Antwort gibt und alles funktioniert, stellen Sie sicher, dass Sie das &quot;Zeug&quot;-Objekt in der Antwort haben. Wenn nicht, sehen Sie vielleicht eine Nachricht, die sagt [!DNL "status":"SUCCESS"]. So verrückt das auch klingen mag, das ist eigentlich der Testversand, dass es nicht richtig funktioniert. Wenn Sie dies sehen, bedeutet dies, dass Sie die Codeaktualisierung in oder [!DNL Launch] abgeschlossen haben, die Weiterleitung in der [!DNL AppMeasurement]Datei jedoch noch nicht abgeschlossen [!DNL Analytics] [!DNL Admin Console] ist. In diesem Fall müssen Sie sicherstellen, dass Sie SSF in der [!DNL Analytics][!DNL Admin Console] für Ihre [!UICONTROL report suite]. Wenn Sie das haben, und es ist noch nicht 4 Stunden geduldig, da es so lange dauern kann, alle notwendigen Änderungen am Backend vorzunehmen.

![false success](assets/falsesuccess.png)

Weitere Informationen [!UICONTROL Server-Side Forwarding]finden Sie in der [Dokumentation](https://marketing.adobe.com/resources/help/en_US/reference/ssf.html).
