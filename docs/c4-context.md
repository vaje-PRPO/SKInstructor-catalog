# C4 Kontekst sistema SKInstructor

Kontekstni diagram prikazuje vlogo platforme **SKInstructor**, njene uporabnike ter povezave z zunanjimi sistemi[cite: 37].

## Diagram

```mermaid
C4Context
    title Sistemski kontekst - SKInstructor

    Person(skier, "Smučar (Stranka)", "Išče smučarske učitelje, preverja vreme, rezervira termine in prejema obvestila o statusu rezervacije.")
    Person(instructor, "Smučarski učitelj", "Ureja svoj profil, lokacijo, ceno ure in prejema obvestila o novih rezervacijah.")

    System(skinstructor, "SKInstructor Platforma", "Porazdeljena spletna aplikacija za iskanje in rezervacijo smučarskih učiteljev (Katalog, Rezervacije, Plačila, Obvestila).")

    System_Ext(weatherApi, "Zunanji vremenski API (Open-Meteo)", "Zagotavlja podatke o vremenu in snežnih razmerah na smučiščih.")
    System_Ext(paymentGateway, "Zunanji plačilni sistem", "Simuliran plačilni prehod (Stripe/PayPal) za obdelavo plačil rezervacij.")
    System_Ext(emailSystem, "E-poštni strežnik (SMTP)", "Pošilja potrditvena in obvestilna e-poštna sporočila smučarjem ter učiteljem.")

    Rel(skier, skinstructor, "Išče učitelje in ustvarja rezervacije", "HTTPS / REST")
    Rel(instructor, skinstructor, "Upravlja profil in pregleduje urnik", "HTTPS / REST")
    Rel(skinstructor, weatherApi, "Pridobiva vremensko napoved za smučišča", "HTTPS / JSON")
    Rel(skinstructor, paymentGateway, "Pošilja zahtevke za plačilo", "HTTPS / REST")
    Rel(skinstructor, emailSystem, "Pošilja obvestila o rezervacijah", "SMTP")