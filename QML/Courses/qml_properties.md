### **1. Default Properties**

A **default property** in QML is a special property of a component that allows you to omit the property name when adding child elements or content. This property is often used in container-like components, where the default property serves as a logical place to add children.

- **Common Example:** `Item`'s `data` property is a default property. It allows you to add child items directly within an `Item` without explicitly referencing the `data` property.

- **Example:**
  ```qml
  Item {
      Rectangle { width: 100; height: 100; color: "red" }
      Rectangle { width: 50; height: 50; color: "blue" }
  }
  ```
  Here, `Item` has a default `data` property, so you can directly place `Rectangle` elements inside it without explicitly referencing `data`.

### **2. Dynamic Properties**

**Dynamic properties** refer to properties that can be added to or removed from QML objects at runtime. This feature allows you to create properties on the fly using JavaScript, which can be useful for certain dynamic behaviors or customization in your application.

- **Adding a Dynamic Property:**
  ```qml
  Rectangle {
      width: 100
      height: 100
      color: "red"

      Component.onCompleted: {
          this.myDynamicProperty = "Hello, World!"
          console.log(myDynamicProperty)  // Outputs: Hello, World!
      }
  }
  ```
  In this example, `myDynamicProperty` is dynamically added to the `Rectangle` at runtime.

### **3. Linked Properties**

**Linked properties** refer to properties that are bound to other properties. When the source property changes, the linked property automatically updates. This is the core of QML's reactivity system, where properties can be linked together to create dynamic and responsive interfaces.

- **Example of Linked Properties:**
  ```qml
  Rectangle {
      width: 100
      height: width * 2  // `height` is linked to `width`
      color: "blue"
  }
  ```
  In this example, the `height` property is linked to the `width` property. Whenever `width` changes, `height` automatically updates to twice the width.

### **4. Readonly Properties**

**Readonly properties** are properties that can be set initially but cannot be modified after they have been set. They are used when you want to ensure that a property remains constant once defined, preventing any further changes.

- **Example using a Readonly Property:**
  ```qml
  Rectangle {
      property int readonly myProperty: 42  // Readonly property
      width: myProperty * 10
      height: 100

      Component.onCompleted: {
          // myProperty = 50  // This would cause an error
          console.log(myProperty)  // Outputs: 42
      }
  }
  ```
  In this example, `myProperty` is a readonly property. You can set its value initially, but attempting to modify it later will result in an error.

### **Summary**

- **Default Properties:** Special properties of a component where you can omit the property name when adding content, often used in container components.
- **Dynamic Properties:** Properties that can be added or removed at runtime using JavaScript.
- **Linked Properties:** Properties bound to other properties, automatically updating when the source property changes, leveraging QML's reactivity.
- **Readonly Properties:** Properties that can be set initially but cannot be changed thereafter, ensuring they remain constant.
