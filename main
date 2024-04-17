#include <iostream>
#include <windows.h>
#include <conio.h>

using namespace std;

HANDLE konsola; // Uchwyt do konsoli

// Funkcja rysująca obszar tekstowy
void rysujObszar()
{
    COORD pozycja = { 10, 10 };
    SetConsoleTextAttribute(konsola, BACKGROUND_GREEN | BACKGROUND_BLUE | FOREGROUND_RED | FOREGROUND_GREEN | FOREGROUND_BLUE);
    for (int i = 0; i < 25; ++i)
    {
        SetConsoleCursorPosition(konsola, pozycja);
        cout << " ";
        pozycja.X++;
    }
    SetConsoleTextAttribute(konsola, 0);
}

// Funkcja obsługująca wejście użytkownika
void obslugaWejscia()
{
    SetConsoleTextAttribute(konsola, BACKGROUND_GREEN | BACKGROUND_BLUE | FOREGROUND_RED | FOREGROUND_GREEN | FOREGROUND_BLUE);
    COORD pozycja = { 10, 10};
    int kodZnaku = 0;
    SetConsoleCursorPosition(konsola, pozycja);

    while ((kodZnaku = _getch()) != 27) // 27 to kod klawisza ESC
    {
        if (kodZnaku == 224) // Klawisze specjalne, wstęp do klawiszy strzałek
        {
            
            kodZnaku = _getch(); // Pobieranie kodu klawisza strzałki
        }

        switch (kodZnaku)
        {
        case 75: // Lewo
            if (pozycja.X > 5)
            {
                pozycja.X--;
                SetConsoleCursorPosition(konsola, pozycja);
            }
            break;
        case 77: // Prawo
            if (pozycja.X < 29)
            {
                pozycja.X++;
                SetConsoleCursorPosition(konsola, pozycja);
            }
            break;
        case 8: // Backspace
            if (pozycja.X > 5)
            {
                pozycja.X--;
                SetConsoleCursorPosition(konsola, pozycja);
                cout << " ";
                SetConsoleCursorPosition(konsola, pozycja);
            }
            break;
        default:
            // Drukowanie znaków drukowanych
            if (kodZnaku >= 32 && kodZnaku <= 126 && pozycja.X < 34)
            {
                cout << char(kodZnaku);
                pozycja.X++;
            }
        }
    }

    SetConsoleTextAttribute(konsola, 0);
    cout << "\nWyjście z programu...\n";
}

int main()
{
    konsola = GetStdHandle(STD_OUTPUT_HANDLE); // Pobranie uchwytu konsoli
    rysujObszar();
    obslugaWejscia();
    return 0;
}
