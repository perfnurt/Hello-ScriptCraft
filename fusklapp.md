[PDF för utskrift](https://gitprint.com/carlrobert/Hello-ScriptCraft/blob/master/fusklapp.md)

Några byggkommandon i ScriptCraft som kan köras inifrån Minecraft:
```javascript
box(material)
box(material, bredd, höjd, djup)
box0(material)
box0(material, bredd, höjd, djup)
prism(material, bredd, längd)
prism0(material, bredd, längd)
cylinder(material, radie, höjd)
cylinder0(material, radie, höjd)
signpost([textrad1, textrad2])
```
När man kör kommandon skall `material` bytas ut mot ett Minecraft-material. 
`bredd`, `höjd`, `djup`, `längd` och `radie` ska bytas ut mot siffror. 
`textrad1` och `textrad2` ska bytas ut mot textsträngar.
Exempel på hur man kör:
```javascript
/js box('41', 4, 7, 3)
/js prism('35:14', 6, 10)
/js cylinder(blocks.oak, 10, 2)
/js signpost(['Hello', 'World!'])
```
Funkar det inte? Kolla att du använt raka citattecken, som sitter på samma knapp som asterisken (*) på svenska tangentbord.

Exempel på hur man kör program som andra användare gjort:
```javascript
/js rainbow(30) 
/js maze(5, 7) 
/js dancefloor(10, 8)
```
Gör ett eget program! Skriv in denna kod i en texteditor:
```javascript
var Drone = require('drone');
function mitthus() {
	var drone = this;
	drone.box('41', 10, 1, 10);
}
Drone.extend('mitthus', mitthus);
```
Gör en egen mapp, t.ex. `SpigotMC/Scriptcraft/plugins/Kalle`
Spara filen som `mitthus.js` i din nya mapp. Kör ditt program inifrån Minecraft genom att skriva:
```javascript
/js refresh()
/js mitthus()
```
Drönaren kan använda alla byggkommandon och dessutom flytta på sig. Flyttkommandon som drönaren kan använda:
```javascript
up(antalBlock)    down(antalBlock)
left(antalBlock)  right(antalBlock)
fwd(antalBlock)   turn(antalVridningar)
```
Ändra koden genom att lägga till de nya raderna:
```javascript
var Drone = require('drone');
function mitthus() {
 	var drone = this;
	drone.box('41', 10, 1, 10);
	// Nytt!
	drone.up();
	drone.box('20', 10, 2, 10);
	drone.up(2);
	drone.box('152', 10, 1, 10);
	// Slut på det nya
}
Drone.extend('mitthus', mitthus);
```
Spara dina ändringar och gör ```/js refresh()```. Kör sedan programmet igen.

#### Felsökningstips
Använd ```/js <tabbtangent>```
för att se alla tillgängliga kommandon. Om ```mitthus()``` saknas i listan är något fel. Kolla felutskrifter i svarta fönstret; de syns inte i chatten.

Använd F3 i chatten för att se koordinater. Testa kod i chatten genom att skriva den en rad i taget:
```javascript
/js var b = self.world.getBlockAt(219,64,102) // blocket nås nu via b
/js b // se blockets egenskaper
/js b.typeId // blockmaterial
/js b.data // färg på t.ex. blocks.wool
```

[PDF för utskrift](https://gitprint.com/carlrobert/Hello-ScriptCraft/blob/master/fusklapp.md)

*Testade versioner: CanaryMod 1.2.0 (Minecraft 1.8+), scriptcraft-3.1.1*
