FitTrack
Aplicació web per a membres i personal d'un gimnàs. Projecte Intermodular, DAW (IFC33C-DAW), CIFP Pau Casesnoves. Equip: Noah Amengual, Adam Doblas, Guillem Antoni Balaguer Torrens.

Estat: UT02 (disseny i viabilitat). Última actualització: 22-11-2026.
Dossier complet: PDF «FitTrack · Dossier de projecte (UT01 + UT02)». Les referències A1-A6 i B0-B10 d'aquest fitxer apunten a les seves seccions. Enllaç al dossier al repositori: [pendent de pujar-lo i d'afegir-ne l'enllaç aquí].

Llegenda: [Fet] contrastat amb font · [Hipòtesi] no contrastat · [Pendent] cal una comprovació o un permís.

1. Necessitat i públic
Els membres d'un gimnàs volen gestionar des del mòbil reserves i consultes i veure l'ocupació abans d'anar-hi. [Hipòtesi: consulta informal a deu persones, data exacta per indicar]
Públic: membres (usuaris principals) i personal del gimnàs. El client seria el gimnàs. La demo es planteja per a un gimnàs gran fictici.
No hi ha cap evidència documentada que els membres vulguin evitar anar al gimnàs o contactar-hi directament. No s'ha d'assumir aquesta motivació; la necessitat és la que consta a les línies anteriors.
Tret diferencial: l'ocupació de màquines, més útil en gimnasos grossos. [Hipòtesi]
2. MVP vigent (primera versió)
Web senzilla amb servidor, dades guardades i dos perfils (membre i personal). Tres funcionalitats:

Ocupació simulada: el membre veu l'aforament general i l'estat lliure/ocupat de les màquines, amb hora d'actualització i la indicació «dades simulades».
Reserves d'activitats: el membre reserva i cancel·la; el personal gestiona activitats i places; mai es supera la capacitat.
Consultes o peticions: el membre envia una consulta i en veu l'estat o la resposta; el personal la revisa i hi respon.
Fora de l'abast ara: sensors reals, pagaments, accés digital o torniquets, aplicació nativa, gestió de vendes, dades reals d'ocupació, ús en diversos gimnasos (SaaS).
Roadmap, subjecte a validació: accés digital, pagaments, compra de material, dades reals, SaaS multi-centre.
Ordre de retallada si falta temps: primer l'estat per màquina (es manté l'aforament general), després el seguiment d'estat de les consultes. Reserves i perfils no es retallen.

3. Decisions vigents
Decisió	Estat	Detall al dossier
MVP web amb dades simulades (no sensors ni temps real)	Decidit a la UT01	A4
Les tres funcionalitats es mantenen	Decidit a la UT02	B0, B2
Tecnologia: web adaptable, servidor Node.js i base de dades relacional (MySQL). Sense framework definitiu	Validada per la prova P1+P2 (22-11-2026): servidor Node.js, MySQL i reserva de l'última plaça. Sense framework definitiu	B0 fila 4, B5
L'ocupació s'actualitza per consulta periòdica, no per sockets	Provisional	B0 fila 4
Sense Flutter ni IoT a l'MVP	Decidit	B5 (D8)
Persistència dins l'MVP; les dades reals d'ocupació queden per a més endavant	Decidit (corregeix A1)	B0 fila 1
Regles de negoci provisionals
Proposades amb ajuda de la IA i acceptades per l'equip com a punt de partida. Es revisaran durant la construcció de l'MVP i amb la validació amb un gimnàs. Detall a B7.

