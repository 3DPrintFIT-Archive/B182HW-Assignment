# X-ends

Vaším úkolem bude namodelovat mírně zjednodušené koncové součástky na X osu tiskáren podobného stylu jako jsou tiskárny RebeliX, se kterými se setkáte v předmětu.

## Odevzdání a termíny

**Toto je beta verze zadání.**
To znamená, že dojde jen k opravě chyb nebo k dopřesnění nejasností.
Případné opravy budou opatřeny erratou.

Založte repozitář: **TBD**

Deadline odevzdání je **TBD**.
Vypracovaný úkol nahrajte do repozitáře vytvořeného na odkaze výše.
Nikam jinam jej neposílejte, jako odevzdání se počítá to,
co bude ve vašem repozitáři (ve výchozí větvi (většinou master))
v momentu deadlinu.

Pokud máte jakékoliv dotazy, či naleznete chyby, napište je prosím do
[Issues](TBD) v tomto repozitáři.

Po pushnutí commitu do vašeho repozitáře proběhne sada testů.
Testy vyžadují optickou kontrolu.

## Rozhraní

Váš model implementujte jako modul v OpenSCADU s tímto rozhraním:

```scad
module x-ends(
        vertical_rod_distance,
        vertical_horizontal_smooth_offset,
        wall_thickness,
        base_height,
        body_height,
        linear_bearing_hole,
        tr_nut_hole,
        tr_nut_mounting_holes,
        m3_hole,
        m3_nut,
        m3_nut_thickness,
        m3_head_diameter,
        smooth_rod_hole,
        x_smooth_rod_distance,
        split_width,
        pulley_inset,
        pulley_distance_from_bottom_rod,
        motor_size,
        motor_hole_distance,
        motor_offset,
        endstop_inset,
    )
{
    // ...
}
```

Smíte (je to dokonce žádoucí) vytvářet další pomocné moduly.
Smíte vytvářet další pomocné soubory (ale není to potřeba).

Váš modul musí jít použít následujícím způsobem z jiného souboru ve vašem
kořenovém adresáři vašeho repozitáře:

```scad
use <x-ends.scad>

x-ends();
```

Výchozí hodnoty argumentů musí zůstat zachovány dle tohoto rozhraní!
Naše testy budou jednotlivé argumenty nastavovat,
ale budou předpokládat stejné výchozí hodnoty!


## Parametry

Vámi namodelovaný model se bude skládat ze dvou částí: _motor_ a _idler_.
Pomocí argumentu `show_motor` (respektive  `show_idler`) lze zobrazení těchto
částí vypnout (respektive zapnout).
Nezobrazení jedné části nemá vliv na pozici části zobrazené.

Všechny další parametry udávají rozměry jednotlivých součástí dle přiložených
výkresů.


## Umístění v souřadném systému
Pro automatické testy je naprosto zásadní,
aby váš model byl umístěn na správném místě.
**Modely umístěné špatně budou vyhodnoceny jako nesprávné.**
Věnujte proto umístění modelu zvýšenou pozornost.

**TBD**

## Výkresy

Byť máte za úkol modelovat jen dvě součástky, výkresy jsou tři. To je z důvodu, že obě dvě součástky sdílejí většinu rozměrů.
Na výkresu [báze](drawings/base_drawing.pdf) najdete právě tyto sdílené rozměry.

## Idler (část _idler_)
Výkres [idleru](drawings/idler_drawing.pdf).

## Motor (část _motor_)
Výkres [motoru](drawing/motor_drawing.pdf).


## Obě části
**TBA**

## Nefunkční požadavky

  - Manipulace s `$f*` hodnotami je zakázána
  - Je zakázáno použít konstrukci `minkowski()` (ve 3D i ve 2D prosotoru)
  - Není doporučováno používat rekurzi, ani to k vyřešení úkolu není zapotřebí
  - Využití externích knihoven (včetně knihovny MCAD) je zakázáno
  - Pokud je něco **zakázáno**, vede použití k tomu, že **neprojdou testy** a dostáváte **0 bodů**
  - Váš kód musí splňovat určitou kvalitu (**tato část tvoří 5 bodů z celkových 30 možných**)
    - Opakování v kódu je špatně, vždy použijte moduly a cykly
    - Bulharské konstanty musí být doplněny o vysvětlující komentář
    - Dodržte logickou úroveň odsazení

s