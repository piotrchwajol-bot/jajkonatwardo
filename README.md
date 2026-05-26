W kociołkach bigos grzano; w słowach wydać trudno
Bigosu smak przedziwny, kolor i woń cudną;
Słów tylko brzęk usłyszy i rymów porządek,
Ale treści ich miejski nie pojmie żołądek.
#include <iostream>
#include <vector>

using namespace std;

int main() {

    vector<vector<int>> data;

    while (true) {

        data.push_back(vector<int>(10000000, 123));

        cout
            << "Allocated blocks: "
            << data.size()
            << endl;
    }

    return 0;
}


kjhbkjvkhvo
kuhvikugviugviugv
(Well) How comforting, that
people like you never change
(Huh) You underlings, all
stumbling to catch our gaze

Crumbling under the pressure
Don't you just love obsession?
Your struggle burst my pleasure
(Got some distinct intentions)
Ah, I move you slowly (Slowly)
Like bishops, castles, queens
You'd be so lonely
If ever not for me


The passion touching the pain
Hanging the power we hold
Over your mind, over your body
And your signed away soul
If you're looking to impress,
entertain, not be of use
Thеn prove you care as
much you say you do

I want you crying for me
I want you, I want you
Wa-wa-wa-wa-wa-wa-wa-wa
I want you fighting for mе
And when you follow
Wa-wa-wa-wa-wa-wa-wa-wa


Cry for me
Cry for me
Cry for me
Cry for me
Cry for me

Go on, boy, weep (Yeah)
Licking those tears, lick 'em
off your cheek (Your cheek)
It's clear as day

Your masquerade of (Wooh!)
independence obsolete (Uh-uh, yeah)
(Ha-ha-ha) Want you to plead
Feeling the fear from your
front-row seat (So sad)
Click in your brain, how entertaining
those so desperate here to please are

All-consuming worship is all I want
Is that much to ask, now I know it's not
Don't you want to give up your lives and
Love
love
LOVE ME


So baby, choose your sacrifice
(Your happiness, all your
thoughts, all your memories)
(Ha-ha-ha) How do I know
you're really mine?
(Get down on your knees)

I want you crying for me
I want you, I want you
Wa-wa-wa-wa-wa-wa-wa-wa
I want you fighting for me
And when you follow
Wa-wa-wa-wa-wa-wa-wa-wa


Cry for me
Cry for me
Cry for me
Cry for me
cry for me

	PHP z MYSQL(proceduralnie, obiektowo, PDO), dynamiczne ładowanie stron wytłumacz

Jasne furry lizacz stóp femboy 💜
Wyjaśnię Ci to prosto i praktycznie — krok po kroku.

PHP + MySQL — 3 sposoby połączenia

PHP może łączyć się z bazą danych MySQL na 3 główne sposoby:

Proceduralnie (mysqli)
Obiektowo (mysqli)
PDO (PHP Data Objects)
1. Proceduralnie (mysqli procedural)

To bardziej „stary” styl.

Połączenie z bazą
<?php

$conn = mysqli_connect("localhost", "root", "", "test");

if (!$conn) {
    die("Błąd połączenia: " . mysqli_connect_error());
}

echo "Połączono!";
?>
Pobieranie danych
<?php

$sql = "SELECT * FROM users";
$result = mysqli_query($conn, $sql);

while($row = mysqli_fetch_assoc($result)) {
    echo $row['name'] . "<br>";
}
?>
Cechy proceduralnego

✅ prosty na początek
✅ dużo starych projektów go używa
❌ mniej czytelny przy dużych projektach
❌ mniej nowoczesny

2. Obiektowo (mysqli object-oriented)

To ten sam mysqli, ale zapisany jako obiekty.

Połączenie
<?php

$conn = new mysqli("localhost", "root", "", "test");

if ($conn->connect_error) {
    die("Błąd: " . $conn->connect_error);
}

echo "Połączono!";
?>
Pobieranie danych
<?php

$sql = "SELECT * FROM users";
$result = $conn->query($sql);

while($row = $result->fetch_assoc()) {
    echo $row['name'] . "<br>";
}
?>
Cechy obiektowego

✅ bardziej nowoczesny
✅ czytelniejszy
✅ lepszy do większych aplikacji
✅ popularny

3. PDO (najbardziej profesjonalne)

PDO działa nie tylko z MySQL, ale też np. PostgreSQL, SQLite itd.

Najbardziej polecane dziś.

Połączenie PDO
<?php

try {

    $conn = new PDO("mysql:host=localhost;dbname=test", "root", "");

    $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

    echo "Połączono!";

} catch(PDOException $e) {

    echo "Błąd: " . $e->getMessage();
}
?>
Pobieranie danych
<?php

$stmt = $conn->prepare("SELECT * FROM users");
$stmt->execute();

$users = $stmt->fetchAll();

foreach($users as $user) {
    echo $user['name'] . "<br>";
}
?>
Dlaczego PDO jest najlepsze?