Àrea	Regla provisional
Autenticació	Registre de membres amb correu i contrasenya; contrasenyes desades amb hash; comptes de personal creats manualment, amb un únic nivell de permisos
Reserves	Un membre pot reservar diverses activitats però només una vegada cada una; pot cancel·lar fins a l'inici; sense llista d'espera; el personal no pot reduir les places per sota de les reserves existents
Ocupació simulada	La genera el servidor automàticament; el personal no l'edita; el nombre de màquines i l'interval d'actualització s'acorden en dissenyar les dades
Consultes	Un text i una resposta; dos estats (oberta i respondida); sense categories ni notificacions
Client de la demo	Un gimnàs gran fictici
4. Hipòtesis i dubtes
Interès real dels usuaris: la mostra és petita i informal (F1).
Que l'equip pugui construir servidor, base de dades i API amb Node.js i MySQL (F6, D1): [Fet] prova P1 superada el 22-11-2026 (Annex A del dossier).
Reserves sense superar places amb peticions simultànies (D2): [Fet] prova P2 superada el 22-11-2026; de dues peticions sobre l'última plaça, una s'accepta i l'altra es rebutja.
Cap gimnàs col·laborador ni permís per a dades reals (F5, D7): [Pendent], no condiciona l'MVP.
Ajudes (Govern de les Illes Balears 2025-2027, CDTI NEOTEC 2026): possibilitat sense comprovar (F8). No es compten com a ingrés.
Protecció de dades personals abans de qualsevol dada real (F10): [Hipòtesi]. De moment, dades de prova fictícies.
5. Fonts principals (detall i dates a B1)
NTT DATA · CrossHero (consultat 30-10-2026) · Technogym Mywellness CRM · Agència Tributària (model 036, facturació, impost sobre societats) · Seguretat Social i SEPE · INSST · Govern de les Illes Balears (ajudes d'innovació i digitalització 2025-2027) · CDTI (NEOTEC 2026).

6. Fases, recursos i cost (resum)
Fases: F1 base de disseny · F2 prova tècnica · F3 disseny d'interfície · F4 construcció de l'MVP · F5 qualitat i proves · F6 documentació i lliurament (B3).
Recursos: les tres persones, ordinadors, repositori Git, Node.js, base de dades relacional, dades simulades. Allotjament de la demo en local per defecte; servei extern pendent (B4).
prova-tecnica/: servidor mínim i script de la prova P1+P2 (reserva simultània de l'última plaça), superada el 22-11-2026 amb Node.js 26.13.1 i MySQL 8.0.43 (Annex A del dossier). Ordre d'execució: npm install express mysql2, carregar schema.sql a MySQL, node server.js (amb la variable DB_PASSWORD si MySQL té contrasenya) i node test.js.
Cost: hipòtesi de 60 h per persona, 15 €/h d'exemple, 2.700 € en temps de persones; despesa real entre 0 i 15 €. No cal finançament extern per a l'MVP (B6).
7. Qualitat
Controls definits al dossier (B8): integritat de les reserves, estat simulat identificat, accés segons perfil, persistència, ús en mòbil, accessibilitat dels formularis, seguretat bàsica i coherència documental.

8. Dades i interaccions (esquema inicial, no arquitectura definitiva)
Camps principals per entitat (inicials, poden canviar):

Usuari: nom, correu, contrasenya (hash), rol (membre o personal).
Activitat: nom, data i hora, places totals i places lliures.
Reserva: usuari, activitat, estat. Un usuari no pot reservar dues vegades la mateixa activitat.
Màquina: nom, zona, estat (lliure o ocupada), hora d'actualització.
Aforament: persones dins, capacitat, hora d'actualització.
Consulta: autor, text, estat (oberta o respondida), resposta, dates.
Relacions i interaccions a B7.

9. Pendents i preguntes obertes
Data i mida real de la consulta a deu persones.
Disponibilitat d'un gimnàs per validar.
Validar les regles de negoci provisionals (secció 3).
Freqüència d'actualització i nombre de màquines de l'ocupació simulada.
Opció d'allotjament de la demo.
Tarifa horària de classe.
Requisits de protecció de dades.
Vigència de les ajudes.
Data i canal de lliurament (la docent ho confirma; revisió prevista 23-11-2026).
Mecanisme de sessions d'usuari (cookie de sessió o token) i algorisme que genera l'ocupació simulada. No estan definits.
10. Per a una IA o una persona nova
Llegeix aquest fitxer sencer. Conté les decisions vigents.
Si una dada és [Hipòtesi] o [Pendent], no la tractis com a confirmada. Node.js i MySQL han superat la prova P1+P2, però encara no hi ha framework definitiu ni arquitectura definitiva.
Si una decisió essencial no hi és, indica-ho en lloc d'endevinar-la.
La prova P1+P2 ja està feta. Primer pas d'implementació previst: partir d'aquell servidor mínim i construir perfils (membre i personal, aquest amb un únic nivell de permisos) i autenticació, i després reserves, ocupació simulada i consultes (fases F3-F4).
