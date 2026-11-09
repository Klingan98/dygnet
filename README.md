# Dygnet

En enkel svensk webbapp/PWA där du fördelar valda delar av dagen mellan ärenden.

## Ändra start och slut

Klicka på **kugghjulet** uppe till höger. Ändra **Starttid** och **Sluttid** och klicka **Spara**.

- Standardintervallet är **10:00–15:30**, alltså 5 timmar och 30 minuter.
- Inställningarna sparas automatiskt **lokalt i webbläsaren** (localStorage). Ingen `.env` behövs.
- Sluttiden måste vara senare än starttiden samma kalenderdag.
- Procentvisningen, kvoterna och urtavlans etiketter uppdateras direkt.
- Ärendenas tid räknas **bara under det valda intervallet**. Timern kan vara aktiv utanför intervallet men då räknas ingen tid.
- Ett nytt pass startar vid den angivna starttiden, och då nollställs dagens upparbetade tid.
- Ändrar du tiderna under ett pass behålls hittills registrerade minuter i den mån det fortfarande är samma pass. Om du flyttar passgränsen så att en annan dag blir aktuell, startar den dagens tidsräkning på noll.

## Uppgradering från äldre version

Sparade ärenden (namn, färg och procentsats) behålls under uppdateringen. Vid första övergången från den gamla 24-timmarsmodellen nollställs dagens upparbetade ärendetider, eftersom de inte kan räknas om rättvist till ett förkortat dygn. En lokal säkerhetskopia av den äldre appens data sparas under nyckeln `dygnet-v1-backup-24h` om lokal lagring tillåter det.

## Köra appen

Publicera mappens filer på en statisk webbserver, eller starta lokalt (från den här mappen):

```bash
python3 -m http.server 8000
```

Öppna sedan http://localhost:8000. Service worker gör appen användbar offline efter första laddningen över HTTP(S).
