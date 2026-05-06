## Silnik CMS

[WordPress](https://wordpress.org/) dla większych i standardowych witryn, dla wszystkiego co "małe" (np. typu Landing Page) możliwe zastosowanie forka [ClassicPress](https://www.classicpress.net/)

---

## Lista wtyczek, które warto wziąć pod uwagę

### Zarządzanie treścią

1. [ACF w wersji PRO](https://www.advancedcustomfields.com/pro/) - hardkodowane układy lub ["flexible content"](https://www.advancedcustomfields.com/resources/flexible-content/), jeśli projekt wymaga zarządzania kolejnością sekcji.
2. [Contact Form 7](https://wordpress.org/plugins/contact-form-7/) - czyste, proste i skuteczne zarządzanie formularzami, z możliwością rozbudowy.

### Użytkowe

1. [Bloat-off – bloat removal and utilities](https://wordpress.org/plugins/bloatoff-utils/) - bazowe optymalizacje.
2. [CompressX](https://wordpress.org/plugins/compressx/) - do automatycznej kompresji Webp/AVIF; jedna z niewielu wtyczek, która umożliwia kompresowanie do formatu AVIF bez ograniczeń, czy podłączeń do zewnętrznych serwisów.
3. [Clean Image Filenames](https://wordpress.org/plugins/clean-image-filenames/) - sanityzacja nazw plików, również tych zawierających polskie znaki diakrytyczne; niezwykle przydatne zwłaszcza w przypadku migracji, gdzie niestandardowe nazwy plików mogą się "pogubić".
4. [Disable Media Pages](https://wordpress.org/plugins/disable-media-pages/) - WordPress co prawda od wersji 6.4 domyślnie wyłącza podstrony załączników, jednak nie wyłącza przy tym blokowania slugów, czy też nie ustawia odpowiednich przekierowań, ta wtyczka rozwiązuje oba te problemy.
5. [Index WP MySQL For Speed](https://wordpress.org/plugins/index-wp-mysql-for-speed/) - optymalizacja dla baz danych większych instalacji.
6. [Mobile Detect](https://wordpress.org/plugins/tinywp-mobile-detect/) - wtyczka uzupełniająca do funkcji wp_is_mobile(), która wyklucza tablety z listy wykryć.
7. [No Gutenberg – Disable Blocks Editor and Global Styles – Back to Classic Editor](https://wordpress.org/plugins/no-gutenberg/) - całkowite pozbycie się Gutenberga i FSE + włączenie obsługi klasycznego edytora.
8. [Pressidium Cookie Consent](https://wordpress.org/plugins/pressidium-cookie-consent/) - w pełni darmowe, nieograniczone zarządzanie ciastkami; alternatywnie można użyć i zakodować [cookieconsent](https://github.com/orestbida/cookieconsent/).
9. [Safe SVG](https://wordpress.org/plugins/safe-svg/) - możliwość wgrywania oraz automatyczna sanityzacja plików typu SVG.
10. [Sierotki](https://wordpress.org/plugins/sierotki/) - poprawne zarządzanie typografią na polsko-języcznych stronach.
11. [The SEO Framework](https://wordpress.org/plugins/autodescription/) - najbardziej zoptymalizowana opcja SEO dla witryny, opcjonalnie jednak trzeba zakodowac dodatkowo wpisy schema.
12. [WP-Sweep](https://wordpress.org/plugins/wp-sweep/) - oczyszczanie instalacji z rewizji, osieroconych wpisów meta, komentarzy-spamu, duplikatów meta itd.; działa optymalnie nawet na większych instalacjach.
13. [WPvivid — Backup, Migration & Staging](https://wordpress.org/plugins/wpvivid-backuprestore/) - backupy.

---

## Obsługa tłumaczeń

Dla bardzo małych instalacji albo [Bogo](https://wordpress.org/plugins/bogo/) albo [Sublanguage](https://github.com/maximeschoeni/sublanguage).<br>
Wszystko cokolwiek bardziej skomplikowanego wymaga Polylang lub WPML ze względu na wsparcie innych wtyczek.

---

## Dodatkowe zabezpieczenia
