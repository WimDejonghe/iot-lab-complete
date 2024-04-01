---
mathjax:
  presets: '\def\lr#1#2#3{\left#1#2\right#3}'
---

# Transistoren.

Als de maximale uitgangsstroom niet voldoende is om een verbruiker te laten werken (voorbeeld om een relais aan te sturen, of een andere verbruiker), dan wordt hier gebruik gemaakt van een transistor. De transistor bezit de functie om het vermogen te leveren aan de verbruiker wat de Output-pin van de microcontroller niet kan. Een andere reden waarom een transistor wordt gebruikt is dat de digitale uitgang van een microcontroller geen open-collector uitgang is, maar een actieve uitgangstrap. Zoals eerder vermeld kan bij dergelijke uitgangen geen andere voedingsbron worden gebruikt dan de VCC van het IC. En aangezien de meeste relais (of andere verbruikers) op een hogere spanning werken dan 5V, kan dit ook opgelost worden met een transistorschakeling.

Er zijn twee type transistoren: NPN en PNP. De symbolen van beide is terug te vinden in de figuur. Voor eenvoudige toepassingen zoals deze waarbij een relais moet worden aangestuurd vanuit een Output-pin van de microcontroller, volstaat een NPN transistor.  

![example image](./images/transistor.png "An exemplary image")

De aansluitklemmen zijn:
**Basis**, **Emitter** en **Collector**.  

![Symbool van een NPN-en PNP-transistor.](./images/tr.png "Symbool van een NPN-en PNP-transistor.")

Let op de pijl op de emitter. De stroom kan enkel in die richting vloeien, vandaar dat een transistor enkel kan gebruikt worden in DC-toepassingen.

Er zijn twee stromen van toepassing bij de transistor. De basisstroom (*Ib*) en de collectorstroom (*Ic*). In de emitter vloeit de som van beide stromen.

![example image](./images/hfe.png "An exemplary image")

De stroom versterkingsfactor *hFE* (beta) is de verhouding van de collectorstroom op de basisstroom. 

:::warning
Een transistor zal, indien mogelijk, er steeds voor zorgen dat de collectorstroom hFE keer groter is dan de basisstroom. 
:::

Een transistor bezit een vaste hFE. Dit kan met bepaalde meettoestellen worden bemeten. Binnen een bepaald type kan volgens de datasheet de hFE veel veranderen (grote spreiding) in waarde van transistor tot transistor.  

$$\h_{FE} = \frac{I_{C}} {I_{B}}$$

De basis-emitter spanning UBE is zoals een diode in doorlaat een spanning van 0,6V.

## Transistor als schakelaar  

Een transistor is een stroomversterker. Het component zal altijd, in de mate van het mogelijke, de basis-stroom versterken met een factor hFE. En deze te laten vloeien als de collector-stroom. 

* Indien de basis-stroom wordt overgedimentioneerd (een te grote stroom), komt het heel regelmatig voor dat de transistor in saturatie komt. Dit wil zeggen dat de verhouding niet meer opgaat, omdat een zo'n grote collector-stroom er niet kan vloeien (stroom wordt dan beperkt door andere elementen in de collector-kring). Op dat moment kan de transistor beschouwt worden als een gesloten schakelaar (tussen collector en emitter). De spanning tussen collector - emitter is dan gedaald tot bijna nul (UCE = 0V).

* Indien er echter totaal geen stroom vloeit in de basis, dan kan er ook geen stroom vloeien in de collector. In zo'n situatie kan de transistor vergeleken worden met een open schakelaar (tussen collector en emitter). De volledige bronspanning staat dan over de collector - emitter (Uce = Ubron).

Een transistor wordt in zo'n situaties veel toegepast. Er kan gesteld worden dat de transistor nu functioneert als een elektronische schakelaar. De bediening gebeurt echter niet manueel, maar door al dan niet een basis-stroom te sturen. Geen basis-stroom = open schakelaar (er kan een IC vloeien), teveel basis-stroom = gesloten schakelaar (er kan geen IC vloeien).