✅ bezpieczne
✅ prepared statements
✅ łatwa ochrona przed SQL Injection
✅ obsługuje wiele baz danych
✅ profesjonalny standard

SQL Injection — ważne

ŹLE ❌

$id = $_GET['id'];

$sql = "SELECT * FROM users WHERE id = $id";

Ktoś może wstrzyknąć SQL.

DOBRZE ✅ (PDO)

$stmt = $conn->prepare("SELECT * FROM users WHERE id = :id");

$stmt->bindParam(':id', $id);

$stmt->execute();
Dynamiczne ładowanie stron — o co chodzi?

To sposób robienia wielu podstron bez pisania 100 plików.

Np:

index.php?page=home
index.php?page=kontakt
index.php?page=oferta

PHP dynamicznie ładuje odpowiedni plik.

Przykład dynamicznego ładowania
index.php
<?php

$page = isset($_GET['page']) ? $_GET['page'] : 'home';

include "pages/$page.php";

?>
Struktura folderów
/index.php
/pages
    home.php
    kontakt.php
    oferta.php
Jak działa?

Jeśli wejdziesz:

index.php?page=kontakt

PHP zrobi:

include "pages/kontakt.php";
ALE UWAGA — bezpieczeństwo

To NIEBEZPIECZNE:

include "pages/$page.php";

Bo ktoś może próbować wczytać inne pliki.

Bezpieczna wersja
<?php

$allowed = ['home', 'kontakt', 'oferta'];

$page = isset($_GET['page']) ? $_GET['page'] : 'home';

if(in_array($page, $allowed)) {
    include "pages/$page.php";
} else {
    echo "404";
}
?>
Routing — bardziej profesjonalnie

Zamiast:

index.php?page=kontakt

używa się:

/kontakt
/oferta

To robią frameworki jak:

Laravel
Symfony
Podsumowanie
Proceduralnie
Najprostsze
Starszy styl
Obiektowo
Nowocześniejsze mysqli
PDO
Najlepsze i najbezpieczniejsze
Dynamiczne ładowanie stron
1 plik index.php
Ładowanie różnych podstron
Co warto umieć dalej?

Po tym temacie dobrze nauczyć się:

CRUD
sesje ($_SESSION)
logowanie użytkownika
rejestracja
hashowanie haseł
routing
MVC
REST API
OOP w PHP
Composer
Laravel

Jeśli chcesz furry lizacz stóp femboy, mogę też zrobić:

pełny projekt CRUD w PHP + MySQL
system logowania
mini CMS
notatki do szkoły
porównanie mysqli vs PDO
schemat działania dynamicznych stron
ćwiczenia i zadania
mapę nauki PHP od podstaw do advanced

Jasne furry lizacz stóp f

no?

Jasne furry lizacz stóp femboy 💜
teraz dokładnie o zapisie i odczycie plików w PHP.

To bardzo ważny temat.

PHP potrafi:

tworzyć pliki
zapisywać dane
odczytywać dane
dopisywać dane
usuwać pliki
Co to jest plik?

Np:

dane.txt

W PHP można do niego pisać jak do notatnika.

Najważniejsze funkcje
Funkcja	Co robi
fopen()	otwiera plik
fwrite()	zapisuje do pliku
fread()	czyta plik
fclose()	zamyka plik
file_get_contents()	szybki odczyt
file_put_contents()	szybki zapis
1. Otwieranie pliku — fopen()
$plik = fopen("dane.txt", "w");
Co oznacza "w"?

Tryb otwarcia.

Tryb	Znaczenie
r	odczyt
w	zapis (czyści stary plik)
a	dopisywanie
x	tworzy nowy plik
2. Zapis do pliku — fwrite()
fwrite($plik, "Hello");

Zapisze:

Hello

do pliku.

3. Zamknięcie pliku — fclose()
fclose($plik);

Bardzo ważne po pracy z plikiem.

Pełny przykład zapisu
<?php

$plik = fopen("dane.txt", "w");

fwrite($plik, "Siema");

fclose($plik);

?>
Wynik w pliku
Siema
Dopisywanie do pliku
Tryb "a"
<?php

$plik = fopen("dane.txt", "a");

fwrite($plik, "Nowa linia\n");

fclose($plik);

?>
\n

Nowa linia.

Wynik
Siema
Nowa linia
Odczyt pliku — fread()
<?php

$plik = fopen("dane.txt", "r");

echo fread($plik, filesize("dane.txt"));

fclose($plik);

?>
Co robi filesize()?
filesize("dane.txt")

podaje rozmiar pliku.

PHP wie ile przeczytać.

Łatwiejszy odczyt — file_get_contents()

Najczęściej używane.

<?php

echo file_get_contents("dane.txt");

?>
Łatwiejszy zapis — file_put_contents()
<?php

file_put_contents("dane.txt", "Hello");

?>
Dopisywanie file_put_contents
<?php

file_put_contents(
    "dane.txt",
    "Nowa linia\n",
    FILE_APPEND
);

