[![Open in Gitpod](https://gitpod.io/button/open-in-gitpod.svg)](https://gitpod-redirect-0.herokuapp.com/)

# Manettes et claviers (chapitre 8.1)

Avant de commencer. Consulter les instructions à suivre dans [instructions.md](instructions.md)

## Appareils d'entrée/sortie 

Dans cette série d'exercices, nous utiliserons un clavier MIDI comme au chapitre 7.2, mais en sortie plutôt qu'en entrée. Nous utiliserons aussi une manette de jeu (de style Xbox) en entrée grâce à la librairie [inputs](https://pypi.org/project/inputs/).

## 1. Associations MIDI, notes et accords

Dans les exercices du chapitre 7.2, Nous avons vu généré un dictionnaire d'association entre des notes et des numéros MIDI, ainsi que des accords avec des notes. En réutilisant `build_note_dictionaries` du chap 7.2, nous allons maintenant charger ces éléments à partir d'un fichier JSON avec une structure particulière. Nous allons ensuite bâtir nos associations de notes MIDI grâce au contenu des dictionnaires.

Au lieu d'avoir ceci dans le code:
```python
english_names = ["C", "Db", "D", "Eb", "E", "F", "F#", "G", "Ab", "A", "Bb", "B"]
solfeggio_names = ["Do", "Réb", "Ré", "Mib", "Mi", "Fa", "Fa#", "Sol", "Lab", "La", "Sib","Si"]
chords = {
	"Do majeur" : ("Do", "Mi", "Sol"),
	"Fa majeur" : ("Fa", "La", "Do"),
	"Sol majeur" : ("Sol", "Si", "Ré"),
	"La mineur" : ("La", "Do", "Mi")
}
```
Nous avons un JSON comme ceci:
Exemple :
```json
{
  "english_names": [ "C", "Db", "D", "Eb", "E", "F", "F#", "G", "Ab", "A", "Bb", "B" ],
  "solfeggio_names": [ "Do", "Réb", "Ré", "Mib", "Mi", "Fa", "Fa#", "Sol", "Lab", "La", "Sib", "Si" ],
  "chords": {
    "Do majeur": [
      "Do3",
      "Mi3",
      "Sol3"
    ],
    "Fa majeur": [
      "Do3",
      "Fa3",
      "La3"
    ],
    "Sol majeur": [
      "Si2",
      "Ré3",
      "Sol3"
    ],
    "La mineur": [
      "Do3",
      "Mi3",
      "La3"
    ]
  }
}
```

## 2. Configuration d'actions sur boutons de manettes

Il faut suivre la démonstration faite en classe. Voici les étapes :

### 2.1. Structure d'un fichier INI

Les fichiers INI sont un format de fichiers de configuration assez simple dans lequel on a des sections qui contiennent des valeurs de configuration. La syntaxe est la suivante :

```ini
[section1]
param1 = la valeur du param1
param2 = la valeur du param2

[section2]
foo = 42
bar = 1337
qux = hello world
```

Pour lire ces fichiers, on peut utiliser le module standard [configparser](https://docs.python.org/3/library/configparser.html). On veut ultimement avoir un fichier qui associe un bouton de manette de jeu à une note ou un accord à envoyer au piano. Par exemple : 

```ini
[gamepad]
BTN_TR = Do4
BTN_SOUTH = Do majeur
BTN_WEST = Ré mineur
BTN_EAST = La mineur
BTN_NORTH = Sol majeur
```

### 2.2. Construire des callbacks à appeler sur des boutons

### 2.3. Charger la configuration et exécuter un code