Een elektronische schakelaar (transistor, thyristor, mosfet, ...) bezit veel voordelen t.o.v. een klassieke mechanische schakelaar.  Als belangrijkste voordelen kan vernoemd worden:

*  veel kortere schakeltijden.
*  veel hogere schakelfrequenties.
*  compacter voor eenzelfde schakelvermogen.
*  bedrijfszekerder en duurzamer door het ontbreken van bewegende delen.

Een ideale elektronische schakelaar bezit onderstaande eigenschappen:

*  Raan = 0 ohm, in gesloten toestand is er bijgevolg geen spanningsverschil over de contacten. Saturatie van de transistor door grote Ib.
*  Ruit = oneindig ohm, in open toestand vloeit er geen stroom. De volledige bronspanning staat over de contacten. Cutt-Off van de transistor door Ib = 0.
*  schakelt zonder vertraging.
*  bezit een klein stuurvermogen.
*  is compact.
*  is betrouwbaar en duurzaam.

De collector-emittor overgang simuleert het schakelcontact van een gewone mechanische schakelaar.  UCE is de spanning over de contacten van de schakelaar. Zie formule. 

![example image](./images/tralssch.png "An exemplary image")

![example image](./images/form1.png "An exemplary image")

Zolang Ube kleiner is dan ongeveer 0,5 V wordt de transistor niet gestuurd en blijft hij bijgevolg gesperd. De basisstroom $ Ib $ is dan 0 en ook de collectorstroom $ Ic $ is 0. Zie formule \ref{eq:TR2}.

![example image](./images/form2.png "An exemplary image")

Door de schakelaar vloeit geen stroom en over zijn contacten staat de volle voedingsspanning.  Dit zijn de eigenschappen van een open schakelaar.

Als Ube groter wordt dan 0,6 V wordt de transistor gestuurd.  We zorgen ervoor dat hij volledig wordt uitgestuurd of gesatureerd is door Ib voldoende groot te kiezen.  In het ideale geval is UCE nu gelijk aan 0 V.  Over de contacten staat geen spanning en de stroom wordt enkel bepaald door de belastingsweerstand.  Dit zijn de eigenschappen van een gesloten schakelaar. Dit kan getekend worden in een XY-assenstelsel. (X = spanning over de transistor UCE, Y = collectorstroom Ic). Ideale schakelkarakteristiek van een bipolaire transistor. Zie figuur.

![example image](./images/trschakelkar.png "An exemplary image")

In punt A is: Ic = Uv/Rc en UCE =  0 V.  - Gesloten schakelaar - . Het opgenomen vermogen Pd = UCE. Ic = 0.Ic = 0 W .

In punt B is: UCE = Uv en Ic is 0A.  - Open schakelaar -. Het opgenomen vermogen Pd = UCE. Ic = Uv.0 = 0 W.

Het opgenomen vermogen in beide toestanden van de schakelaar is bijgevolg 0 W.  Tijdens het schakelen zelf neemt de transistor echter wel een zeker vermogen op omdat er bij de overgang van A naar B, of omgekeerd, wel stroom vloeit.

Als er rekening wordt gehouden met het niet-ideaal zijn van de transistor wil dit zeggen dat er in saturatie toch een kleine spanning over de collector-emitter staat en dus niet gelijk is aan 0V. Deze spanning is echter zeer klein en hangt af van type/soort transistor. Deze is weergegeven in de karakteristiek .

![example image](./images/schakelkar.png "An exemplary image")

In punt A, bij gesloten schakelaar, is er wel een kleine spanning UCEsat over de transistor waardoor de collectorstroom kleiner is dan de waarde bepaald door de voedingsspanning en de collectorweerstand.
Bij bipolaire transistors houden we normaal rekening met een UCEsat van 0,3 V of lager; bij MOSFETS is deze spanning te verwaarlozen en rekenen we met 0 V.

In punt B, bij open schakelaar, vloeit er een kleine sperstroom I.  Het gevolg hiervan is dat de weerstand van de schakelaar geen oneindig is, maar een zekere waarde bezit.  Bij bipolaire transistors is de lekstroom in de orde van enkele µA, of nog kleiner, zodat de weerstand verschillende Mega ohm kan bedragen.  Bij MOSFETS is de lekstroom in de orde van nA zodat de weerstand kan oplopen tot miljoenen Mega ohm.

