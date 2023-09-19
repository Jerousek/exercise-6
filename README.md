[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-8d59dc4de5201274e310e4c54b9627a8934c3b88527886e3b421487c677d23eb.svg)](https://classroom.github.com/a/j6wVnL9A)
[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-c66648af7eb3fe8bc4f294546bfd86ef473780cde1dea487d3c4ff354943c9ae.svg)](https://classroom.github.com/online_ide?assignment_repo_id=10587086&assignment_repo_type=AssignmentRepo)
# Exercise 06 - Liga Mistrů - spojový seznam

Pokračujte v projektech z minulého cvičení a nahraďte v knihovně použití pole za ADS spojový seznam. Spojový seznam bude realizovat všechny požadované operace, které definují základní rozhraní v C# pro třídy kolekcí dat. Ačkoliv spojový seznam rozhodně není polem (resp. obecně přímo indexovatelnou datovou strukturou)
je v rámci procvičení realizováno i rozhraí **IList**

## Postup
* Projekty (obsah složek) **ChampionsLeague** a **ChampionsLeagueLibrary** nahraďte hotovými projekty z minulého cvičení
* Projekt **ChampionsLeagueLibraryTests** neměňte! Obsahuje nové jednotkové testy.
* Realizujte spojový seznam v souboru **ObjectLinkedList.cs**
  * Vytvořte třídu **ObjectLinkedList**
	* třída implicitně realizuje rozhraní **ICollection**, **IEnumerable**, **IList** (z ns **System.Collections** - NEgenerické varianty!)
	* realizujte všechny vlastnosti a metody vyžadované předepsanými rozhraními
	* interní struktura spojového seznamu je acyklický obousměrně zřetězený seznam bez hlavy
	  * třída pro reprezentaci jednoho uzlu v seznamu by neměla být vidět mimo třídu **ObjectLinkedList**
	* pro realizaci není dovoleno použít jiné kolekce z knihovny .NET, ani z jiné externí knihovny
	* veškeré výjimky jsou nahrazeny "no-op" stylem - místo výjimky se nic nestane! v případě návratových hodnot se vrací null
	* vlastnosti kolekcí **IsSynchronized** = false, **SyncRoot** = this, **IsFixedSize** = false, **IsReadOnly** = false
	* **indexer** - indexuje se od nuly do počtu prvků - 1
	* **Remove** - odebírá první shodný (**Equals**) prvek
	* **Insert** - umožňuje vložení pouze na platné indexy uprostřed seznamu + začátek + konec seznamu
	  * pokus o přidání na záporné indexy nebo indexy za koncem seznamu neprovádí nic (žádný prvek se nepřidá)
	  * prázdný seznam ```[]``` - je dovoleno pouze
	  	* ```Insert(0, x)``` - ```[x]``` 
	  * seznam s jedním prvkem ```[x]``` - jsou přípustné následující varianty
	  	* ```Insert(0, y)``` - vložení na začátek seznamu - ```[y, x]```
	  	* ```Insert(1, y)``` - vložení na konec seznamu - ```[x, y]```
	  * seznam se dvěma prvky ```[x, y]``` - jsou přípustné následující varianty
	  	* ```Insert(0, z)``` - ```[z, x, y]```
	  	* ```Insert(1, z)``` - ```[x, z, y]```
	  	* ```Insert(2, z)``` - ```[x, y, z]```
	  * obdobně pro seznamy s větším počtem prvků
* Ve třídě **PlayerRecords** 
  * Změňte typ atributu **players** na **ObjectLinkedList**, upravte všechny reference na atribut a obnovte původní funkcionalitu
  * Doplňte implicitní realizaci rozhraní **IEnumerable** (ns **System.Collections**); volání metody delegujte na atribut **players**
