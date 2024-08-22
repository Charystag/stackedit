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

---

## **Exercice 2 : Utilisation de `QML_ELEMENT` pour Simplifier l'Enregistrement**

#### **Objectif :**
Apprendre à utiliser la macro `QML_ELEMENT` pour enregistrer une classe dans QML de manière simplifiée.

#### **Étape 1 : Modifier la Classe pour Ajouter `QML_ELEMENT`**

1. **Modifiez le fichier `counter.h` de l'exercice précédent pour inclure `QML_ELEMENT`.**

```cpp
#ifndef COUNTER_H
#define COUNTER_H

#include <QObject>
#include <QtQml/qqml.h>  // Inclusion nécessaire pour utiliser QML_ELEMENT

class Counter : public QObject {
    Q_OBJECT
    QML_ELEMENT // Expose automatiquement cette classe à QML

    // Propriété exposée à QML
    Q_PROPERTY(int count READ count WRITE setCount NOTIFY countChanged)

public:
    explicit Counter(QObject *parent = nullptr);

    int count() const;
    void setCount(int value);

signals:
    void countChanged();

private:
    int m_count;
};

#endif // COUNTER_H
```

2. **Modifiez le fichier d'implémentation `counter.cpp` pour rester conforme à l'exercice précédent.**

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
- **`QML_ELEMENT`** : Cette macro, ajoutée à la classe `Counter`, expose automatiquement cette classe à QML sans nécessiter d'enregistrement manuel via `qmlRegisterType`. Cela simplifie l'intégration entre C++ et QML, surtout pour les projets où de nombreuses classes doivent être exposées à QML.

