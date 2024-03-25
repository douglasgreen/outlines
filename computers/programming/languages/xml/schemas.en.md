# XML Schemas

## Introduction to XML Schemas

### What are XML schemas?

An XML schema is a description of the structure and content constraints of an XML document. It defines the elements, attributes, data types, default values, and other rules that an XML document must follow to be considered valid. 

XML schemas are typically expressed using a schema language such as Document Type Definition (DTD), XML Schema Definition (XSD), or RELAX NG. These languages allow specifying which elements can appear in the document, the order and number of child elements, data types for elements and attributes, and more.

### Purpose and benefits of using XML schemas

The main purposes and benefits of XML schemas include:

- Defining a contract for data exchange between systems so the sender and receiver have the same expectations about the content
- Validating that an XML document conforms to the defined structure, data types, and constraints
- Enabling more powerful validation than just checking well-formedness, catching many content errors 
- Supporting data types to validate content and enable easier processing and conversion
- Using the familiar XML syntax, allowing schemas to be edited, parsed, manipulated and transformed using standard XML tools
- Providing extensibility by allowing schemas to be reused, extended, and combined
- Optimizing storage, search, and retrieval of XML content

### Brief history of XML Schema development

Some key milestones in the development of XML schemas include:

- 1986 - DTDs (Document Type Definitions) first introduced as part of SGML
- 1998 - XML 1.0 released, using DTDs for defining document structure
- 1999-2000 - Initial work on XML Schema Definition (XSD) at W3C
- 2001 - First version of RELAX NG schema language developed by OASIS
- 2001-2004 - Successive draft versions of XSD (XML Schema) released 
- 2004 - XML Schema 1.0 becomes a W3C Recommendation
- 2006-2012 - Further development of alternative languages like Schematron, Relax NG
- 2012 - XML Schema 1.1 released, adding new features

So in summary, XML schemas define the structure, content model, data types and constraints for XML documents. They serve a critical role in enabling validation, data exchange, and optimized processing of XML. The W3C's XML Schema Definition (XSD) has emerged as the primary schema language, but several important alternatives exist to meet different needs.

## XML Schema Basics

### XML Schema Abstract Data Model

The XML Schema abstract data model defines the building blocks that make up a schema. An XML Schema is a set of schema components, which fall into 3 main groups:

1. Primary components (must have names):
   - Simple type definitions
   - Complex type definitions  
   - Attribute declarations
   - Element declarations

2. Secondary components (must have names):
   - Attribute group definitions
   - Identity-constraint definitions
   - Model group definitions
   - Notation declarations

3. "Helper" components (dependent on their context):
   - Annotations
   - Model groups
   - Particles
   - Wildcards
   - Attribute Uses

During validation, declaration components like element and attribute declarations are associated by name to the information items being validated. Definition components like simple and complex types define internal schema components that can be referenced by other components.

### Schema Components and Their Properties

Each kind of schema component has specific properties that define its behavior and constraints. For example:

- Attribute Declarations have properties like {name}, {target namespace}, {type definition}, {scope}, {value constraint}, etc.

- Complex Type Definitions have properties like {name}, {target namespace}, {attribute uses}, {content type}, {prohibited substitutions}, etc.

- Element Declarations have properties like {name}, {target namespace}, {type definition}, {identity-constraint definitions}, {nillable}, etc.

Some properties are required while others are optional. The values of these properties determine how the component behaves in validation and its constraints on XML documents.

### Constraints and Validation Rules in XML Schema

XML Schema provides several kinds of constraints and validation rules that schema components specify for XML documents:

1. Constraints on the schema components themselves (Schema Component Constraints) - conditions components must satisfy to be valid schema components

2. Constraints on the XML representation of schema components (Schema Representation Constraints) - rules for the XML elements/attributes used to represent the schema component

3. Validation rules - the actual validation checking of XML documents performed by schema validators, as specified by each schema component 

4. Schema information set contributions - augmentations to the post-schema-validation infoset (PSVI) that provide additional info based on schema validation results

These different categories of constraints enforce validity at the schema component level, schema document level, and XML instance document level.

### Conformance Requirements for XML Schema Processors

The XML Schema spec defines different conformance requirements for processors:

- Minimally conforming processors must completely implement all Schema Component Constraints, Validation Rules, and Schema Information Set Contributions.

- Processors that claim to conform to the XML Representation of Schemas must additionally implement all Schema Representation Constraints when processing schema documents.

- Fully conforming processors must be minimally conforming, conform to the XML Representation of Schemas, and be able to access schema documents from the Web per additional rules.

