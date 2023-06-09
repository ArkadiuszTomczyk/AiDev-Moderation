    Inicjalizacja klienta HTTP i ładowanie pliku properties: Kod inicjalizuje obiekt klienta HTTP, który jest używany do wysyłania zapytań do serwera. Następnie ładuje plik config.properties, który zawiera klucze API potrzebne do interakcji z usługami API.

    Autoryzacja i uzyskanie tokena: Aplikacja wykonuje żądanie POST do URL https://zadania.aidevs.pl/token/moderation z kluczem API uzyskanym z pliku properties. Odpowiedź z tego żądania powinna zawierać token, który jest zapisywany na późniejsze użycie.

    Wysyłanie żądania o zadanie: Klient HTTP wysyła żądanie GET do https://zadania.aidevs.pl/task/{token}, gdzie {token} to token otrzymany w poprzednim kroku. Odpowiedź z tego żądania zawiera zadanie do wykonania, które jest przechowywane jako tekst.

    Przetwarzanie zadania: Odpowiedź z żądania zadania jest przetwarzana jako JSON i konwertowana na listę zdań. Każde zdanie jest następnie wypisywane na konsolę.

    Moderacja zdań: Dla każdego zdania z listy, klient wysyła żądanie POST do https://api.openai.com/v1/moderations z kluczem API uzyskanym z pliku properties. Odpowiedzi z tych żądań są analizowane i wyniki moderacji są zapisywane na liście moderationResults.

    Wysyłanie odpowiedzi: Klient tworzy i wysyła żądanie POST do https://zadania.aidevs.pl/answer/{token} z wynikami moderacji jako ciałem żądania. Status odpowiedzi na to żądanie jest następnie wyświetlany na konsoli.