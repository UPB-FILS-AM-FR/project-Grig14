# Automatic Color Object Sorter

## Description

Ce projet consiste en la realisation d'un trieur automatique d'objets par couleur.

Le systeme utilise un capteur de couleur pour detecter la couleur dominante d'un petit objet place dans la zone de lecture. Les valeurs mesurees sont traitees par un microcontroleur Arduino, qui determine la categorie de l'objet: rouge, vert, bleu ou inconnu.

Apres la detection, le systeme actionne un mecanisme controle par servomoteurs afin d'orienter l'objet vers le compartiment correspondant. Un ecran OLED affiche l'etat du systeme, la couleur detectee et le nombre d'objets tries.

Le systeme inclut aussi des boutons pour lancer un cycle de tri, remettre les compteurs a zero ou entrer en mode calibration. Un buzzer et des LEDs fournissent un retour sonore et visuel.

## Motivation

Ce projet a ete choisi parce qu'il combine plusieurs aspects importants des systemes embarques: lecture de capteurs, traitement des donnees, controle de moteurs, affichage local et interaction avec l'utilisateur.

Il s'inspire des systemes industriels de tri automatique, utilises pour separer des objets selon leurs proprietes physiques. Une version reduite permet de comprendre le principe de fonctionnement avec des composants accessibles.

Le projet est aussi adapte a une demonstration pratique, car le resultat est directement visible: un objet est detecte, sa couleur est reconnue, puis il est dirige vers le bon compartiment.

## Architecture

Le systeme est controle par un Arduino Uno ou Arduino Nano.

Le capteur de couleur mesure les composantes rouge, verte et bleue reflechies par l'objet. Ces donnees sont envoyees au microcontroleur, qui les compare avec des seuils definis ou calibres.

En fonction de la couleur detectee, l'Arduino controle les servomoteurs pour orienter la rampe ou la trappe de tri. L'ecran OLED affiche les informations utiles, tandis que les LEDs et le buzzer indiquent l'etat du systeme.

```text
[Objet colore]
      |
      v
[Capteur de couleur]
      |
      v
[Arduino Uno/Nano]
      |
      |----> [Servomoteurs]
      |          tri mecanique
      |
      |----> [Ecran OLED]
      |          couleur + statistiques
      |
      |----> [LEDs + Buzzer]
      |          feedback utilisateur
      |
      <---- [Boutons]
                start / reset / calibration
## Components

| Device | Usage | Price |
| --- | --- | --- |
| Arduino Uno ou Arduino Nano | Microcontroleur principal | ~35 RON |
| Capteur de couleur TCS34725 ou TCS3200 | Detection de la couleur de l'objet | ~20 RON |
| Servomoteurs SG90 ou MG90S | Orientation de la rampe ou de la trappe | ~15 RON x2 |
| Ecran OLED SSD1306 128x64 I2C | Affichage de l'etat du systeme | ~25 RON |
| Boutons poussoirs | Start, reset et calibration | ~2 RON x3 |
| Buzzer passif | Signal sonore | ~4 RON |
| LED RGB ou 3 LEDs simples | Signal visuel | ~3 RON |
| Resistances 220 ohm | Protection des LEDs | ~1 RON |
| Resistances 10k ohm | Pull-up/pull-down pour boutons | ~1 RON |
| Breadboard | Prototypage du circuit | ~10 RON |
| Fils jumper | Connexions | ~10 RON |
| Cable USB | Programmation et alimentation | ~10 RON |
| Alimentation externe 5V | Alimentation des servomoteurs | ~20 RON |
| Materiel mecanique | Structure du trieur | carton / 3D print |

## Libraries

| Library | Description | Usage |
| --- | --- | --- |
| Wire | Communication I2C | OLED et capteur TCS34725 |
| Adafruit TCS34725 | Lecture du capteur de couleur | Detection RGB |
| Adafruit SSD1306 | Driver pour l'ecran OLED | Affichage |
| Adafruit GFX | Bibliotheque graphique | Texte et elements visuels |
| Servo | Controle des servomoteurs | Mecanisme de tri |