So in summary, the XML Schema abstract model provides a framework for defining schema components, their properties, and the constraints and rules they impose on XML documents. Processors have different levels of conformance based on how completely they implement the different categories of constraints in the abstract model.

## Schema Document Structure

### Anatomy of an XML Schema Document

An XML Schema document is an XML document that defines the structure, content and semantics of another XML document. The root element of an XML Schema document is the `<schema>` element, which is defined in the XML Schema namespace `http://www.w3.org/2001/XMLSchema`.

The `<schema>` element can contain the following child elements in this order:

1. Annotation elements (`<annotation>`)
2. Inclusion elements (`<include>`, `<import>`, `<redefine>`) 
3. Top-level schema component definitions like:
   - `<simpleType>` 
   - `<complexType>`
   - `<element>`
   - `<attribute>`
   - `<group>`
   - `<attributeGroup>`
   - `<notation>`

The schema components defined within the `<schema>` element belong to the target namespace specified by the `targetNamespace` attribute.

### The schema Element and Its Attributes

The `<schema>` element is the root element of every XML Schema. It contains definitions and declarations for the schema components that make up the schema.

Some of the important attributes of the `<schema>` element are:

- `targetNamespace` - Specifies the namespace that the schema components belong to
- `elementFormDefault` and `attributeFormDefault` - Specifies whether locally declared elements and attributes must be qualified with a namespace prefix
- `blockDefault` - Specifies which type derivations are not allowed in the schema
- `finalDefault` - Specifies which type derivations and restrictions cannot be further derived in the schema

The `<schema>` element may also contain attributes from other namespaces for extensibility.

### Defining the Target Namespace

The `targetNamespace` attribute on the `<schema>` element defines the namespace URI that the schema components in the schema document belong to. This serves to avoid naming conflicts between schema components defined in different schemas.

For example:

```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"
           targetNamespace="http://www.example.com/myschema">
  ...
</xs:schema>
```

Here, the schema components are associated with the namespace `http://www.example.com/myschema`. XML instance documents that conform to this schema must use this namespace for its elements and attributes.

If the `targetNamespace` is not specified, the schema components do not belong to any namespace. Note that an empty string value for `targetNamespace` is not equivalent to omitting it - it puts the components into a namespace with an empty URI.

### Including and Importing Schema Documents

XML Schema allows splitting the schema definitions into multiple schema documents. Schema components from these documents can be assembled together in two ways:

1. Using `<include>` to include schema components from another schema document having the same target namespace. The included components become part of the including schema.

2. Using `<import>` to reference schema components from an external schema with a different target namespace. The imported components remain in a separate namespace, but can be referenced.

Both `<include>` and `<import>` take a `schemaLocation` attribute that provides a hint to the XML processor about where to find the referenced schema document. However, the processor is free to locate the document using other means as well.

For example:

```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"
           targetNamespace="http://www.example.com/myschema">

  <xs:include schemaLocation="myschema-base.xsd"/>
  
  <xs:import namespace="http://www.example.com/ext" 
             schemaLocation="extension.xsd"/>

  ...  
</xs:schema>
```

In summary, an XML Schema document is a structured XML document with a `<schema>` root element that defines a set of schema components within a target namespace. The schema can be modularized into multiple documents using `<include>` and `<import>`. This allows defining complex schemas in a manageable way by assembling schema components from multiple namespaces.

## Defining Elements

### Declaring Elements with the element Element

Elements are declared in XML Schema using the `<element>` element. The `<element>` element is used to define the name, type, and cardinality constraints of an element that can appear in an XML document instance.

For example:

```xml
<xs:element name="customer" type="xs:string"/>
```

This declares an element named "customer" of type `xs:string`. 

### Element Names, Types, and Cardinality Constraints

When declaring an element, you specify the following key properties:

- `name` - Specifies the name of the element. Required for global elements.
- `type` - Specifies the data type of the element's content. Can refer to a built-in schema type like `xs:string` or a custom simple or complex type defined in the schema.
- `minOccurs` and `maxOccurs` - Specifies the minimum and maximum number of times the element can appear. Default is 1 for both. Setting `maxOccurs="unbounded"` allows the element to repeat any number of times.

For example:

```xml
<xs:element name="address" minOccurs="1" maxOccurs="unbounded">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="street" type="xs:string"/>
      <xs:element name="city" type="xs:string"/>
    </xs:sequence>
  </xs:complexType>
</xs:element>
```

This declares an "address" element that must appear at least once but can be repeated. Its content is defined inline as a complex type with a sequence of "street" and "city" elements.

### Global vs Local Element Declarations

Elements can be declared globally, as direct children of the `<schema>` element, or locally within a complex type definition.

