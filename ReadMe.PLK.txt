<I am Unicode File!>

Patcher & Monitor połączeń TCP/IP typu Half Open

Nazwa Projektu:	TCP-Z  (TCP-Z Monitor Sieci)
Obsł. Systemy Oper.:	Windows XP/2003/2008/Vista/Windows 7, Wszystkie SP*, Wszystkie 32bit (x86) / 64bit (x64)
Autor:		deepxw#126.com
Blog:		http://deepxw.lingd.net/article-1415261-1.html
		http://deepxw.blogspot.com   (English)

Podwyższ limit połączeń TCP half-open (niekompletnych wychodzących), Uwolnij potęgę swojej sieci, ściągaj szybciej i więcej w tym samym czasie.

Cechy:
1) Bezpieczny oraz prosty w użyciu: Modyfikuje Tcpip.sys w pamięci. Zmiany są natychmiastowe; bez potrzeby uruchamiania komputera ponownie.

2) Szeroka Kompatybilność: Wyszukuje offset, który jest odpowiedzialny za limit poprzez sygnaturę w pliku, dzięki temu uaktualnienia i poprawki MS nie wpływają na jego pracę.
   Wspiera wszystkie wersje Windows, które posiadają limit half-open.

3) Profesjonalne Zestawienie: TCP-Z pokazuje liczbę nawiązanych połączeń; połączeń typu half open; Tworzonych Głęboko, Prędkość ściągania / wysyłania w czasie rzeczywistym. 
Posiada również możliwość pokazywania zdarzeń ostrzegawczych na minutę, takich jak przekroczona ilość połączeń TCP typu half-open.

*******************
*  Sposób użycia  *
*******************
1) Ręczny: 
Użyj Interfejsu graficznego (GUI) aplikacji tcpz.exe / tcpz64.exe aby zmodyfikować limitowaną wartość.

Pomimo wyjścia/zakończenia programu TCP-Z, zmodyfikowana wartość pozostanie w użyciu (w pamięci kernela) aż do
ponownego uruchomienia/wyłączenia komputera.

Jest to tymczasowe rozwiązanie, jako, że każde ponowne uruchomienie systemu przywróci starą, domyślną wartość.
Musisz modyfikować limitowaną wartość po każdym uruchomieniu..


Naciśnij ten przycisk, aby zastosować nową wartość.

2) Automatycznie: 
Zainstaluj TCP-Z Virtual Device aby patchować w trybie cichym (ukrytym). 

Virtual Device to także patch w pamięci kernela, jednak jest bardziej automatyczny, na takiem samej zasadzie jak patchowanie pliku.

Modyfikuje limitowaną wartość bez interakcji użytkownika. Użyj Menadżera Urządzeń aby dopasować maksymalną wartość.

Sterownik wystarczy zainstalować raz, a limit half-open będzie zmieniony wg. twoich ustawień..
Limit będzie modyfikowany przy każdym starcie systemu, do momentu odinstalowania sterownika TCPZ Virtual Device.

Powinien działać nawet po zainstalowaniu Service Packa dla Windowsa; nie ma potrzeby ponownej instalacji sterownika.

Instaluj, lub Odinstaluj.
32bity, uruchom program jako administrator: "TCPZ_Setup-x86.exe".
64bity, uruchom program jako administrator: "TCPZ_Setup-x64.exe"


Dwie wersje TCP-Z mogą być uruchomione niezależnie, możesz wybrać jedną z nich.

Jeśli chcesz patchować plik tcpip.sys bezpośrednio, użyj narzędzia "Universal Tcpip.sys Patch".


* Skróty klawiszowe
Przełącz pomiedzy zakładkami		Ctrl + Tab
Przełącz pomiędzy wartościami		Tab
Potwierdź				Space
Zrzut okna TCP-Z do pliku		F5
Zrzut całego ekranu do pliku 		F6
 
* Wiersz poleceń
tcpz.exe  -limit:200
tcpz.exe  -limit:200  -autoexit
tcpz.exe  -minimize

Jeśli program antywirusowy blokuje ładowanie sterownika tcp-z i powoduje błąd przy uruchomieniu tcp-z, możesz pominąć ładowanie sterownika uruchamiając tcp-z z parametrem :
tcpz.exe  -nodriver

Jednak bez sterownika tracisz możliwość modyfikowania limitu w pamięci kernela.



****************************************
*  Najczęstsze problemy i rozwiązania  *
****************************************
1, Aby używać trzybu graficznego, kliknij prawym na tcpz.exe, wybierz 'uruchom jako administrator'.

2, W Systemach 64bitowych Vista/Win7, musisz włączyć tryb TESTSIGNING. 
Otwórz wiersz poleceń jako administrator, uruchom poniższe komendy:
bcdedit.exe -set loadoptions DDISABLE_INTEGRITY_CHECKS
bcdedit.exe -set TESTSIGNING ON
Zrestartuj komputer, aby zmiany odniosły efekt.
Powyższe komendy wystarczy uruchomić raz.
Jeśli na pulpicie będzie znak wodny "Test Mode", możesz go usunąć poprzez "RemoveWatermarkX64.exe".

Systemy 32-bitowe - nie ma potrzeby stosowania powyższego.

3, Jeśli program wykona nieprawidłową operację, przy następnym uruchomieniu zgłosi błąd ładowania sterownika. musisz uruchomić poniższą komendę:
32bit:
REG DELETE HKLM\SYSTEM\CurrentControlSet\Services\tcpz-x86
64bit:
REG DELETE HKLM\SYSTEM\CurrentControlSet\Services\tcpz-x64

