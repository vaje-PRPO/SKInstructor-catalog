# SKInstructor-catalog
Ta repozitorij vsebuje mikrostoritev za katalog učiteljev (catalog service).

Mikrostoritev `catalog-service` je del porazdeljene spletne aplikacije **SKInstructor**, namenjene iskanju in rezervaciji smučarskih učiteljev. Storitev skrbi za upravljanje profilov smučarskih učiteljev, njihovih lokacij (smučišč), jezikovnih znanj, licenc in urnih postavk.

## Ekipa in lastništvo

* **Lastnik storitve (`catalog-service`):** Lina Herman

## Tehnološki sklad

* **Jezik:** Java 25 LTS
* **Ogrodje:** Spring Boot 
* **Gradnja:** Maven (`./mvnw`)
* **Podatkovna baza:** PostgreSQL (`catalog_db`)
* **API specifikacija:** OpenAPI 3.1 (`openapi.yaml`)

## REST API končne točke

Osnovna pot: `/api/v1`

* `GET /teachers` — Pridobi seznam učiteljev z možnostjo filtriranja (`resort`, `maxPrice`, `language`).
* `GET /teachers/{id}` — Podrobnosti posameznega učitelja.
* `POST /teachers` — Registracija novega smučarskega učitelja.
* `PUT /teachers/{id}` — Posodobitev podatkov obstoječega učitelja.
* `DELETE /teachers/{id}` — Izbris profila učitelja.

Celotna pogodba vmesnika je definirana v datoteki `openapi.yaml`.

## Lokalni zagon in razvoj

### Predpogoji
* Nameščen JDK 25
* Nameščen Docker (za lokalno instanco baze PostgreSQL in Dev Services)

### Zagon v razvojnem načinu
Repozitorij uporablja Maven Wrapper, zato lokalna namestitev Mavna ni potrebna.

Za zagon aplikacije (Quarkus Dev Mode):
```bash
./mvnw quarkus:dev