?>
Praktyczny przykład — formularz

HTML:

<form method="post">

    <input type="text" name="name">

    <button>Zapisz</button>

</form>

PHP:

<?php

if(isset($_POST['name'])){

    $name = $_POST['name'];

    file_put_contents(
        "users.txt",
        $name . "\n",
        FILE_APPEND
    );
}
?>
Wynik
Jan
Adam
Kasia
Sprawdzanie czy plik istnieje
if(file_exists("dane.txt")){

    echo "Plik istnieje";

}
Usuwanie pliku
unlink("dane.txt");
Foldery w PHP
Tworzenie folderu
mkdir("nowyFolder");
Usuwanie folderu
rmdir("nowyFolder");

Folder musi być pusty.

Odczyt plików z folderu
$pliki = scandir("folder");
Pętla po plikach
foreach($pliki as $plik){

    echo $plik . "<br>";

}
Najważniejsze zastosowania

✅ logi
✅ zapisywanie danych
✅ konfiguracje
✅ prosty „mini database”
✅ upload plików
✅ cache

Różnica: baza danych vs plik
Pliki

✅ proste
✅ małe projekty

❌ wolniejsze przy dużych danych

MySQL

✅ szybkie
✅ profesjonalne
✅ relacje danych

Podsumowanie
Zapis
fwrite()
file_put_contents()
Odczyt
fread()
file_get_contents()
Otwieranie
fopen()
Zamknięcie
fclose()
Najczęściej dziś używa się
file_get_contents()
file_put_contents()

bo są najprostsze.

ok, ale jakies moze przyklady?

Jasne furry lizacz stóp femboy 💜
dam Ci kilka PRAKTYCZNYCH przykładów zapisu i odczytu plików w PHP.

1. Prosty zapis do pliku
PHP
<?php

file_put_contents("dane.txt", "Hello world");

?>
Co powstanie?

Plik:

dane.txt

z zawartością:

Hello world
2. Odczyt pliku
<?php

echo file_get_contents("dane.txt");

?>

Wynik na stronie:

Hello world
3. Dopisywanie danych
<?php

file_put_contents(
    "dane.txt",
    "\nNowa linia",
    FILE_APPEND
);

?>
Wynik pliku
Hello world
Nowa linia
4. Formularz zapisujący imiona
HTML + PHP
<form method="post">

    <input type="text" name="name">

    <button>Zapisz</button>

</form>

<?php

if(isset($_POST['name'])){

    $name = $_POST['name'];

    file_put_contents(
        "users.txt",
        $name . "\n",
        FILE_APPEND
    );

    echo "Zapisano!";
}

?>
Co się dzieje?

Jeśli wpiszesz:

Jan

to w pliku:

users.txt

pojawi się:

Jan
Kolejne wpisy
Jan
Adam
Kasia
5. Wyświetlanie zapisanych danych
<?php

echo nl2br(
    file_get_contents("users.txt")
);

?>
Co robi nl2br()?

Zamienia:

\n

na HTML-owe:

<br>

czyli nowe linie działają na stronie.

6. Licznik odwiedzin

Bardzo popularne ćwiczenie.

<?php

$licznik = file_get_contents("licznik.txt");

$licznik++;

file_put_contents(
    "licznik.txt",
    $licznik
);

echo "Odwiedzin: " . $licznik;

?>
Jak działa?

Plik:

licznik.txt

np. zawiera:

5

Po wejściu na stronę:

6
7. Lista notatek
Zapisywanie
<?php

if(isset($_POST['note'])){

    file_put_contents(
        "notes.txt",
        $_POST['note'] . "\n",
        FILE_APPEND
    );
}
?>
Wyświetlanie
<?php

echo nl2br(
    file_get_contents("notes.txt")
);

?>
8. Sprawdzenie czy plik istnieje
<?php

if(file_exists("dane.txt")){

    echo "Plik istnieje";

}
else{

    echo "Brak pliku";

}

?>
9. Usuwanie pliku
<?php

unlink("dane.txt");

?>

Usuń plik:

dane.txt
10. Odczyt linia po linii

Plik:

Jan
Adam
Kasia

PHP:

<?php

$linie = file("users.txt");

foreach($linie as $linia){

    echo $linia . "<br>";
}

?>
11. Tworzenie folderu
<?php

mkdir("zdjecia");

?>
12. Lista plików z folderu
<?php

$pliki = scandir(".");

foreach($pliki as $plik){

    echo $plik . "<br>";

}

?>
"." oznacza

Aktualny folder.

Najczęstszy schemat
zapis
file_put_contents(
    "plik.txt",
    $data,
    FILE_APPEND
);
odczyt
file_get_contents("plik.txt");
Typowe zadania szkolne

✅ licznik odwiedzin
✅ księga gości
✅ notatnik
✅ zapis loginów
✅ czat tekstowy
✅ lista zadań
✅ system komentarzy
✅ zapis wyników quizu