- Global element declarations define standalone elements that can be referenced throughout the schema. They must have a unique name within the schema's target namespace.

- Local element declarations define elements within the context of a particular complex type. They do not need to have unique names and cannot be referenced from outside their containing type.

For example:

```xml
<xs:element name="customer" type="customerType"/>

<xs:complexType name="customerType">
  <xs:sequence>
    <xs:element name="name" type="xs:string"/>
    <xs:element name="address" type="addressType"/>
  </xs:sequence>
</xs:complexType>
```

Here, "customer" is a global element that references the "customerType" complex type. "name" and "address" are local elements declared within "customerType".

### Abstract Elements and Substitution Groups

An element can be declared as abstract using the `abstract="true"` attribute. An abstract element cannot appear directly in an instance document, but can be used as the head of a substitution group.

A substitution group allows elements to be substituted for the abstract head element. Elements in the group must have the same type as the head element or a type derived from the head element's type.

For example:

```xml
<xs:element name="shape" type="shapeType" abstract="true"/>
<xs:element name="circle" type="circleType" substitutionGroup="shape"/>
<xs:element name="square" type="squareType" substitutionGroup="shape"/>
```

This defines an abstract "shape" element as the head of a substitution group. The "circle" and "square" elements can be used wherever "shape" is referenced.

So in summary, the `<element>` element is used to declare elements in an XML Schema, specifying their names, types, and constraints. Elements can be declared globally or locally, and advanced features like abstract elements and substitution groups provide flexibility in XML document structures.

## Defining Attributes

### Declaring Attributes with the attribute Element

Attributes are declared in XML Schema using the `<attribute>` element. The `<attribute>` element is used to define the name, type, default values, and other properties of an attribute that can appear on an element in an XML document instance.

For example:

```xml
<xs:attribute name="customerID" type="xs:integer"/>
```

This declares an attribute named "customerID" of type `xs:integer`.

### Attribute Names, Types, and Default Values

When declaring an attribute, you specify the following key properties:

- `name` - Specifies the name of the attribute. Required unless `ref` is used.
- `type` - Specifies the data type of the attribute's value. Can refer to a built-in schema type like `xs:string`, `xs:integer`, `xs:date`, etc. or a custom simple type defined in the schema.
- `default` - Specifies a default value for the attribute. If the attribute is not present in an instance document, the schema processor will provide this value.
- `fixed` - Specifies a fixed value that the attribute must have. Mutually exclusive with `default`.

For example:

```xml
<xs:attribute name="country" type="xs:string" fixed="US"/>
```

This declares a "country" attribute with a fixed value of "US". If the attribute appears, it must have this value, and if it is omitted, the schema processor will provide it.

### Attribute References and Attribute Groups

Instead of defining an attribute directly within an element declaration, you can define it as a global `<attribute>` child of the `<schema>` element and then reference it using the `ref` attribute:

```xml
<xs:attribute name="customerID" type="xs:integer"/>

<xs:complexType name="customerType">
  <xs:attribute ref="customerID"/>
</xs:complexType>  
```

Attribute groups allow bundling a set of attribute declarations for reuse. They are defined using the `<attributeGroup>` element and referenced using `<attributeGroup ref="...">`:

```xml
<xs:attributeGroup name="customerAttributes">
  <xs:attribute name="customerID" type="xs:integer"/>
  <xs:attribute name="status" type="xs:string"/>
</xs:attributeGroup>

<xs:complexType name="customerType">
  <xs:attributeGroup ref="customerAttributes"/>
</xs:complexType>
```

### Attribute Wildcards with anyAttribute

The `<anyAttribute>` element allows specifying a wildcard for attributes from a particular namespace or namespaces. This enables elements to have attributes not explicitly declared in the schema.

The `namespace` attribute specifies which namespaces the wildcard allows attributes from - e.g. `##any` allows attributes from any namespace. The `processContents` attribute indicates how the schema processor should handle validation of these attributes - e.g. `lax` means validating them if a schema is available, but not raising errors otherwise.

For example:

```xml
<xs:complexType name="openType">
  <xs:anyAttribute namespace="##any" processContents="skip"/> 
</xs:complexType>
```

This allows elements of type `openType` to have any attributes from any namespace, without requiring those attributes to be validated.

So in summary, the `<attribute>` element is used to declare attributes in XML Schema, specifying their names, types, default/fixed values, and other properties. Attributes can be declared locally or globally and grouped for reuse. The `<anyAttribute>` element provides a wildcard mechanism to allow undeclared attributes from specified namespaces.

## Simple Types

### Overview of Built-in Simple Types

XML Schema provides a set of 44 built-in simple types that can be used directly to specify the type of elements and attributes. These include:

