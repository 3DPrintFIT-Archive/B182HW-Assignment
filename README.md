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
module x_ends(
	base_height = 7,
	body_height = 60,
	wall_thickness = 3,
	vertical_horizontal_rods_offset = 23,
	tr_nut_hole = 12.5,
	tr_nut_mount_hole = 16,
	vertical_rods_distance = 25,
	smooth_rod_hole = 8.1,
	linear_bearing_hole = 15,
	split_width = 1,
	layer_height = 0.15,
	bolt_hole_diameter = 3.3,
	nut = 5.6,
	nut_thickness = 2.5,
	x_smooth_rods_distance = 45,
	pulley_inset = 10,
	pulley_distance_from_bottom_rod = 45/2,
	motor_size = 42.3,
	motor_hole_distance = 31,
	motor_offset = 3,
	endstop_inset = 7,
	endstop_distance_from_bottom_rod = 12,
	small_bolt_hole = 1.9,
	bolt_head_height = 3,
	bolt_head_diameter = 6,
	show_motor = true,
	show_idler = true
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
Věnujte proto umístění modelu zvýšenou pozornost, požadovanou pozici najdete ve výkresech ([svg](drawings/position.svg), [png](drawings/position.svg.png)).


## Výkresy

Byť máte za úkol modelovat jen dvě součástky, výkresy jsou tři. To je z důvodu, že obě dvě součástky sdílejí většinu rozměrů.
Na výkresu báze ([svg](drawings/base_drawing.svg), [png](drawings/base_drawing.svg.png)) najdete právě tyto sdílené rozměry.
Dále máte k dispozici obrázky projekcí této základní součástky ([svg](drawings/base_projections.svg), [png](drawings/base_projections.svg.png)), případně jsou k dispozici také jen okótované výkresy bez projekcí  ([svg](drawings/base_dimensions.svg), [png](drawings/base_dimensions.svg.png)).

## Idler (část _idler_)
Výkres [idleru](drawings/idler_drawing.pdf).

## Motor (část _motor_)
Výkres [motoru](drawing/motor_drawing.pdf).


## Obě části
Výkresy obou částí dohromady jsou vidět na výkresech vyznačující jejich pozici v souřadném systému ([svg](drawings/position.svg), [png](drawings/position.svg.png)).

## Nefunkční požadavky

  - Manipulace s `$f*` hodnotami je povolena pouze pro konstrukci pravidelných šestiúhelníků (např. pro matičky)
  - Je zakázáno použít konstrukci `minkowski()` (ve 3D i ve 2D prosotoru)
  - Není doporučováno používat rekurzi, ani to k vyřešení úkolu není zapotřebí
  - Využití externích knihoven (včetně knihovny MCAD) je zakázáno
  - Pokud je něco **zakázáno**, vede použití k tomu, že **neprojdou testy** a dostáváte **0 bodů**
  - Váš kód musí splňovat určitou kvalitu (**tato část tvoří 5 bodů z celkových 30 možných**)
    - Opakování v kódu je špatně, vždy použijte moduly a cykly
    - Bulharské konstanty musí být doplněny o vysvětlující komentář
    - Dodržte logickou úroveň odsazení