Er wordt hier eens een volledig ontwerp uitgewerkt waarbij de transistor werkt als elektronische schakelaar. Zie figuur .

![example image](./images/trschakeling.png "An exemplary image")

We moeten een bepaalde waarde van collectorweerstand in serie met de led schakelen omdat de voedingsspanning te hoog is voor de led.  We moeten uiteraard de waarde van die weerstand kunnen berekenen.  Vervolgens moeten we de grootte van de basisweerstand berekenen die er zal voor zorgen dat de basisstroom en bijgevolg de collectorstroom voldoende groot is.

We kiezen voor een transistor van het type BC547.  In het vademecum vinden we voor UCEsat : 0,4 V en hFE = 200.  Bemerk dat we de minimale waarde van hFE kiezen zodat we zeker zijn dat de transistor in verzadiging komt.  Door de led wensen we een stroom van 10 mA en over de LED staat een spanning van 1,6 V.

De waarde van de collectorweerstand berekenen we uit :

![example image](./images/form3.png "An exemplary image")  

De nodige basisstroom om deze collectorstroom te verkrijgen wordt gevonden met de formule \ref{eq:TR4}.

![example image](./images/form4.png "An exemplary image")  

We kunnen nu tenslotte de grootte van de basisweerstand berekenen met de formule \ref{eq:TR5}.

![example image](./images/form5.png "An exemplary image")  

Belangrijk is nog dat we bij het schakelen van een inductieve belasting, een relais bvb. (principewerking van een relais/contactor: zie figuur \ref{relais}), een diode moeten schakelen parallel over de belasting zoals getekend in figuur.

![example image](./images/trrelais.png "An exemplary image")  

Uit de wet van Lenz weten we dat bij het uitschakelen een zeer hoge inductiespanning kan ontstaan, die op de collector van de transistor terecht komt.  Deze inductiespanning zal de transistor in de meeste gevallen vernietigen.  Zo een diode noemen we een vrijloopdiode.

![example image](./images/contactor_relay.png "An exemplary image")  

Om het geheel nog duidelijker te maken en om een idee te hebben van de werkelijke waarden van de parameters berekenen we een volledige schakeling.  We werken met het basisschema van figuur met de LED.
De schakeling werkt op een voedingsspanning van 30 V en we wensen een collectorstroom van 150 mA.
Voor de parameters van de transistor kiezen we: Icsper = 0,1µA, hFEmin = 50, UBEsat =0,75 V en UCEsat =0,4 V.
We berekenen: Rc, Ib, Rb, Pdsat, Pdsper, Rcesat en Rcesper.

![example image](./images/form6.png "An exemplary image")  

## Praktisch: ESP32

Stel dat een verbruiker (werkspanning = 5V) moet worden aangestuurd vanuit een digitale outputpin van de ESP32. 
Er kunnen zich twee toestanden voordoen: 
>- Outputpin is laag (0V) => transistor in cut-off toestand (vgl. met open schakelaar)
>- Outputpin is hoog (3,3V) => transistor in saturatie toestand (vgl. met gesloten schakelaar)

Dit is weergegeven in volgende figuren:

![Een transistor in Cut-off.](./images/esp2.png "Een transistor in Cut-off.") 
![Een transistor in saturatie.](./images/esp1.png "Een transistor in saturatie.") 

Een transistor wordt in saturatie en cut-off veel toegepast. Men noemt dit de transistor als schakelaar en functioneert als een elektronische schakelaar. De bediening gebeurt echter niet manueel, maar door al dan niet een basis-stroom te sturen.
* Geen basis-stroom = open schakelaar (er kan geen IC vloeien) -> Cut-off;
* Te veel basis-stroom = gesloten schakelaar (IC die vloeit is maximum) -> Saturatie.

De collector-emittor overgang simuleert het schakelcontact van een gewone mechanische
schakelaar.

![Links een transistor in saturatie en rechts in cut-off.](./images/tr_toestand.png "Links een transistor in saturatie en rechts in cut-off.") 

