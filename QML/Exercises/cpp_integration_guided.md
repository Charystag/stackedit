## **Exercice 1 : Créer et Enregistrer une Classe C++ Simple**

#### **Objectif :**
Créer une classe C++ simple et l'exposer à QML.

#### **Étape 1 : Définir une Classe C++ avec des Propriétés**

1. **Créez un fichier d'en-tête (`counter.h`) pour définir une classe `Counter` avec une propriété `count`.**

```cpp
#ifndef COUNTER_H
#define COUNTER_H

#include <QObject>

class Counter : public QObject {
    Q_OBJECT

    // Expose la propriété 'count' à QML
    Q_PROPERTY(int count READ count WRITE setCount NOTIFY countChanged)

public:
    explicit Counter(QObject *parent = nullptr);

    // Getter pour la propriété 'count'
    int count() const;

    // Setter pour la propriété 'count'
    void setCount(int value);

signals:
    // Signal émis lorsque la valeur de 'count' change
    void countChanged();

private:
    int m_count;
};

#endif // COUNTER_H
```

2. **Créez un fichier d'implémentation (`counter.cpp`) pour définir les méthodes de `Counter`.**

```cpp
#include "counter.h"

Counter::Counter(QObject *parent) : QObject(parent), m_count(0) {
    // Initialisation de 'm_count' à 0
}

int Counter::count() const {
    return m_count;
}

void Counter::setCount(int value) {
    if (m_count != value) {
        m_count = value;
        emit countChanged(); // Émet le signal lorsque 'count' change
    }
}
```

**Explications :**
- **Q_PROPERTY** : Expose la propriété `count` à QML, permettant ainsi de la lire (`READ count`) et de la modifier (`WRITE setCount`).
- **Signals** : Utilise `countChanged` pour notifier QML lorsque la propriété change, assurant une mise à jour réactive de l'interface utilisateur.

**Documentation :**
- [QObject](https://doc.qt.io/qt-6/qobject.html)
- [Q_PROPERTY](https://doc.qt.io/qt-6/properties.html)

#### **Étape 2 : Enregistrer la Classe avec `qmlRegisterType()` dans `main.cpp`**

1. **Modifiez `main.cpp` pour enregistrer la classe `Counter` et la rendre disponible dans QML.**

```cpp
#include <QGuiApplication>
#include <QQmlApplicationEngine>
#include "counter.h"

int main(int argc, char *argv[]) {
    QGuiApplication app(argc, argv);
    QQmlApplicationEngine engine;

    // Enregistrement de la classe Counter pour la rendre disponible dans QML
    qmlRegisterType<Counter>("MyApp", 1, 0, "Counter");

    const QUrl url(u"qrc:/main.qml"_qs);
    engine.load(url);

    return app.exec();
}
```

**Explications :**
- **`qmlRegisterType<Counter>("MyApp", 1, 0, "Counter")`** : Enregistre la classe `Counter` sous le nom `Counter` dans le module QML `MyApp`, version 1.0.

**Documentation :**
- [qmlRegisterType](https://doc.qt.io/qt-6/qqmlengine.html#qmlRegisterType)

#### **Étape 3 : Instancier la Classe dans QML et Lier les Propriétés à des Éléments UI**

1. **Créez un fichier `main.qml` pour instancier `Counter` et lier ses propriétés à une interface utilisateur.**

```qml
import QtQuick 6.7
import QtQuick.Controls 6.7
import MyApp 1.0

ApplicationWindow {
    visible: true
    width: 400
    height: 200
    title: "Exemple avec Counter"

    Column {
        anchors.centerIn: parent
        spacing: 20

        Counter {
            id: counter
            count: 10 // Initialisation de la valeur
        }

        Slider {
            from: 0
            to: 100
            value: counter.count
            onValueChanged: counter.count = value
        }

        Text {
            text: "Valeur actuelle : " + counter.count
            font.pointSize: 20
        }
    }
}
```

**Explications :**
- **`Counter`** : Instancie la classe `Counter` dans QML et initialise `count` à 10.
- **`Slider`** : Le `Slider` contrôle la valeur de `count`, permettant de modifier cette valeur en glissant le curseur.
- **`Text`** : Affiche la valeur actuelle de `count`, liée dynamiquement à l'instance de `Counter`.

**Documentation :**
- [Slider](https://doc.qt.io/qt-6/qml-qtquick-controls-slider.html)
- [Text](https://doc.qt.io/qt-6/qml-qtquick-text.html)
