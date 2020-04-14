# Tvořím Web od A do Z: Podklady pro 10. lekci

## Příklady

- [Formuláře](priklady/01-formulare)
- [Tabulky](priklady/02-tabulky)

## Formuláře

Formuláře tvoří oblast webdesignu, kde se spolu nejblíže potkávají uživatelé, kódéři (frontendisti) a programátoři (backendisti). Protože každý uživatel internetu dříve nebo později narazí na formulář, ani my se jim nemůžeme vyhnout. A že na formulář narazíte na internetu záhy, dokládá [tato stránka](https://google.cz) – ano i tak vypadá formulář. Formuláře znáte také z přihlašovacích stránek, kam vyplňujete své uživatelské jméno a heslo. Prostřednictvím formulářů přidáváte komentáře na Facebooku (nebo jinde), tweetujete anebo třeba nahráváte fotku.

Příklad jednoduchého formuláře.

```html
<form action="prihlaseni.py" method="POST">
    <label for="username">Uživatelské jméno</label>
    <input id="username" type="text" name="user" required>
    <label for="pwd">Heslo</label>
    <input id="pwd" type="password" name="password" required>
    <button>Přihlásit</button>
</form>
```

Můžeme z něj vyčíst následující: po uživateli chceme aby vyplnil své uživatelské jméno a heslo, oba údaje jsou povinné (atribut `required`). Údaje z formuláře se odešlou do souboru `prihlaseni.py`, který se nachází v téže složce jako soubor s přihlašovacím formulářem (zpracovávat je bude programovací jazyk Python – přípona `.py`).

Zobecnit tyto informace můžeme následovně: jazyk HTML je jazykem značkovacím, a neumí tudíž zpracovat formulářová data, o to se musí postarat nějaký programovací jazyk (JavaScript, Java, PHP, Python). Značka `form` má proto atribut `action`, jehož hodnotou je cesta (popřípadě celá URL) k souboru s obslužným programem. Pokud chceme data z formuláře odeslat skrytě, zvolíme metodu `POST` (prostřednictvím atributu `method` na značce `form`). Výchozí metoda `GET` totiž připojí formulářová data přímo k URL z `action`. Ta jsou pak viditelná, a tudíž snado zcizitelná.

Více o formulářích na výborně zpracovaném [Marksheet.io](https://marksheet.io/html-forms.html) (anglicky). Zde jen pár poznámek.

### Input

Základním stavebním kamenem formulářů jsou prvky `input`. Pomocí atributu `type` ovlivníme nejen jeho výslednou podobu (checkbox, radio, range, color), ale i to, jaké uspořádání bude mít klávesnice zobrazená na dotykovém zařízení. Užitím vhodného typu vstupního pole tak můžeme návštěvníkovi naší stránky významnou měrou usnadnit práci s formulářem. A to by nám mělo jít v první řadě.

### Nenuťte mně přemýšlet aneb přístupnost

Vyplňování formulářů vyžaduje od uživatelů jisté úsilí, které bychom měli co nejvíce snížit. [Nenuťte mně přemýšlet](https://www.knihydobrovsky.cz/kniha/nenutte-uzivatele-premyslet-85047) říká v originále Steve Krug a tím shrnuje do jednoduché věty velmi komplexní zadání pro kódéry formulářů. Protože udělat něco jednoduchého k užívání může být pěkně složité. A naopak zesložitit něco prostého se dá velmi jednoduše. Proto při kódování formulářů buďte obezřetné a dbejte základních pravidel.

1. Vstupní pole (`input`) je vždy doprovázeno popiskem `label`. Obě jsou pak propojena přes shodnou hodnotu atributu `for` (u `label`) a `id` (u `input`). Výjimkou je `input` typu `hidden`.
2. Pečlivě volte typ vstupního pole (atribut `type`). Vhodným použitím uživatelům vyplňování zpříjemníte, naopak nevhodným je pěkně otrávíte.
3. Pokud žádáte nějaké údaje (datum narození, telefon), vysvětlete **proč** je chcete (datum narození, kvůli statistice; telefon, abychom vám mohli zavolat v případě problému) a **jak** je mají uživatelé zadat (datum narození – stačí nám rok a měsíc, telefonní číslo v mezinárodním formátu).
4. Chybně vyplněná pole označte a hlavně vysvětlete, v čem je chyba.

### Focus

**Prvek na stránce, který v danou chvíli přijímá vstup z klávesnice, má _focus_.** Focus tak mohou získat jen některé prvky, konkrétně formulářové prvky a odkazy. Po těchto _focusovatelných_ prvcích se lze pohybovat pomocí klávesy <kbd>Tab</kbd> (při současném stisku <kbd>Shift</kbd> směrem vzad). Mezerníkem nebo klávesou <kbd>Enter</kbd>/<kbd>Return</kbd> pak spustíte na daném prvku akci (zaškrtnete políčko, stisknete tlačítko, prokliknete odkaz).

Vyplňte si [cvičný formulář](http://udacity.github.io/ud891/lesson2-focus/01-basic-form/), hledejte:

- zpáteční letenku
- do Melbourne
- odlet 28. září 2020
- návrat 8. října 2020
- místo u okénka
- nechcete spam

Pozor, myší to nejde ☺.

---

## Tabulky v HTML

Tabulky se v HTML vytvářejí dost těžkopádně, přesto je třeba se s nimi seznámit, protože kromě výpisu tabulkových dat se stále hojně využívají v tvorbě HTML e-mailů.

```html
<table>
    <thead>
        <tr>
            <th>záhlaví 1. sloupce</th>
            <th>záhlaví 2. sloupce</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>1. řádek v 1. sloupci</td>
            <td>1. řádek v 2. sloupci</td>
        </tr>
        <tr>
            <td>2. řádek v 1. sloupci</td>
            <td>2. řádek v 2. sloupci</td>
        </tr>
    </tbody>
</table>
```

Vnitřní struktura tabulky kopíruje strukturu prvku `html`, obsahuje prvky `thead`, `tbody` v nichž se nacházejí samotné řádky tabulky (`tr`). Do řádků tabulky se umisťují výhradně prvky `th` (v záhlaví, `thead`) nebo `td` (uvnitř `tbody`), ty pak představují jednotlivé buňky tabulky.

Pozor, uvnitř prvku `td` (resp. `th`) mohou být zanořeny libovolné další prvky (s výjimkou `html`, `head` a `body`), a to včetně dalších tabulek (kdysi se tak stavěly webové stránky…)!