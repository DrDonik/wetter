# Pendler-Wetter-App

## Zweck
Persönliche Single-File-Web-App, die täglich eine einzige Frage beantwortet: **Ich pendle mit dem Velo: Was soll ich heute anziehen?**
Bewusst keine allgemeine Wetter-App. Bestehende Apps zeigen zu viel oder das Falsche.

## Richtlinien zur Implementierung
1. Immer zuerst die User Experience bedenken und definieren. Keine unnötigen Schritte, kein visuelles Rauschen, einfache, konsistente und intuitive Bedienung, kein unnötiges Scrollen, keine unnötige cognitive load.
2. Niemals irgendetwas sofort implementieren. Immer zuerst den Plan zur Implementierung und die daraus resultierende User Experience vorstellen und klären, ob alles richtig verstanden wurde und der Vorschlag den Vorstellungen des Nutzers entspricht. Die Implementierung darf erst erfolgen, wenn der Nutzer dies explizit erlaubt.
3. Dies ist eine persönliche App: es braucht weder backward noch forward compatibility.

## Pull Requests
Coderabbit reviewt dieses Repository nicht automatisch (es hat weniger als 10 Sterne). Jedes Review muss deshalb selbst ausgelöst werden: nach dem Eröffnen des PR ein Kommentar, der genau `@coderabbitai review` enthält. Nach jedem Push erneut auslösen, auch bei reinen Doku-Änderungen, denn jeder Push hebt die Freigabe auf (Änderungen an Titel oder Beschreibung des PR sind keine Pushes). Coderabbit reviewt höchstens einmal pro Stunde. Ein Auslöser innerhalb dieser Stunde wird nicht ausgeführt: Coderabbit ändert seine Bestätigung in „Action not completed: Review rate limited“ und seinen Zusammenfassungs-Kommentar oben im PR in einen Hinweis „Review limit reached“ mit der Wartezeit. Der Auslöser wird verworfen, nicht nachgeholt.

Abweichend von Richtlinie 2 werden offensichtliche Korrekturen aus dem Review direkt umgesetzt; alles, was eine Ermessensfrage ist, wird mit dem Nutzer besprochen statt selbst entschieden. Jeder Coderabbit-Thread mit abgelehntem Vorschlag bekommt eine Antwort: Coderabbit gibt erst frei, wenn alle seine Threads erledigt sind, und listet offene in einem Hinweis „Automatic approval withheld“ in seinem Zusammenfassungs-Kommentar. Einen Thread mit abgelehntem Vorschlag erst als erledigt markieren, wenn der Nutzer der Ablehnung zugestimmt hat.

Direkt nach dem Eröffnen des PR Auto-Merge (Squash) einschalten. Das Ruleset auf `main` verlangt eine Freigabe und hebt sie bei jedem Push auf; es gibt kein CI und keinen Pflicht-Check. Coderabbits Freigabe ist diese Freigabe, der PR merget also von selbst, sobald die Review-Runde fertig ist. Niemand merget von Hand.

Sich nicht darauf verlassen, dass PR-Ereignisse ankommen. Nach jedem Auslösen eine Nachfrage mit `send_later` einplanen: 10 Minuten nach dem Auslösen oder eine Minute nach der Wartezeit, die ein Hinweis zum Stundenlimit nennt. Bei der Nachfrage den PR lesen: gemergt heisst fertig; keine Reaktion von Coderabbit auf den Auslöser heisst, er ging verloren, also einmal neu auslösen; ein Hinweis zum Stundenlimit heisst, nach Ablauf neu auslösen; verlangte Änderungen heissen umsetzen und besprechen wie oben. Nach jedem Schritt eine neue Nachfrage einplanen, bis der PR gemergt ist oder auf den Nutzer wartet.