Usuń ten wpis w rejestrze: [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Enum\Root\LEGACY_TCPZ-X86]
Zrestartuj komputer, Uruchom aplikację ponownie, aby sprawdzić czy problem został rozwiązany.

Niektóre programy antywirusowe zablokują ładowanie sterownika TCP-Z, należy ustawić regułę ignorowania/dodania do zaufanych w ustawieniach antywirusa aby umożliwić poprawne ładowanie się sterownika TCP-Z.

4, W Windows XP możliwy jest patch zarówno pliku, jak i pamięci. W Vista/Windows 7 tylko patch pamięci.

5, Jeśli patchujesz plik tcpip.sys w Windows XP x64, powinieneś użyć 64bitowej wersji TCPZ64.exe.

6, Windows 2003/2008 nie ma limitów.

7, Vista / Windows 7 obługują nieskończoną wartość w Sterowniku TCP-Z Virtual Driver. Ustaw limitowaną wartość na zero (0), oznacza ona nieskończoność.

//Historia:
2008.09.14
  * Update to Unicode version, supports English/Chinese Simple/Chinese Traditional.

2008.09.21
  + Add a new installer.
  * Driver: Increased one finding action. Improve success rate.

2008.10.13
  + Support read limited value from tcpip.sys of Windows 7.

2008.10.23  V1.5.3.15
  + Read & display create depth from tcpip.sys.
  + Windows 7 M1 memory patch.
  * Can't read information from a few of net interface.

2008.10.30  V1.5.5.20
  + Windows 7 M3 (x86) memory patch.
  + Add warning message for AMD multi-core CPU user.

2008.11.01  V1.5.6.25
  + Windows 7 M3 (x64) memory patch. (Beta)
  * Windows XP file limited change to 1000.
  * Modified function of disable SFC in NT5.
  
2008.11.07  V2.0.0.30 beta
  * Modified all search function. Improve success rate.

2008.11.12  V2.1.0.33
  + Add tcpz64.exe, a native x64 program.
  * Modify search function.
  * Memory Limited of XP up to 1000.
  * Fix: compatibility of multi-core CPU.
  * Fix: fail to load driver in Windows 7 x64.

2008.11.29  V2.2.0.35
  + Virtual drive, add an option to custom limited value. Add an Unlimited option for Vista / Windows 7.
  + GUI program, capture screen by hot-key F5 / F6. It needs GDI+ support.
  * GUI program, add Vista UAC manifest. May not be compatible with XP SP2, you can upgrade Service Pack, or continue to use the V2.1 version of TCP-Z. 
  * GUI program be changed to a single file, portable version.

2008.12.16  V2.2.1.36
　* Modify TcpzQueryRegParameters(), Add a null parameter iNullAction, Avoid NOD32 report as virus.
　
2008.12.27  V2.3.0.42
　* Change digital signature of program files.
　+ GUI program, modify UI, add a beautiful skin.
　+ GUI program, display limited address in kernel memory, and file “Tcpip.sys”.
　  For compatibility, only display low part in 64bit OS.
　* Fixed: unknown file limited value in Windows 7 Build 6.1.6936.0, and Windows 2003 5.2.3790.4331.
　* Fixed: file patch Fail in windows XP SP3, because unable disable WFP.
　# Drivers has no changes.

2008.12.29  V2.3.1.43
  * GUI program, Remove the function of disable WFP, because Compatibility of this code is not so good.
    And because there is no disabled SFC, patch file will not to a 100% success, because Windows will automatically resume tcpip.sys.
    Another way, use Memory patch method.

2009.01.08  V2.4.0.46
  + Windows 7 x64 6.1.7000.0 Memory Patch.
  + GUI program, support keyboard control. Thank Aldares. 
                 Ctrl + Tab = switch tab; Tab = switch control.
  * GUI program, File Patch, improve compatibility of disable WFP in Windows XP. Thank BRD-IlLusioN-CCCP. 
  * GUI program, fixed, user interface in non-standard DPI can not correctly display. 

2009.02.05, V2.5.1.50
  * GUI program, identify whether tcpip.sys is the original file without modification.
  * GUI program, supports Windows XP x64 SP1 early version.
  * GUI program & Drivers, supports Windows Vista SP2 RC v.275, x64, 6.0.6002.16659.

2009.03.07, V2.6.0.64 Beta
  + Support more language. German by http://Mods.sub.cc; Italian by FSoft; Polish by PrEzi; Romanian by Misaki-kun & StelistCristi. Thank them.
  + Statistics of incoming and outgoging attempts...
  + Statistics of connections by each program.
  + Mini bar;
  + function of change the alignment of peak label.
  + Save setting at exit.

2009.03.16 V2.6.0.66
  + Support more language. Bulgarian by ExaFlop; Swedish by Marshall Mathers; Thai by Pruthisith; Turkish by Yekta Kayman; Ukraine by ShriEkeR. Thank them!

2009.04.06 V2.6.1.72
  + Support more language. Russian by Serhii Hlodin, Mixa, Qui Sum; Korean by deuxdoom; French by jacklours; Portugese by Anubis. Thank them!
  + Add options in tcpz.ini to customize the upper value of the graph.
  * Fixed: Y-axis label display not correct in big font. Error range of incoming connection graph.
  * Fixed: Transparence percentage display not correct.
  * Fixed: Can't display speed in some computer.
  * Fixed: Network traffic turn to zero when more than 4GB.
  * Fixed: Can't receive the shutdown message.
  * Build with WDK 6001.18002.

2009.04.09 V2.6.2.75
  * Hide the tunnel type of Adapter in Vista/Windows 7.
  * Increase the range of searcher, supports Windows 7 6.1.7077.0 (winmain_win7rc.090404-1255), x86.
