## Silnik CMS

[WordPress](https://wordpress.org/) dla większych i standardowych witryn, dla wszystkiego co "małe" (np. typu Landing Page) możliwe zastosowanie forka [ClassicPress](https://www.classicpress.net/).
<br><br>
*Bez wykorzystania auto-instalatorów.

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

Dla bardzo małych instalacji albo [Bogo](https://wordpress.org/plugins/bogo/) albo [Sublanguage](https://github.com/maximeschoeni/sublanguage).
W skrajnych przypadkach natywna funkcjonalność obsługująca hreflang/alternate/przełącznik/locale_switch.<br>
([4 faza Gutenberga ma wprowadzić natywną obsługę multi-języcznych instalacji w WP](https://wptavern.com/how-will-gutenberg-phase-4-impact-multilingual-solutions-for-wordpress), tak więc po wdrożeniu sytuacja może się zmienić).<br><br>
Wszystko cokolwiek bardziej skomplikowanego wymaga Polylang lub WPML ze względu na wsparcie innych wtyczek.

---

## Dodatkowe zabezpieczenia

### Bazowe wytyczne

1. Jeśli nie ma potrzeby, to nie instalować ociężałych systemów zabezpieczeń typu Wordfence.
2. Wdrożenie świeżych kluczy SALT po przejściu instalacji na produkcję.
3. SSL jako podstawa.
4. Instalacja na produkcji powinna wykorzystywać separację folderów.
5. Wyłączenie XMLRPC.
6. Systematyczne aktualizacje wtyczek oraz motywu, jeśli używany jest "gotowiec".
7. Absolutny zakaz instalacji wtyczek typu "nulled" lub z nie-oficjalnych źródeł.
8. Systematyczne backupy.

### Konta

1. Absolutny zakaz dodawania kont z loginami typu admin, jakiekolwiek wariacje zawierające admin/wp lub nazwę firmy/witryny.
2. Jeśli jest możliwość, to zabezpieczyć panel administracyjny poprzez [BasicAuth](https://en.wikipedia.org/wiki/Basic_access_authentication).
3. Logowanie dwu-składnikowe do panelu administracyjnego, jeśli jest taka możliwość.

### Baza danych

1. Prefix bazy danych nie powinien rozpoczynać się od wp_.
2. Baza danych nie powinna być współdzielona pomiędzy instalacjami, czy innymi aplikacjami.
3. Użytkownik bazy danych powinien różnić się nazwą od bazy danych.
4. Mocne hasło dla bazy danych absolutnym wymogiem.
5. Jeśli jest możliwość, to zablokować dostęp zdalny.

### Dodatkowe zapisy dla .htaccess

1. Odmowa dostępu z zewnątrz do plików konfiguracyjnych i WordPressowego readme.
```
<FilesMatch "wp-config.*\.php|\.htaccess|readme\.html">
Order allow,deny
Deny from all
</FilesMatch>
```
2. Wyłączenie numeracji użytkowników
```
RewriteCond %{QUERY_STRING} author=\d
RewriteRule ^ /? [L,R=301]
```
<a name="blokada-xmlrpc"></a>
3. Kompletne zablokowanie XMLRPC
```
<files xmlrpc.php>
Order allow,deny
Deny from all
</files>
```
4. Blokada przetwarzania plików .php w folderze /wp-includes/, z wyjątkiem tinymce i ms-files
```
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /
RewriteRule ^wp-admin/includes/ - [F,L]
RewriteRule !^wp-includes/ - [S=3]
RewriteRule ^wp-includes/[^/]+\.php$ - [F,L]
RewriteRule ^wp-includes/js/tinymce/langs/.+\.php - [F,L]
RewriteRule ^wp-includes/theme-compat/ - [F,L]
</IfModule>
```

### Dodatkowe zapisy dla wp-config.php

1. Jeśli jest możliwość, to przenosiny dostępów bazy do oddzielnego pliku
```
// DB credentials
require_once "db-001x.php";
```

2. Kompletne wyłączenie wyświetlania informacji debugowania
```
// Debug
define( 'WP_DEBUG', false );
define( 'WP_DEBUG_LOG', false );
define( 'WP_DEBUG_DISPLAY', false );
if (! WP_DEBUG ) {
	ini_set('display_errors', 0);
}
```

3. Blokada edycji plików z poziomu panelu administracyjnego WP
```
define(	'DISALLOW_FILE_EDIT', true); // Disable file edits from CMS
```

4. Blokada wgrywania wtyczek/motywów (docelowo/domyślnie na produkcji)
```
define( 'DISALLOW_FILE_MODS', true );
```

### Dodatkowe zapisy dla folderu /wp-content/uploads/

1. Blokada przetwarzania plików .php
```
<FilesMatch "\.(?i:php)$">
	Order allow,deny
	Deny from all
</FilesMatch>
```

### Dodatkowe zapisy dla functions.php

1. Ukrywanie wersji z sekcji head, kanałów RSS i skryptów
```
// Removes WP version info
remove_action('wp_head', 'wp_generator');

function my_secure_generator( $generator, $type ) {
	return '';
}
add_filter( 'the_generator', 'my_secure_generator', 10, 2 );

function my_remove_src_version( $src ) {
	global $wp_version;

	$version_str = '?ver='.$wp_version;
	$offset = strlen( $src ) - strlen( $version_str );

	if ( $offset >= 0 && strpos($src, $version_str, $offset) !== FALSE )
		return substr( $src, 0, $offset );

	return $src;
}
add_filter( 'script_loader_src', 'my_remove_src_version' );
add_filter( 'style_loader_src', 'my_remove_src_version' );
```

2. Wyłączanie haseł aplikacji dla kont użytkowników
```
add_filter('wp_is_application_passwords_available', '__return_false');
```
- używane jedynie w bardzo specyficznych przypadkach i domyślnie nie są wymagane.

3. Wyłączenie XMLRPC
```
add_filter('xmlrpc_enabled', '__return_false');
```
- wskazane jest również [zablokowanie w .htaccess](#blokada-xmlrpc)
