# -API
 API Penetration Testing by university.apisec.ai


 Fundamentals Notes
 # 🔐 Bezpieczeństwo API — Notatka całościowa

---

## 1. API ukryte na widoku („APIs Hiding in Plain Sight”)

- API są łatwe do znalezienia w ruchu sieciowym aplikacji (np. DevTools → Network)
- Nawet jeśli UI nie pokazuje funkcji, API może je udostępniać
- Atakujący analizują ruch aplikacji, aby odkryć endpointy

---

## 2. Dlaczego API są głównym celem ataków

**API:**
- łączą frontend z backendem
- dają bezpośredni dostęp do danych
- są łatwe do odkrycia

**Ekosystem API:**
- Web UI  
- aplikacje mobilne  
- publiczne API  
- funkcje aplikacji  
- dane backendowe  
- API wewnętrzne  

👉 **API = centralny punkt komunikacji systemu**  
➡ kompromitacja API = kompromitacja całej aplikacji

---

## 3. Jak atakowane są API

Atakujący → aplikacja → API → backend



Atakujący szukają API, które:

- mają nadmierne uprawnienia
- zwracają za dużo informacji
- pozwalają na dostęp do nieautoryzowanych funkcji
- zawierają błędy logiki biznesowej

---

## 4. Klasyczny cyberatak vs atak API

**Klasyczny łańcuch ataku**
1. Rekonesans  
2. Infiltracja  
3. Weaponize  
4. Ruch boczny  
5. Eskalacja uprawnień  
6. Włamanie  

**Atak API**

👉 API skraca drogę atakującego

---

## 5. Przykład incydentu — T-Mobile

- dostęp do danych przez pojedyncze API bez autoryzacji
- ~37 milionów kont klientów
- jedna luka → masowe naruszenie

---

## 6. Krajobraz regulacyjny (Compliance)

| Standard | Zakres |
|--------|------|
| PCI DSS | płatności kartą |
| GDPR | dane osobowe |
| HIPAA | dane medyczne |
| SEC | spółki publiczne |
| UNECE R155 | motoryzacja |
| FedRAMP | systemy rządowe |

---

## 7. Obszary zgodności regulacyjnej

### Bezpieczeństwo
- bezpieczne tworzenie aplikacji
- testy podatności przed wdrożeniem
- szybkie wykrywanie i naprawa błędów

### Prywatność
- ochrona danych osobowych i medycznych
- obowiązek zgłaszania naruszeń
- wysokie kary finansowe

### Dostępność danych
- interoperacyjność
- udostępnianie danych
- kary za blokowanie dostępu

---

## 8. OWASP API Security Top 10 (2023)

1. Broken Object Level Authorization  
2. Broken Authentication  
3. Broken Object Property Level Authorization  
4. Unrestricted Resource Consumption  
5. Broken Function Level Authorization  
6. Unrestricted Access to Sensitive Business Flows  
7. Server Side Request Forgery (SSRF)  
8. Security Misconfiguration  
9. Improper Inventory Management  
10. Unsafe Consumption of APIs  

---

# Szczegółowe podatności

---

## API1 — Broken Object Level Authorization (BOLA)

**Opis**
- błędy kontroli dostępu do obiektów
- najczęstsza podatność API
- trudna do wykrycia runtime

**Ryzyko**
- wyciek danych
- dostęp do cudzych danych
- oszustwa finansowe

**Przykład**
> Czy użytkownik A może odczytać dane użytkownika B?

---

## API2 — Broken Authentication

**Przyczyny**
- brak OAuth
- brak MFA
- brak CAPTCHA
- błędna implementacja auth
- credential stuffing

**Skutki**
- przejęcie kont
- nieautoryzowane operacje
- harvesting danych
- ransomware

---

## API3 — Broken Object Property Level Authorization

**Opis**
- dostęp do pól obiektu bez uprawnień
- mass assignment
- excessive data exposure

**Ryzyko**
- zmiana pól (`account_type=premium`)
- wyciek danych wrażliwych

---

## API4 — Unrestricted Resource Consumption

**Problemy**
- brak rate limiting
- brak limitów pamięci/plików
- zbyt duże odpowiedzi
- zbyt wiele operacji w request

**Skutki**
- DoS
- degradacja systemu
- spadek wydajności

---

## API5 — Broken Function Level Authorization

**Opis**
- dostęp do operacji bez uprawnień
- manipulacja metodami HTTP

**Skutki**
- eskalacja uprawnień
- zmiana danych kont
- usuwanie danych

---

## API7 — SSRF

**Opis**
serwer API wysyła request tam gdzie nie powinien

**Skutki**
- dostęp do systemów wewnętrznych
- wycieki danych
- pivot do dalszych ataków

---

## API8 — Security Misconfiguration

**Przykłady**
- brak aktualizacji
- brak TLS
- złe uprawnienia
- brak nagłówków bezpieczeństwa
- verbose errors

**Skutek**
→ pełna kompromitacja systemu

---

## API9 — Improper Inventory Management

**Problemy**
- brak wiedzy o API
- stare endpointy
- brak wersjonowania
- shadow / zombie APIs

---

## API10 — Unsafe Consumption of APIs

**Ryzyka**
- podatne API partnera
- brak walidacji danych
- niebezpieczna integracja

**Skutki**
- przejęcie kont
- wyciek danych
- kompromitacja systemu

---

# 📊 Kluczowe wzorce ryzyka API

**Najczęstsze klasy problemów**
- autoryzacja → API1, API3, API5
- uwierzytelnianie → API2
- limity → API4
- konfiguracja → API8
- widoczność API → API9
- zależności zewnętrzne → API10

---

## 🚨 Najważniejszy wniosek

> Większość podatności API to błędy logiki biznesowej,  
> nie klasyczne luki techniczne.

---