**Documentation :**
- [QML_ELEMENT](https://doc.qt.io/qt-6/qtqml-cppintegration-exposecppattributes.html#qml-element)
- [QObject](https://doc.qt.io/qt-6/qobject.html)

#### **Étape 2 : Supprimer l'Appel à `qmlRegisterType()` dans `main.cpp`**

1. **Modifiez le fichier `main.cpp` pour supprimer l'appel à `qmlRegisterType`.**

```cpp
#include <QGuiApplication>
#include <QQmlApplicationEngine>
#include "counter.h"

int main(int argc, char *argv[]) {
    QGuiApplication app(argc, argv);
    QQmlApplicationEngine engine;

    // Plus besoin de qmlRegisterType<Counter>("MyApp", 1, 0, "Counter");
    // grâce à l'utilisation de QML_ELEMENT

    const QUrl url(u"qrc:/main.qml"_qs);
    engine.load(url);

    return app.exec();
}
```

**Explications :**
- **Suppression de `qmlRegisterType`** : Comme la classe `Counter` est maintenant automatiquement enregistrée grâce à `QML_ELEMENT`, l'appel manuel à `qmlRegisterType` devient superflu et peut être retiré.

**Documentation :**
- [QQmlApplicationEngine](https://doc.qt.io/qt-6/qqmlapplicationengine.html)

#### **Étape 3 : Vérifier l'Utilisation de la Classe dans QML**

1. **Maintenez le fichier `main.qml` de l'exercice précédent. La classe `Counter` devrait fonctionner sans problème.**

> :bulb: Il est cependant nécessaire de retirer l'import du module MyApp vu que nous ne le définissons plus dans notre 
> fichier `main.cpp`

```qml
import QtQuick 6.7
import QtQuick.Controls 6.7

ApplicationWindow {
    visible: true
    width: 400
    height: 200
    title: "Exemple avec Counter et QML_ELEMENT"

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
- **Vérification** : Si la classe `Counter` fonctionne correctement dans le fichier QML sans avoir besoin de `qmlRegisterType`, cela confirme que `QML_ELEMENT` a été utilisé avec succès pour simplifier l'enregistrement.

**Documentation :**
- [Slider](https://doc.qt.io/qt-6/qml-qtquick-controls-slider.html)
- [Text](https://doc.qt.io/qt-6/qml-qtquick-text.html)

**Résultat Attendu :** Familiarité avec l'utilisation de `QML_ELEMENT` pour simplifier l'enregistrement des types C++ dans QML, ce qui réduit le code nécessaire dans `main.cpp` et simplifie le processus de développement.

---

## **Exercice 3 : Exposer des Fonctions C++ à QML**

#### **Objectif :**
Apprendre à exposer des méthodes d'une classe C++ à QML en utilisant `Q_INVOKABLE`.

#### **Étape 1 : Ajouter une Méthode Simple à la Classe C++**

1. **Modifiez le fichier `counter.h` pour ajouter une méthode `increment()` à la classe `Counter`.**

```cpp
#ifndef COUNTER_H
#define COUNTER_H

#include <QObject>
#include <QtQml/qqml.h>

class Counter : public QObject {
    Q_OBJECT
    QML_ELEMENT // Expose automatiquement cette classe à QML

    // Propriété exposée à QML
    Q_PROPERTY(int count READ count WRITE setCount NOTIFY countChanged)

public:
    explicit Counter(QObject *parent = nullptr);

    int count() const;
    void setCount(int value);

    // Méthode exposée à QML pour incrémenter la valeur de count
    Q_INVOKABLE void increment();

signals:
    void countChanged();

private:
    int m_count;
};

#endif // COUNTER_H
```

2. **Implémentez la méthode `increment()` dans le fichier `counter.cpp`.**

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

void Counter::increment() {
    setCount(m_count + 1); // Incrémente la valeur de 'count'
}
```

**Explications :**
- **`Q_INVOKABLE`** : Cette macro expose la méthode `increment()` à QML, ce qui permet de l'appeler directement depuis le code QML. Cette méthode permet d'incrémenter la valeur de `count` en l'augmentant de 1.

**Documentation :**
- [Q_INVOKABLE](https://doc.qt.io/qt-6/qtqml-cppintegration-exposecppattributes.html#q-invokable)
- [QObject](https://doc.qt.io/qt-6/qobject.html)

#### **Étape 2 : Appeler la Méthode depuis QML**

1. **Modifiez le fichier `main.qml` pour appeler la méthode `increment()` lorsque l'utilisateur clique sur un bouton.**

```qml
import QtQuick 6.7
import QtQuick.Controls 6.7

ApplicationWindow {
    visible: true
    width: 400
    height: 200
    title: "Appel de Méthode C++ depuis QML"

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

        Button {
            text: "Incrémenter"
            onClicked: counter.increment() // Appel de la méthode C++ incrémenter
        }
    }
}
```

**Explications :**
- **`onClicked: counter.increment()`** : Cette ligne de code QML appelle la méthode `increment()` de la classe C++ `Counter` lorsque l'utilisateur clique sur le bouton. Cela augmente la valeur de `count` de 1 à chaque clic, ce qui est ensuite automatiquement reflété dans l'interface utilisateur grâce à la liaison de données en QML.

**Documentation :**
- [Button](https://doc.qt.io/qt-6/qml-qtquick-controls-button.html)
- [Signal Handlers in QML](https://doc.qt.io/qt-6/qtqml-syntax-signals.html)

**Résultat Attendu :** Après cet exercice, vous devriez être capable d'appeler des méthodes C++ directement depuis QML, en utilisant `Q_INVOKABLE`. Cela vous permet de créer des interactions plus complexes entre l'interface utilisateur en QML et la logique d'affaires implémentée en C++.

---

## **Exercice 4 : Utiliser des Slots comme Fonctions QML**

#### **Objectif :**
Apprendre à exposer des slots C++ en tant que fonctions appelables depuis QML.

#### **Étape 1 : Modifier la Méthode pour qu'elle Devienne un Slot Public**

1. **Modifiez le fichier `counter.h` pour changer la méthode `increment()` de `Q_INVOKABLE` à un slot public.**

```cpp
#ifndef COUNTER_H
#define COUNTER_H

#include <QObject>
#include <QtQml/qqml.h>

class Counter : public QObject {
    Q_OBJECT
    QML_ELEMENT // Expose automatiquement cette classe à QML

    // Propriété exposée à QML
    Q_PROPERTY(int count READ count WRITE setCount NOTIFY countChanged)

public:
    explicit Counter(QObject *parent = nullptr);

    int count() const;
    void setCount(int value);

public slots:
    // Slot public exposé à QML
    void increment();

signals:
    void countChanged();

private:
    int m_count;
};

#endif // COUNTER_H
```

2. **Le fichier d'implémentation `counter.cpp` reste inchangé car l'implémentation de la méthode ne change pas.**

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

void Counter::increment() {
    setCount(m_count + 1); // Incrémente la valeur de 'count'
}
```

**Explications :**
- **`public slots:`** : Le mot-clé `slots` dans une section publique de la classe expose la méthode `increment()` en tant que slot, ce qui permet de l'utiliser de manière similaire à une méthode marquée avec `Q_INVOKABLE`, mais avec l'avantage d'être connectable à d'autres signaux, y compris des signaux QML.

**Documentation :**
- [Slots](https://doc.qt.io/qt-6/signalsandslots.html#slots)

#### **Étape 2 : Connecter le Slot aux Événements QML**

1. **Modifiez le fichier `main.qml` pour connecter le slot `increment()` à un événement QML, comme un clic sur un bouton.**

```qml
import QtQuick 6.7
import QtQuick.Controls 6.7

ApplicationWindow {
    visible: true
    width: 400
    height: 200
    title: "Utilisation des Slots comme Fonctions QML"

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

        Button {
            text: "Incrémenter"
            onClicked: counter.increment() // Appel du slot C++ incrémenter
        }
    }
}
```

**Explications :**
- **`onClicked: counter.increment()`** : Ce code QML appelle le slot `increment()` de la classe C++ `Counter` lorsque le bouton est cliqué. En transformant la méthode en un slot, vous avez non seulement la possibilité de l'appeler depuis QML, mais aussi de la connecter directement à d'autres signaux, offrant ainsi une plus grande flexibilité.

**Documentation :**
- [Button](https://doc.qt.io/qt-6/qml-qtquick-controls-button.html)
- [Signal Handlers in QML](https://doc.qt.io/qt-6/qtqml-syntax-signals.html)

**Résultat Attendu :** Vous devriez maintenant comprendre comment utiliser des slots comme des alternatives aux méthodes marquées avec `Q_INVOKABLE`. Cette approche vous permet de bénéficier de la puissance des signaux et slots de Qt tout en offrant une interaction fluide entre C++ et QML.

---

## **Exercice 5 : Gérer les Changements de Propriété avec des Signaux**

#### **Objectif :**
Implémenter des signaux pour notifier QML lorsque des propriétés changent en C++, afin de maintenir la synchronisation entre les deux.

#### **Étape 1 : Ajouter un Signal pour les Changements de Propriété**

1. **Modifiez le fichier `counter.h` pour vous assurer que le signal `countChanged` est correctement défini et associé à la propriété `count`.**

```cpp
#ifndef COUNTER_H
#define COUNTER_H

#include <QObject>
#include <QtQml/qqml.h>

class Counter : public QObject {
    Q_OBJECT
    QML_ELEMENT // Expose automatiquement cette classe à QML

    // Propriété exposée à QML avec un signal pour notifier les changements
    Q_PROPERTY(int count READ count WRITE setCount NOTIFY countChanged)

public:
    explicit Counter(QObject *parent = nullptr);

    int count() const;
    void setCount(int value);

signals:
    // Signal émis lorsque la propriété 'count' change
    void countChanged();

public slots:
    void increment();

private:
    int m_count;
};

#endif // COUNTER_H
```

2. **Implémentez le setter dans le fichier `counter.cpp` pour qu'il émette le signal `countChanged` chaque fois que la valeur de `count` change.**

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

void Counter::increment() {
    setCount(m_count + 1); // Incrémente la valeur de 'count'
}
```

**Explications :**
- **Signal `countChanged`** : Ce signal est utilisé pour notifier QML que la propriété `count` a changé, ce qui déclenche une mise à jour de l'interface utilisateur si cette propriété est liée à un élément UI.

**Documentation :**
- [Q_PROPERTY](https://doc.qt.io/qt-6/properties.html)
- [Signals and Slots](https://doc.qt.io/qt-6/signalsandslots.html)

#### **Étape 2 : Utiliser le Mot-Clé `NOTIFY` dans `Q_PROPERTY`**

1. **Le mot-clé `NOTIFY` dans `Q_PROPERTY` est déjà utilisé correctement dans la déclaration de la propriété `count` :**

```cpp
Q_PROPERTY(int count READ count WRITE setCount NOTIFY countChanged)
```

- **Explications** : Le mot-clé `NOTIFY` indique à QML quel signal doit être émis lorsque la propriété `count` change. Cela permet à QML de réagir automatiquement aux changements de la propriété.

**Documentation :**
- [NOTIFY in Q_PROPERTY](https://doc.qt.io/qt-6/properties.html#notifying-property-changes)

#### **Étape 3 : Lier des Éléments UI à la Propriété dans QML**

1. **Modifiez le fichier `main.qml` pour lier des éléments UI à la propriété `count` et observer les mises à jour automatiques.**

```qml
import QtQuick 6.7
import QtQuick.Controls 6.7

ApplicationWindow {
    visible: true
    width: 400
    height: 200
    title: "Mise à jour Automatique avec des Signaux"

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

        Button {
            text: "Incrémenter"
            onClicked: counter.increment() // Appel du slot C++ incrémenter
        }
    }
}
```

**Explications :**
- **Liaison Dynamique** : Dans ce code, le texte de l'élément `Text` est automatiquement mis à jour lorsque la valeur de `count` change, grâce à la liaison dynamique entre la propriété `count` de `Counter` et l'élément UI.
- **Mise à Jour Automatique** : Le signal `countChanged` déclenche une mise à jour automatique de tous les éléments liés à la propriété `count`, assurant ainsi que l'interface utilisateur reste en synchronisation avec la logique métier en C++.

**Documentation :**
- [Binding in QML](https://doc.qt.io/qt-6/qtqml-syntax-propertybinding.html)

**Résultat Attendu :** Après cet exercice, vous devriez comprendre comment utiliser des signaux pour notifier QML des changements de propriétés en C++. Cela permet de maintenir la synchronisation entre les données gérées en C++ et l'interface utilisateur en QML, assurant une mise à jour réactive et automatique de l'interface.

---

## **Exercice 6 : Travailler avec les Propriétés de Contexte**

#### **Objectif :**
Apprendre à exposer des objets C++ existants à QML en utilisant `setContextProperty()`.

#### **Étape 1 : Créer et Initialiser un Objet C++ dans `main.cpp`**

1. **Modifiez le fichier `main.cpp` pour créer et initialiser une instance de la classe `Counter`.**

```cpp
#include <QGuiApplication>
#include <QQmlApplicationEngine>
#include <QQmlContext>
#include "counter.h"

int main(int argc, char *argv[]) {
    QGuiApplication app(argc, argv);
    QQmlApplicationEngine engine;

    // Créer une instance de la classe Counter
    Counter myCounter;
    myCounter.setCount(15);  // Initialiser la valeur de 'count' à 15

    // Exposer l'instance 'myCounter' à QML
    engine.rootContext()->setContextProperty("myCounter", &myCounter);

    const QUrl url(u"qrc:/main.qml"_qs);
    engine.load(url);

    return app.exec();
}
```

**Explications :**
- **`Counter myCounter;`** : Ici, nous créons une instance de `Counter` directement dans `main.cpp`.
- **`myCounter.setCount(15);`** : Cette ligne initialise la propriété `count` de `myCounter` à 15.
- **`setContextProperty("myCounter", &myCounter);`** : Cette ligne expose l'objet `myCounter` à QML sous le nom `myCounter`, permettant ainsi d'accéder à cet objet et à ses propriétés directement dans le code QML.

**Documentation :**
- [QQmlContext::setContextProperty](https://doc.qt.io/qt-6/qqmlcontext.html#setContextProperty)
- [QQmlApplicationEngine](https://doc.qt.io/qt-6/qqmlapplicationengine.html)

#### **Étape 2 : Accéder aux Propriétés et Méthodes de l'Objet dans QML**

1. **Créez ou modifiez le fichier `main.qml` pour accéder aux propriétés et méthodes de `myCounter`.**

```qml
import QtQuick 6.7
import QtQuick.Controls 6.7

ApplicationWindow {
    visible: true
    width: 400
    height: 200
    title: "Utilisation des Propriétés de Contexte"

    Column {
        anchors.centerIn: parent
        spacing: 20

        Slider {
            from: 0
            to: 100
            value: myCounter.count
            onValueChanged: myCounter.count = value
        }

        Text {
            text: "Valeur actuelle : " + myCounter.count
            font.pointSize: 20
        }

        Button {
            text: "Incrémenter"
            onClicked: myCounter.increment() // Appel du slot 'increment()' de myCounter
        }
    }
}
```

**Explications :**
- **`myCounter.count`** : Vous pouvez accéder directement à la propriété `count` de `myCounter` depuis QML, grâce à l'exposition via `setContextProperty`.
- **`myCounter.increment()`** : La méthode `increment()` de `myCounter` est également accessible et peut être appelée à partir d'un événement QML, comme un clic de bouton.

**Documentation :**
- [Binding in QML](https://doc.qt.io/qt-6/qtqml-syntax-propertybinding.html)
- [Signal Handlers in QML](https://doc.qt.io/qt-6/qtqml-syntax-signals.html)

**Résultat Attendu :** Après cet exercice, vous devriez être capable d'exposer des instances spécifiques d'objets C++ à QML en utilisant `setContextProperty()`. Cela vous permet de manipuler ces objets directement dans QML, offrant ainsi une flexibilité supplémentaire pour la gestion de l'état et l'interaction entre la logique C++ et l'interface utilisateur QML.

---

## **Exercice 7 : Création et Utilisation d'Objets Singletons**

#### **Objectif :**
Implémenter un singleton en C++ et l'utiliser globalement dans QML.

#### **Étape 1 : Créer une Classe Singleton C++ avec `QML_SINGLETON` et `QML_ELEMENT`**

1. **Créez un fichier d'en-tête (`singletoncounter.h`) pour définir la classe `SingletonCounter` en tant que singleton.**

```cpp
#ifndef SINGLETONCOUNTER_H
#define SINGLETONCOUNTER_H

#include <QObject>
#include <QtQml/qqml.h>

class SingletonCounter : public QObject {
    Q_OBJECT
    QML_SINGLETON // Indique que cette classe est un singleton
    QML_ELEMENT   // Expose automatiquement cette classe à QML

    Q_PROPERTY(int count READ count WRITE setCount NOTIFY countChanged)

public:
    explicit SingletonCounter(QObject *parent = nullptr);

    // Méthode statique pour accéder au singleton
    static SingletonCounter* create(QQmlEngine*, QJSEngine*) {
        static SingletonCounter instance;
        return &instance;
    }

    int count() const;
    void setCount(int value);

public slots:
    void increment();

signals:
    void countChanged();

private:
    int m_count;
};

#endif // SINGLETONCOUNTER_H
```

2. **Créez le fichier d'implémentation (`singletoncounter.cpp`) pour définir les méthodes de `SingletonCounter`.**

```cpp
#include "singletoncounter.h"

SingletonCounter::SingletonCounter(QObject *parent) : QObject(parent), m_count(0) {
    // Initialisation de 'm_count' à 0
}

int SingletonCounter::count() const {
    return m_count;
}

void SingletonCounter::setCount(int value) {
    if (m_count != value) {
        m_count = value;
        emit countChanged(); // Émet le signal lorsque 'count' change
    }
}

void SingletonCounter::increment() {
    setCount(m_count + 1); // Incrémente la valeur de 'count'
}
```

**Explications :**
- **`QML_SINGLETON`** : Cette macro indique que `SingletonCounter` est un singleton, ce qui signifie qu'il n'y aura qu'une seule instance de cette classe accessible globalement en QML.
- **`QML_ELEMENT`** : Cette macro expose la classe à QML sans nécessiter d'enregistrement explicite dans le code C++.
- **Méthode `create`** : Cette méthode statique assure que la classe est bien utilisée en tant que singleton en renvoyant toujours la même instance.

**Documentation :**
- [QML_SINGLETON](https://doc.qt.io/qt-6/qtqml-cppintegration-exposecppattributes.html#qml-singleton)
- [Singleton Pattern](https://en.wikipedia.org/wiki/Singleton_pattern)

#### **Étape 2 : Enregistrer la Classe Singleton (Si nécessaire)**

1. **Si vous n'utilisez pas `QML_ELEMENT`, vous devriez enregistrer manuellement la classe singleton dans `main.cpp`. Cependant, avec `QML_ELEMENT`, cette étape n'est pas nécessaire.**

**Exemple sans `QML_ELEMENT` :**

```cpp
#include <QGuiApplication>
#include <QQmlApplicationEngine>
#include <QQmlContext>
#include "singletoncounter.h"

int main(int argc, char *argv[]) {
    QGuiApplication app(argc, argv);
    QQmlApplicationEngine engine;

    // Enregistrement du singleton
    qmlRegisterSingletonType<SingletonCounter>("MyApp", 1, 0, "SingletonCounter", SingletonCounter::create);

    const QUrl url(u"qrc:/main.qml"_qs);
    engine.load(url);

    return app.exec();
}
```

**Explications :**
- **`qmlRegisterSingletonType`** : Utilisé pour enregistrer le type singleton si `QML_ELEMENT` n'est pas utilisé. Il faut fournir une fonction pour créer le singleton, ici `SingletonCounter::create`.

**Documentation :**
- [qmlRegisterSingletonType](https://doc.qt.io/qt-6/qqmlengine.html#qmlRegisterSingletonType)

#### **Étape 3 : Accéder et Utiliser le Singleton depuis Différents Fichiers QML**

1. **Créez un fichier `main.qml` pour accéder au singleton `SingletonCounter` et interagir avec lui.**

```qml
import QtQuick 6.7
import QtQuick.Controls 6.7
import "."
/*
Si le singleton a été inclus avec qmlRegisterSingletonType on rajoute la 
ligne suivante :
import MyApp 1.0
*/

ApplicationWindow {
    visible: true
    width: 400
    height: 200
    title: "Utilisation du Singleton"

    StackView {
        id: stackView
        initialItem: mainPage
        anchors.fill: parent
    }

    Component {
        id: mainPage
        Page {
            Column {
                anchors.centerIn: parent
                spacing: 20

                Text {
                    text: "Valeur actuelle : " + SingletonCounter.count
                    font.pointSize: 20
                }

                Slider {
                    from: 0
                    to: 100
                    value: SingletonCounter.count
                    onValueChanged: SingletonCounter.count = value
                }

                Button {
                    text: "Incrémenter"
                    onClicked: SingletonCounter.increment()
                }

                Button {
                    text: "Naviguer vers l'autre page"
                    onClicked: stackView.push(otherPage)
                }
            }
        }
    }

    Component {
        id: otherPage
        OtherPage {}
    }
}
```

**Explications :**
- **StackView** : Utilisé pour gérer la navigation entre différentes pages QML. Le initialItem définit la page de démarrage.
- **Component** : Les composants sont utilisés pour définir les pages que le StackView peut naviguer entre.
- **SingletonCounter** : Accès au singleton exposé à QML sans avoir besoin d'importer un module spécifique.

2. **Créez un autre fichier QML (`OtherPage.qml`) pour montrer l'accès global au singleton :**

```qml
import QtQuick 6.7
import QtQuick.Controls 6.7

Page {
    Column {
        anchors.centerIn: parent
        spacing: 20

        Text {
            text: "Valeur dans SingletonCounter : " + SingletonCounter.count
            font.pointSize: 20
        }

        Button {
            text: "Incrémenter dans l'autre page"
            onClicked: SingletonCounter.increment()
        }
    }
}
```

**Explications :**
- **Accès Global** : Le singleton `SingletonCounter` peut être accédé depuis n'importe quel fichier QML, assurant une cohérence des données à travers l'application. Il est accessible sans besoin de le réimporter explicitement grâce à QML_SINGLETON et QML_ELEMENT. 
- **Réutilisation** : En utilisant le singleton, vous pouvez partager et gérer des états globaux, comme un compteur, à travers différentes parties de l'application.
- **Interaction** : L'interface utilisateur dans OtherPage.qml peut interagir avec le singleton de la même manière que dans main.qml.

**Documentation :**
- [Singleton in QML](https://doc.qt.io/qt-6/qtqml-cppintegration-definetypes.html#singleton-types)

**Résultat Attendu :** Après cet exercice, vous devriez comprendre comment créer et utiliser des singletons en C++ et les exposer globalement à QML. Cela permet de gérer des états partagés et des ressources uniques de manière centralisée dans votre application Qt.

---

## **Exercice 8 : Utilisation de `QQmlContext` pour Exposer des Données C++ à QML**

#### **Objectif :**
Apprendre à utiliser `QQmlContext` pour exposer un objet C++ existant à QML et permettre à l'interface utilisateur QML d'accéder aux données et méthodes de cet objet.


### **Étape 1 : Créer une Classe C++ avec une Propriété**

1. **Créez une nouvelle classe C++ nommée `MessageHandler`.**
   - Cette classe contiendra une propriété `message` de type `QString`.

   **messagehandler.h :**
   ```cpp
   #ifndef MESSAGEHANDLER_H
   #define MESSAGEHANDLER_H

   #include <QObject>
   #include <QString>

   class MessageHandler : public QObject {
       Q_OBJECT
       Q_PROPERTY(QString message READ message WRITE setMessage NOTIFY messageChanged)

   public:
       explicit MessageHandler(QObject *parent = nullptr);

       QString message() const;
       void setMessage(const QString &message);

   signals:
       void messageChanged();

   private:
       QString m_message;
   };

   #endif // MESSAGEHANDLER_H
   ```

   **Explications :**
   - **`Q_PROPERTY`** : Cette macro expose la propriété `message` à QML. Elle permet de lire et d'écrire la valeur de `message` et d'émettre un signal `messageChanged()` lorsqu'elle change.
   - **`QString m_message;`** : Stocke la valeur de la propriété `message`.

2. **Implémentez les méthodes `message` et `setMessage` dans le fichier source.**

   **messagehandler.cpp :**
   ```cpp
   #include "messagehandler.h"

   MessageHandler::MessageHandler(QObject *parent)
       : QObject(parent), m_message("Hello from C++!") {
   }

   QString MessageHandler::message() const {
       return m_message;
   }

   void MessageHandler::setMessage(const QString &message) {
       if (m_message != message) {
           m_message = message;
           emit messageChanged();
       }
   }
   ```

   **Explications :**
   - **`message()`** : Retourne la valeur actuelle de `m_message`.
   - **`setMessage()`** : Modifie la valeur de `m_message` et émet le signal `messageChanged()` si la nouvelle valeur est différente de l'ancienne.


### **Étape 2 : Exposer l'Objet C++ à QML avec `QQmlContext`**

1. **Modifiez le fichier `main.cpp` pour exposer l'objet `MessageHandler` à QML.**

   **main.cpp :**
   ```cpp
   #include <QGuiApplication>
   #include <QQmlApplicationEngine>
   #include <QQmlContext>
   #include "messagehandler.h"

   int main(int argc, char *argv[]) {
       QGuiApplication app(argc, argv);

       // Créer une instance de MessageHandler
       MessageHandler messageHandler;

       QQmlApplicationEngine engine;


       // Exposer l'objet MessageHandler à QML via le contexte
       engine.rootContext()->setContextProperty("messageHandler", &messageHandler);

       // Charger le fichier QML principal
       const QUrl url(u"qrc:/main.qml"_qs);
       engine.load(url);

       if (engine.rootObjects().isEmpty())
           return -1;

       return app.exec();
   }
   ```

   **Explications :**
   - **`setContextProperty("messageHandler", &messageHandler);`** : Expose l'instance `messageHandler` à QML sous le nom de `messageHandler`, rendant ses propriétés et méthodes accessibles dans le code QML.

> :warning: Attention à bien allouer l'objet sur la stack avant d'instancier l'engine pour que celui-ci ne soit pas écrasé lorsque du dépilement de la stack.
> Ceci préviendra l'accès à des propriétés d'un objet supprimé du fait du binding de propriété


### **Étape 3 : Utiliser l'Objet C++ Exposé dans QML**

1. **Créez un fichier QML (`main.qml`) pour utiliser la propriété `message` de l'objet `MessageHandler` exposé.**

   **main.qml :**
   ```qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7

   ApplicationWindow {
       visible: true
       width: 400
       height: 300
       title: "Exposition de C++ à QML"

       Column {
           anchors.centerIn: parent
           spacing: 20

           Text {
               text: messageHandler.message
               font.pointSize: 20
               color: "blue"
           }

           TextField {
               id: messageInput
               placeholderText: "Entrez un nouveau message"
           }

           Button {
               text: "Mettre à jour le message"
               onClicked: messageHandler.message = messageInput.text
           }
       }
   }
   ```

   **Explications :**
   - **`messageHandler.message`** : Accède à la propriété `message` exposée par l'objet `MessageHandler` en C++.
   - **`onClicked: messageHandler.message = messageInput.text`** : Permet de mettre à jour la propriété `message` en C++ depuis l'interface utilisateur QML lorsque l'utilisateur clique sur le bouton.


### **Étape 4 : Test et Validation**

1. **Compilez et exécutez le projet.**
   - Vous devriez voir le texte "Hello from C++!" s'afficher dans l'interface utilisateur QML.
   - Entrez un nouveau message dans le champ de texte et cliquez sur le bouton pour mettre à jour le message affiché.

**Résultat attendu :**
Le texte affiché dans l'interface QML doit correspondre à la valeur de la propriété `message` de l'objet `MessageHandler`. Lorsque l'utilisateur modifie le texte dans le champ de texte et clique sur le bouton, le message affiché doit se mettre à jour pour refléter la nouvelle valeur.