- 19 primitive types like `string`, `boolean`, `decimal`, `float`, `double`, `duration`, `dateTime`, `time`, `date`, `gYearMonth`, `gYear`, `gMonthDay`, `gDay`, `gMonth`, `hexBinary`, `base64Binary`, `anyURI`, `QName`, `NOTATION`

- 25 derived types built on the primitive types, such as `normalizedString`, `token`, `language`, `Name`, `NCName`, `ID`, `IDREF`, `ENTITY`, `integer`, `nonPositiveInteger`, `negativeInteger`, `long`, `int`, `short`, `byte`, `nonNegativeInteger`, `unsignedLong`, `unsignedInt`, `unsignedShort`, `unsignedByte`, `positiveInteger`

These built-in types form the foundation from which custom simple types can be derived.

### Defining Custom Simple Types

New simple types are defined by deriving them from existing simple types (built-in's and derived). We can derive a new simple type by restricting an existing simple type, in other words, the legal range of values for the new type are a subset of the existing type's range of values.

We use the `<simpleType>` element to define and name the new simple type. Within `<simpleType>`, we use the `<restriction>` element to indicate the existing base type, and to specify the facets that constrain the range of values.

For example, to create a new type of integer called "myInteger" whose range of values is between 10000 and 99999 inclusive:

```xml
<xsd:simpleType name="myInteger">
  <xsd:restriction base="xsd:integer">
    <xsd:minInclusive value="10000"/>
    <xsd:maxInclusive value="99999"/> 
  </xsd:restriction>
</xsd:simpleType>
```

This derives `myInteger` by restricting the base type `integer` using the `minInclusive` and `maxInclusive` facets.

### Simple Type Restrictions and Facets

Each simple type, whether built-in or derived, has a set of constraining facets that can be applied to it. Which facets are applicable depends on the specific base type. The available facets are:

- `length` - restricts the number of characters/list items allowed 
- `minLength` - restricts the minimum number of characters/list items
- `maxLength` - restricts the maximum number of characters/list items
- `pattern` - restricts values to those that match a regular expression
- `enumeration` - restricts values to a specified set of values
- `whiteSpace` - specifies how whitespace is handled
- `maxInclusive` - specifies maximum value (inclusive)
- `maxExclusive` - specifies maximum value (exclusive) 
- `minExclusive` - specifies minimum value (exclusive)
- `minInclusive` - specifies minimum value (inclusive)
- `totalDigits` - restricts the total number of digits 
- `fractionDigits` - restricts the number of fractional digits

When defining a custom simple type by restriction, you specify one or more of these facets to constrain the allowed values. The facets used must be applicable to the base type.

### List and Union Simple Types

In addition to restricting a simple type, you can also define new simple types as a list or union of other simple types.

A list type is a whitespace-separated list of values of a specified simple type. To define a list type, use a `<list>` element inside `<simpleType>` specifying the `itemType` attribute:

```xml
<xsd:simpleType name="myIntList">
  <xsd:list itemType="xsd:int"/>
</xsd:simpleType>
```

A union type allows a value to be one of several specified simple types. To define a union type, use a `<union>` element inside `<simpleType>` specifying the `memberTypes` attribute with a list of types:

```xml
<xsd:simpleType name="myIntOrString">
  <xsd:union memberTypes="xsd:int xsd:string"/>  
</xsd:simpleType>
```

So in summary, XML Schema provides a rich set of built-in simple types that can be used directly or as the basis for deriving new custom simple types. Custom types are defined by restricting an existing type using facets, or by creating list and union types. This allows schemas to precisely specify the valid structure and content of conforming XML documents.

## Complex Types

### Defining Complex Types with the complexType Element

Complex types are used to define elements that contain other elements and/or attributes. They are defined using the `<complexType>` element in an XML Schema.

The `<complexType>` element has several key attributes:

- `name` - Specifies a name for the complex type. Required if the type is being defined globally as a child of the `<schema>` element.
- `abstract` - If set to true, the complex type cannot be used directly in instance documents and must be extended by another complex type. Default is false.
- `mixed` - If set to true, the complex type can contain a mixture of elements and text content. Default is false.

For example:

```xml
<xs:complexType name="personType">
  <xs:sequence>
    <xs:element name="firstName" type="xs:string"/>
    <xs:element name="lastName" type="xs:string"/>
  </xs:sequence>
  <xs:attribute name="age" type="xs:positiveInteger"/>
</xs:complexType>
```

This defines a complex type named `personType` that contains a sequence of `firstName` and `lastName` elements, and an `age` attribute.

### Content Models - Simple Content, Complex Content, Mixed Content

The content of a complex type can be specified using one of three content models:

1. Simple content - contains only text and attributes, no child elements. Defined using `<simpleContent>`.

2. Complex content - contains only child elements and attributes, no text. Defined using `<complexContent>` with a nested `<sequence>`, `<choice>`, or `<all>` element.

3. Mixed content - contains a mixture of text and child elements. Enabled by setting the `mixed` attribute to true on the `<complexType>`.

For example, a complex type with simple content:

```xml
<xs:complexType name="nameType">
  <xs:simpleContent>
    <xs:extension base="xs:string">
      <xs:attribute name="language" type="xs:string"/>
    </xs:extension>
  </xs:simpleContent>
</xs:complexType>
```

And a complex type with mixed content:

```xml
<xs:complexType name="letterType" mixed="true">
  <xs:sequence>
    <xs:element name="name" type="xs:string"/>
    <xs:element name="orderid" type="xs:positiveInteger"/>
    <xs:element name="shipdate" type="xs:date"/>
  </xs:sequence>
</xs:complexType>
```

### Deriving Complex Types by Extension and Restriction

New complex types can be derived from existing complex types using either extension or restriction. This allows reuse and refinement of type definitions.

Extension adds new elements or attributes to the end of the base type's content model. It's defined using an `<extension>` element inside `<complexContent>`:

```xml
<xs:complexType name="fullpersoninfo">
  <xs:complexContent>
    <xs:extension base="personinfo">
      <xs:sequence>
        <xs:element name="address" type="xs:string"/>
        <xs:element name="city" type="xs:string"/>
        <xs:element name="country" type="xs:string"/>
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

Restriction limits the content allowed in the base type, e.g. by removing elements or making optional elements required. It's defined using a `<restriction>` element:

```xml
<xs:complexType name="restrictedpersoninfo">
  <xs:complexContent>
    <xs:restriction base="personinfo">
      <xs:sequence>
        <xs:element name="firstName" type="xs:string"/>
        <xs:element name="lastName" type="xs:string"/>
      </xs:sequence>
    </xs:restriction>
  </xs:complexContent>
</xs:complexType>
```

### Abstract Types and Final Types

Complex types can be defined as abstract using the `abstract` attribute. An abstract type cannot be used directly in instance documents, only extended by other types.

The `final` attribute prevents further derivation of the complex type by extension and/or restriction. It can contain `#all` (blocks all derivation), `extension` (blocks extension), or `restriction` (blocks restriction).

For example:

```xml
<xs:complexType name="baseType" abstract="true" final="restriction">
  <xs:sequence>
    <xs:element name="id" type="xs:string"/>
  </xs:sequence>  
</xs:complexType>
```

This defines an abstract base type that cannot be restricted, only extended.

So in summary, the `<complexType>` element is used to define elements that contain other elements and attributes. The content can be simple, complex or mixed. Complex types support inheritance by extension and restriction, and can be made abstract or final to control derivation. This provides a powerful mechanism for defining structured, reusable data models in XML Schema.

## Named Model Groups

### Defining Reusable Content Models with the group Element

The `<group>` element allows defining a named model group that contains a set of element declarations or references. This enables reusing common content models across multiple complex types.

A model group is defined by specifying a name and a content model within the `<group>` element:

```xml
<xs:group name="myModelGroup">
  <xs:sequence>
    <xs:element ref="firstName"/>
    <xs:element ref="lastName"/> 
  </xs:sequence>
</xs:group>
```

This defines a model group named "myModelGroup" consisting of a sequence of "firstName" and "lastName" element references.

### Referencing Model Groups in Complex Types

To reuse a named model group, it is referenced within the content model of a complex type definition using a `<group>` element with a `ref` attribute pointing to the group name:

```xml
<xs:complexType name="personType">
  <xs:sequence>
    <xs:group ref="myModelGroup"/>
    <xs:element name="age" type="xs:integer"/>
  </xs:sequence>
</xs:complexType>
```

Here, the "myModelGroup" is incorporated into the content model of the "personType" complex type. It's as if the content of "myModelGroup" was copied directly into the complex type definition.

Model groups can also be referenced within other named model groups, allowing nested reuse of content models.

### Deriving Model Groups by Restriction

Although model groups cannot be derived by extension, the XML Schema spec allows deriving a model group by restriction to a limited degree.

When a `<group>` element with a `name` attribute appears inside a `<redefine>` element, it can restrict the model group it refers to in its `ref` attribute by removing elements or constraining their occurrence.

For example:

```xml
<xs:redefine schemaLocation="base.xsd">
  <xs:group name="restrictedGroup">
    <xs:restriction base="originalGroup">
      <xs:sequence>
        <xs:element ref="a"/>
        <xs:element ref="b" minOccurs="0"/>
      </xs:sequence>  
    </xs:restriction>
  </xs:group>
</xs:redefine>  
```

This derives a new group "restrictedGroup" by restricting "originalGroup", making the "b" element optional. The redefined group is only available within the schema that contains the `<redefine>`.

So in summary, named model groups provide a way to define reusable content models that can be referenced in multiple complex types. While they don't support derivation by extension, a limited form of restriction is possible when redefining groups. This promotes modular schema design and avoids duplication of similar content models.

## Named Attribute Groups

### Defining Reusable Attribute Declarations with attributeGroup

The `<attributeGroup>` element allows defining a named group of attribute declarations that can be referenced and reused in multiple complex type definitions. This promotes modularization and avoids duplication of common attributes across the schema.

An attribute group is defined by specifying a name and one or more attribute declarations or references within the `<attributeGroup>` element:

```xml
<xs:attributeGroup name="personAttrGroup">
  <xs:attribute name="firstName" type="xs:string"/>
  <xs:attribute name="lastName" type="xs:string"/>
  <xs:attribute name="age" type="xs:positiveInteger"/>
</xs:attributeGroup>
```

This defines an attribute group named "personAttrGroup" consisting of "firstName", "lastName" and "age" attribute declarations.

### Referencing Attribute Groups in Complex Types

To reuse a named attribute group, it is referenced within the complex type definition using an `<attributeGroup>` element with a `ref` attribute pointing to the group name:

```xml
<xs:complexType name="personType">
  <xs:sequence>
    <xs:element name="address" type="addressType"/>
  </xs:sequence>
  <xs:attributeGroup ref="personAttrGroup"/>
</xs:complexType>
```

Here, the "personAttrGroup" is incorporated into the "personType" complex type. It's as if the attribute declarations in "personAttrGroup" were copied directly into the complex type.

Attribute groups can be referenced in multiple complex types, enabling consistent and centralized definitions of common attributes.

### Extending and Restricting Attribute Groups

Unlike named model groups, attribute groups do support derivation by both extension and restriction to a limited degree.

To extend an attribute group, define a new group that references the base group and adds new attribute declarations:

```xml
<xs:attributeGroup name="fullPersonAttrGroup">
  <xs:attributeGroup ref="personAttrGroup"/>
  <xs:attribute name="gender" type="xs:string"/>  
</xs:attributeGroup>
```

This creates an extended version of "personAttrGroup" that includes an additional "gender" attribute.

To restrict an attribute group, the new group definition must be nested inside a `<redefine>` element that references the schema containing the base group:

```xml
<xs:redefine schemaLocation="base.xsd">
  <xs:attributeGroup name="restrictedPersonAttrGroup">
    <xs:restriction base="personAttrGroup">
      <xs:attribute name="firstName" type="xs:string"/>
      <xs:attribute name="lastName" type="xs:string"/>
    </xs:restriction>
  </xs:attributeGroup>
</xs:redefine>
```

This restricts "personAttrGroup" to only allow the "firstName" and "lastName" attributes, omitting "age". The redefined group is only available within the schema that contains the `<redefine>`.

So in summary, the `<attributeGroup>` element enables defining reusable sets of attribute declarations that can be referenced by name in complex type definitions. Attribute groups support derivation by extension to add attributes, and restriction to limit attributes, allowing flexible and modular attribute definitions in an XML Schema.

## Identity Constraints

### Defining Uniqueness and Reference Constraints

XML Schema provides three elements for defining identity constraints:

1. `<unique>` - Specifies that an element or attribute value (or combination of values) must be unique within a specified scope.

2. `<key>` - Specifies a uniqueness constraint like `<unique>`, and additionally requires that the value(s) must be present (i.e. cannot be null).

3. `<keyref>` - Specifies a reference constraint that requires the value(s) to match those of a `<key>` or `<unique>` constraint in the specified scope.

Each of these elements contains a `<selector>` element specifying the elements the constraint applies to, and one or more `<field>` elements specifying the element/attribute values to be checked.

For example:

```xml
<xs:element name="library">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="book" maxOccurs="unbounded">
        <xs:complexType>
          <xs:sequence>
            <xs:element name="title" type="xs:string"/>
            <xs:element name="author" type="xs:string"/>
            <xs:element name="isbn" type="xs:string"/>
          </xs:sequence>
        </xs:complexType>
      </xs:element>
    </xs:sequence>
  </xs:complexType>
  
  <xs:unique name="uniqueISBN">
    <xs:selector xpath="book"/>
    <xs:field xpath="isbn"/>
  </xs:unique>
</xs:element>
```

This defines a `<unique>` constraint named "uniqueISBN" specifying that the `isbn` element value must be unique across all `book` elements within the `library` element.

### Using XPath Expressions in selector and field Elements

The `<selector>` and `<field>` elements use XPath expressions to specify the target elements and values for the constraint:

- The `<selector>` element's `xpath` attribute contains an XPath expression relative to the constraint's parent element, specifying the set of elements the constraint applies to.

- Each `<field>` element's `xpath` attribute contains an XPath expression relative to elements selected by `<selector>`, specifying the element/attribute value(s) to check.

The XPath subset allowed in `<selector>` is:
- `Path` separated by `|`
- `Path` is `('.//')? ( Step ('/' Step)* )?` 
- `Step` is `.` or `NameTest`
- `NameTest` is `QName` or `*` or `NCName:*`

The XPath subset allowed in `<field>` is:
- `.` or `@` followed by a `NameTest`
- `NameTest` is `QName` or `*` or `NCName:*`

### Specifying Scope for Identity Constraints

The scope of an identity constraint is determined by its location in the schema:

- If defined as a child of an element declaration, the constraint applies to all instances of that element. This is called "element scope".

- If defined within a complex type definition, the constraint applies to all elements of that type. This is called "type scope".

- The top-level `<schema>` element can also contain identity constraints that apply globally.

For example:

```xml
<xs:element name="library">
  <xs:unique name="globalBookTitle">
    <xs:selector xpath=".//book"/>
    <xs:field xpath="title"/>
  </xs:unique>
</xs:element>
```

This constraint with "element scope" specifies that `book/title` values must be unique within the entire `library` element and its descendants.

So in summary, XML Schema's `<unique>`, `<key>` and `<keyref>` elements allow defining uniqueness and reference constraints on element/attribute values using XPath expressions. The scope of the constraints is determined by their location in the schema. This provides a flexible way to enforce integrity of XML data beyond just single attributes.

## Annotations and Documentation

## Adding Annotations with the annotation Element

The `<annotation>` element allows adding annotations to schema components for documentation or application-specific information. Annotations do not affect the schema's meaning but provide additional information for users and applications.

An `<annotation>` can be added as the first child of any schema component, such as `<schema>`, `<element>`, `<attribute>`, `<simpleType>`, `<complexType>`, etc. It contains one or more `<documentation>` and/or `<appinfo>` elements.

For example:

```xml
<xs:element name="product">
  <xs:annotation>
    <xs:documentation>Represents a product in the catalog</xs:documentation>
    <xs:appinfo source="http://myapp.com/product">
      <display-name>Product</display-name>
    </xs:appinfo>
  </xs:annotation>
  <xs:complexType>
    ...
  </xs:complexType>
</xs:element>
```

This adds an annotation to the "product" element declaration with both documentation and application info.

## User Information with the documentation Element

The `<documentation>` element is used to provide human-readable information about the schema component it annotates. The content of `<documentation>` can be any text or well-formed XML. 

Multiple `<documentation>` elements can be included to provide the information in different languages. The `xml:lang` attribute specifies the language used.

For example:

```xml
<xs:documentation xml:lang="en">English description</xs:documentation>
<xs:documentation xml:lang="fr">Description en français</xs:documentation>
```

The information in `<documentation>` is intended for schema users to better understand the purpose and usage of the annotated component.

## Application Information with the appinfo Element

The `<appinfo>` element is used to provide information for applications that process the schema or XML documents based on it. The content of `<appinfo>` can be any well-formed XML.

The `source` attribute of `<appinfo>` specifies a URI reference indicating the source or purpose of the application information. This allows distinguishing between different types of app info.

For example:

```xml
<xs:appinfo source="http://myapp.com/display">
  <display-name>Product Name</display-name>
  <display-order>1</display-order>
</xs:appinfo>

<xs:appinfo source="http://myapp.com/persistence">
  <db-field>PRODUCT_NAME</db-field>
</xs:appinfo>  
```

This includes two `<appinfo>` elements with different `source` URIs to separate display-related and persistence-related information.

The specific format and meaning of the content inside `<appinfo>` is defined by the applications that use it. The schema processor does not validate or interpret it.

So in summary, the `<annotation>` element, along with its `<documentation>` and `<appinfo>` children, allows attaching human-readable documentation and application-specific information to XML Schema components. This provides a standard way to enrich schemas with additional metadata without affecting their core meaning and validation behavior.

## Modularizing Schemas

## Strategies for Modularizing Large Schemas

When working with large and complex schemas, it's important to modularize them into smaller, more manageable pieces. Some strategies for doing this include:

1. Splitting the schema into multiple files based on logical groupings of components. For example, having separate files for elements, complex types, simple types, etc.

2. Using the `<include>` element to compose a schema from multiple schema documents addressing the same namespace. This allows physically separating components while still treating them as part of one logical schema.

3. Using the `<import>` element to reference components from schemas with different target namespaces. This enables reuse across schema modules.

4. Defining reusable groups of elements and attributes via named model groups (`<group>`) and attribute groups (`<attributeGroup>`). These can be referenced from multiple type definitions.

5. Deriving new types from existing ones using `<extension>` and `<restriction>` rather than always defining new types from scratch.

The goal is to break down the schema into smaller, self-contained modules with clear dependencies that are easier to understand, maintain and reuse.

## Includes, Imports and Redefines

XML Schema provides three main mechanisms for modularizing and combining schemas:

1. `<include>` - Allows combining multiple schema documents that have the same target namespace into a single logical schema. The included components become part of the including schema.

2. `<import>` - Allows referencing components from an external schema with a different target namespace. The imported components remain in a separate namespace and are used by reference.

3. `<redefine>` - Allows including an external schema document with the ability to redefine certain components in it. The redefined components replace the originals within the redefining schema. However, `<redefine>` is deprecated in the latest version of XML Schema.

Both `<include>` and `<import>` take a `schemaLocation` attribute that specifies the URI of the schema document to be included or imported. Cyclic dependencies via `<include>` and `<import>` are allowed.

## Chameleon Design Pattern for Schema Composition 

The chameleon design pattern is a technique for authoring schema documents intended to be included in other schemas without specifying a target namespace. When such a "chameleon" schema is included in another schema, it takes on the including schema's target namespace (if any).

This allows writing schema components that can be reused across multiple schemas with different target namespaces. Any references to unqualified components within the chameleon schema will automatically resolve to the including schema's namespace.

To use the chameleon pattern:

1. Author a schema document without specifying a `targetNamespace` attribute on the `<schema>` element.

2. Include this schema in other schemas using `<include>`. 

3. The included components will adopt the enclosing schema's target namespace if it has one, or remain unqualified if it does not.

This provides flexibility in authoring reusable schema modules that can be namespace-independent.

So in summary, XML Schema provides several mechanisms for modularizing large schemas and assembling them from smaller parts. `<include>` and `<import>` allow combining schemas in the same or different namespaces, while the chameleon pattern enables writing namespace-neutral schema modules. Effective use of these techniques can make complex schemas much more manageable.

## Namespaces and Schema Composition

Explain Namespaces and Schema Composition, while discussing the following topics:
* Target namespaces and unqualified locals
* Assembling a schema from multiple documents and namespaces
* Namespace-related schema composition constraints

## Schema Extensibility

Explain Schema Extensibility, while discussing the following topics:
* Extensibility mechanisms in XML Schema
* Adding elements and attributes not defined in the schema
* Controlling extensibility with final and block attributes

## Using Schemas for Validation

Explain Using Schemas for Validation, while discussing the following topics:
* Associating schemas with XML documents
* Schema validation outcomes and error handling
* Validation rules for elements and attributes
* Post-schema-validation infoset (PSVI)

## Advanced Techniques

Explain Advanced Techniques, while discussing the following topics:
* Conditional type assignment
* Inheriting and overriding facets
* Type alternatives and default types
* Assertions and type alternatives

## Schema Design Best Practices

Explain Schema Design Best Practices, while discussing the following topics:
* General schema design principles
* Naming conventions for schema components
* Refactoring and normalizing schemas
* Versioning strategies for schemas

## Schema Languages and Technologies

Explain Schema Languages and Technologies, while discussing the following topics:
* Other XML schema languages - RELAX NG, Schematron
* Comparison of features and limitations
* Combining schemas from multiple languages
* Code generation and data binding

## Schemas in Practice

Explain Schemas in Practice, while discussing the following topics:
* Schemas for common XML vocabularies
* Industry-specific schema usage - finance, healthcare, etc.
* Case studies and real-world schema examples

## Future of XML Schema

Explain Future of XML Schema, while discussing the following topics:
* Limitations and criticisms of XML Schema 1.0
* New features in XML Schema 1.1
* Possible future directions for XML Schema
* Alternative schema-aware technologies on the horizon

## Glossary of Terms

Write a glossary of the top twenty terms used about XML schemas.

## Frequently Asked Questions

Write a list of the top twenty frequently asked questions about XML schemas and give a brief answer to each.

## Important People/Places/Things

Write a list of the top 20 important people/places/things (choose one) of XML schemas.

## Timeline

Write a timeline of the top 20 important events in the history of XML schemas.
