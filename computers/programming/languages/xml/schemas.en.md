# XML Schemas

## Introduction to XML Schemas

### What are XML schemas?

An XML schema is a description of the structure and content constraints of an XML document. It
defines the elements, attributes, data types, default values, and other rules that an XML document
must follow to be considered valid.

XML schemas are typically expressed using a schema language such as Document Type Definition (DTD),
XML Schema Definition (XSD), or RELAX NG. These languages allow specifying which elements can appear
in the document, the order and number of child elements, data types for elements and attributes, and
more.

### Purpose and benefits of using XML schemas

The main purposes and benefits of XML schemas include:

-   Defining a contract for data exchange between systems so the sender and receiver have the same
    expectations about the content
-   Validating that an XML document conforms to the defined structure, data types, and constraints
-   Enabling more powerful validation than just checking well-formedness, catching many content
    errors
-   Supporting data types to validate content and enable easier processing and conversion
-   Using the familiar XML syntax, allowing schemas to be edited, parsed, manipulated and
    transformed using standard XML tools
-   Providing extensibility by allowing schemas to be reused, extended, and combined
-   Optimizing storage, search, and retrieval of XML content

### Brief history of XML Schema development

Some key milestones in the development of XML schemas include:

-   1986 - DTDs (Document Type Definitions) first introduced as part of SGML
-   1998 - XML 1.0 released, using DTDs for defining document structure
-   1999-2000 - Initial work on XML Schema Definition (XSD) at W3C
-   2001 - First version of RELAX NG schema language developed by OASIS
-   2001-2004 - Successive draft versions of XSD (XML Schema) released
-   2004 - XML Schema 1.0 becomes a W3C Recommendation
-   2006-2012 - Further development of alternative languages like Schematron, Relax NG
-   2012 - XML Schema 1.1 released, adding new features

So in summary, XML schemas define the structure, content model, data types and constraints for XML
documents. They serve a critical role in enabling validation, data exchange, and optimized
processing of XML. The W3C's XML Schema Definition (XSD) has emerged as the primary schema language,
but several important alternatives exist to meet different needs.

## XML Schema Basics

### XML Schema Abstract Data Model

The XML Schema abstract data model defines the building blocks that make up a schema. An XML Schema
is a set of schema components, which fall into 3 main groups:

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

During validation, declaration components like element and attribute declarations are associated by
name to the information items being validated. Definition components like simple and complex types
define internal schema components that can be referenced by other components.

### Schema Components and Their Properties

Each kind of schema component has specific properties that define its behavior and constraints. For
example:

-   Attribute Declarations have properties like {name}, {target namespace}, {type definition},
    {scope}, {value constraint}, etc.

-   Complex Type Definitions have properties like {name}, {target namespace}, {attribute uses},
    {content type}, {prohibited substitutions}, etc.

-   Element Declarations have properties like {name}, {target namespace}, {type definition},
    {identity-constraint definitions}, {nillable}, etc.

Some properties are required while others are optional. The values of these properties determine how
the component behaves in validation and its constraints on XML documents.

### Constraints and Validation Rules in XML Schema

XML Schema provides several kinds of constraints and validation rules that schema components specify
for XML documents:

1. Constraints on the schema components themselves (Schema Component Constraints) - conditions
   components must satisfy to be valid schema components

2. Constraints on the XML representation of schema components (Schema Representation Constraints) -
   rules for the XML elements/attributes used to represent the schema component

3. Validation rules - the actual validation checking of XML documents performed by schema
   validators, as specified by each schema component

4. Schema information set contributions - augmentations to the post-schema-validation infoset (PSVI)
   that provide additional info based on schema validation results

These different categories of constraints enforce validity at the schema component level, schema
document level, and XML instance document level.

### Conformance Requirements for XML Schema Processors

The XML Schema spec defines different conformance requirements for processors:

-   Minimally conforming processors must completely implement all Schema Component Constraints,
    Validation Rules, and Schema Information Set Contributions.

-   Processors that claim to conform to the XML Representation of Schemas must additionally
    implement all Schema Representation Constraints when processing schema documents.

-   Fully conforming processors must be minimally conforming, conform to the XML Representation of
    Schemas, and be able to access schema documents from the Web per additional rules.

So in summary, the XML Schema abstract model provides a framework for defining schema components,
their properties, and the constraints and rules they impose on XML documents. Processors have
different levels of conformance based on how completely they implement the different categories of
constraints in the abstract model.

## Schema Document Structure

### Anatomy of an XML Schema Document

An XML Schema document is an XML document that defines the structure, content and semantics of
another XML document. The root element of an XML Schema document is the `<schema>` element, which is
defined in the XML Schema namespace `http://www.w3.org/2001/XMLSchema`.

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

The schema components defined within the `<schema>` element belong to the target namespace specified
by the `targetNamespace` attribute.

### The schema Element and Its Attributes

The `<schema>` element is the root element of every XML Schema. It contains definitions and
declarations for the schema components that make up the schema.

Some of the important attributes of the `<schema>` element are:

-   `targetNamespace` - Specifies the namespace that the schema components belong to
-   `elementFormDefault` and `attributeFormDefault` - Specifies whether locally declared elements
    and attributes must be qualified with a namespace prefix
-   `blockDefault` - Specifies which type derivations are not allowed in the schema
-   `finalDefault` - Specifies which type derivations and restrictions cannot be further derived in
    the schema

The `<schema>` element may also contain attributes from other namespaces for extensibility.

### Defining the Target Namespace

The `targetNamespace` attribute on the `<schema>` element defines the namespace URI that the schema
components in the schema document belong to. This serves to avoid naming conflicts between schema
components defined in different schemas.

For example:

```xml
<xs:schema
    xmlns:xs="http://www.w3.org/2001/XMLSchema"
    targetNamespace="http://www.example.com/myschema"
>
  ...
</xs:schema>
```

Here, the schema components are associated with the namespace `http://www.example.com/myschema`. XML
instance documents that conform to this schema must use this namespace for its elements and
attributes.

If the `targetNamespace` is not specified, the schema components do not belong to any namespace.
Note that an empty string value for `targetNamespace` is not equivalent to omitting it - it puts the
components into a namespace with an empty URI.

### Including and Importing Schema Documents

XML Schema allows splitting the schema definitions into multiple schema documents. Schema components
from these documents can be assembled together in two ways:

1. Using `<include>` to include schema components from another schema document having the same
   target namespace. The included components become part of the including schema.

2. Using `<import>` to reference schema components from an external schema with a different target
   namespace. The imported components remain in a separate namespace, but can be referenced.

Both `<include>` and `<import>` take a `schemaLocation` attribute that provides a hint to the XML
processor about where to find the referenced schema document. However, the processor is free to
locate the document using other means as well.

For example:

```xml
<xs:schema
    xmlns:xs="http://www.w3.org/2001/XMLSchema"
    targetNamespace="http://www.example.com/myschema"
>

  <xs:include schemaLocation="myschema-base.xsd" />

  <xs:import
        namespace="http://www.example.com/ext"
        schemaLocation="extension.xsd"
    />

  ...
</xs:schema>
```

In summary, an XML Schema document is a structured XML document with a `<schema>` root element that
defines a set of schema components within a target namespace. The schema can be modularized into
multiple documents using `<include>` and `<import>`. This allows defining complex schemas in a
manageable way by assembling schema components from multiple namespaces.

## Defining Elements

### Declaring Elements with the element Element

Elements are declared in XML Schema using the `<element>` element. The `<element>` element is used
to define the name, type, and cardinality constraints of an element that can appear in an XML
document instance.

For example:

```xml
<xs:element name="customer" type="xs:string" />
```

This declares an element named "customer" of type `xs:string`.

### Element Names, Types, and Cardinality Constraints

When declaring an element, you specify the following key properties:

-   `name` - Specifies the name of the element. Required for global elements.
-   `type` - Specifies the data type of the element's content. Can refer to a built-in schema type
    like `xs:string` or a custom simple or complex type defined in the schema.
-   `minOccurs` and `maxOccurs` - Specifies the minimum and maximum number of times the element can
    appear. Default is 1 for both. Setting `maxOccurs="unbounded"` allows the element to repeat any
    number of times.

For example:

```xml
<xs:element name="address" minOccurs="1" maxOccurs="unbounded">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="street" type="xs:string" />
      <xs:element name="city" type="xs:string" />
    </xs:sequence>
  </xs:complexType>
</xs:element>
```

This declares an "address" element that must appear at least once but can be repeated. Its content
is defined inline as a complex type with a sequence of "street" and "city" elements.

### Global vs Local Element Declarations

Elements can be declared globally, as direct children of the `<schema>` element, or locally within a
complex type definition.

-   Global element declarations define standalone elements that can be referenced throughout the
    schema. They must have a unique name within the schema's target namespace.

-   Local element declarations define elements within the context of a particular complex type. They
    do not need to have unique names and cannot be referenced from outside their containing type.

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

Here, "customer" is a global element that references the "customerType" complex type. "name" and
"address" are local elements declared within "customerType".

### Abstract Elements and Substitution Groups

An element can be declared as abstract using the `abstract="true"` attribute. An abstract element
cannot appear directly in an instance document, but can be used as the head of a substitution group.

A substitution group allows elements to be substituted for the abstract head element. Elements in
the group must have the same type as the head element or a type derived from the head element's
type.

For example:

```xml
<xs:element name="shape" type="shapeType" abstract="true"/>
<xs:element name="circle" type="circleType" substitutionGroup="shape"/>
<xs:element name="square" type="squareType" substitutionGroup="shape"/>
```

This defines an abstract "shape" element as the head of a substitution group. The "circle" and
"square" elements can be used wherever "shape" is referenced.

So in summary, the `<element>` element is used to declare elements in an XML Schema, specifying
their names, types, and constraints. Elements can be declared globally or locally, and advanced
features like abstract elements and substitution groups provide flexibility in XML document
structures.

## Defining Attributes

### Declaring Attributes with the attribute Element

Attributes are declared in XML Schema using the `<attribute>` element. The `<attribute>` element is
used to define the name, type, default values, and other properties of an attribute that can appear
on an element in an XML document instance.

For example:

```xml
<xs:attribute name="customerID" type="xs:integer" />
```

This declares an attribute named "customerID" of type `xs:integer`.

### Attribute Names, Types, and Default Values

When declaring an attribute, you specify the following key properties:

-   `name` - Specifies the name of the attribute. Required unless `ref` is used.
-   `type` - Specifies the data type of the attribute's value. Can refer to a built-in schema type
    like `xs:string`, `xs:integer`, `xs:date`, etc. or a custom simple type defined in the schema.
-   `default` - Specifies a default value for the attribute. If the attribute is not present in an
    instance document, the schema processor will provide this value.
-   `fixed` - Specifies a fixed value that the attribute must have. Mutually exclusive with
    `default`.

For example:

```xml
<xs:attribute name="country" type="xs:string" fixed="US" />
```

This declares a "country" attribute with a fixed value of "US". If the attribute appears, it must
have this value, and if it is omitted, the schema processor will provide it.

### Attribute References and Attribute Groups

Instead of defining an attribute directly within an element declaration, you can define it as a
global `<attribute>` child of the `<schema>` element and then reference it using the `ref`
attribute:

```xml
<xs:attribute name="customerID" type="xs:integer"/>

<xs:complexType name="customerType">
  <xs:attribute ref="customerID"/>
</xs:complexType>
```

Attribute groups allow bundling a set of attribute declarations for reuse. They are defined using
the `<attributeGroup>` element and referenced using `<attributeGroup ref="...">`:

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

The `<anyAttribute>` element allows specifying a wildcard for attributes from a particular namespace
or namespaces. This enables elements to have attributes not explicitly declared in the schema.

The `namespace` attribute specifies which namespaces the wildcard allows attributes from - e.g.
`##any` allows attributes from any namespace. The `processContents` attribute indicates how the
schema processor should handle validation of these attributes - e.g. `lax` means validating them if
a schema is available, but not raising errors otherwise.

For example:

```xml
<xs:complexType name="openType">
  <xs:anyAttribute namespace="##any" processContents="skip" />
</xs:complexType>
```

This allows elements of type `openType` to have any attributes from any namespace, without requiring
those attributes to be validated.

So in summary, the `<attribute>` element is used to declare attributes in XML Schema, specifying
their names, types, default/fixed values, and other properties. Attributes can be declared locally
or globally and grouped for reuse. The `<anyAttribute>` element provides a wildcard mechanism to
allow undeclared attributes from specified namespaces.

## Simple Types

### Overview of Built-in Simple Types

XML Schema provides a set of 44 built-in simple types that can be used directly to specify the type
of elements and attributes. These include:

-   19 primitive types like `string`, `boolean`, `decimal`, `float`, `double`, `duration`,
    `dateTime`, `time`, `date`, `gYearMonth`, `gYear`, `gMonthDay`, `gDay`, `gMonth`, `hexBinary`,
    `base64Binary`, `anyURI`, `QName`, `NOTATION`

-   25 derived types built on the primitive types, such as `normalizedString`, `token`, `language`,
    `Name`, `NCName`, `ID`, `IDREF`, `ENTITY`, `integer`, `nonPositiveInteger`, `negativeInteger`,
    `long`, `int`, `short`, `byte`, `nonNegativeInteger`, `unsignedLong`, `unsignedInt`,
    `unsignedShort`, `unsignedByte`, `positiveInteger`

These built-in types form the foundation from which custom simple types can be derived.

### Defining Custom Simple Types

New simple types are defined by deriving them from existing simple types (built-in's and derived).
We can derive a new simple type by restricting an existing simple type, in other words, the legal
range of values for the new type are a subset of the existing type's range of values.

We use the `<simpleType>` element to define and name the new simple type. Within `<simpleType>`, we
use the `<restriction>` element to indicate the existing base type, and to specify the facets that
constrain the range of values.

For example, to create a new type of integer called "myInteger" whose range of values is between
10000 and 99999 inclusive:

```xml
<xsd:simpleType name="myInteger">
  <xsd:restriction base="xsd:integer">
    <xsd:minInclusive value="10000" />
    <xsd:maxInclusive value="99999" />
  </xsd:restriction>
</xsd:simpleType>
```

This derives `myInteger` by restricting the base type `integer` using the `minInclusive` and
`maxInclusive` facets.

### Simple Type Restrictions and Facets

Each simple type, whether built-in or derived, has a set of constraining facets that can be applied
to it. Which facets are applicable depends on the specific base type. The available facets are:

-   `length` - restricts the number of characters/list items allowed
-   `minLength` - restricts the minimum number of characters/list items
-   `maxLength` - restricts the maximum number of characters/list items
-   `pattern` - restricts values to those that match a regular expression
-   `enumeration` - restricts values to a specified set of values
-   `whiteSpace` - specifies how whitespace is handled
-   `maxInclusive` - specifies maximum value (inclusive)
-   `maxExclusive` - specifies maximum value (exclusive)
-   `minExclusive` - specifies minimum value (exclusive)
-   `minInclusive` - specifies minimum value (inclusive)
-   `totalDigits` - restricts the total number of digits
-   `fractionDigits` - restricts the number of fractional digits

When defining a custom simple type by restriction, you specify one or more of these facets to
constrain the allowed values. The facets used must be applicable to the base type.

### List and Union Simple Types

In addition to restricting a simple type, you can also define new simple types as a list or union of
other simple types.

A list type is a whitespace-separated list of values of a specified simple type. To define a list
type, use a `<list>` element inside `<simpleType>` specifying the `itemType` attribute:

```xml
<xsd:simpleType name="myIntList">
  <xsd:list itemType="xsd:int" />
</xsd:simpleType>
```

A union type allows a value to be one of several specified simple types. To define a union type, use
a `<union>` element inside `<simpleType>` specifying the `memberTypes` attribute with a list of
types:

```xml
<xsd:simpleType name="myIntOrString">
  <xsd:union memberTypes="xsd:int xsd:string" />
</xsd:simpleType>
```

So in summary, XML Schema provides a rich set of built-in simple types that can be used directly or
as the basis for deriving new custom simple types. Custom types are defined by restricting an
existing type using facets, or by creating list and union types. This allows schemas to precisely
specify the valid structure and content of conforming XML documents.

## Complex Types

### Defining Complex Types with the complexType Element

Complex types are used to define elements that contain other elements and/or attributes. They are
defined using the `<complexType>` element in an XML Schema.

The `<complexType>` element has several key attributes:

-   `name` - Specifies a name for the complex type. Required if the type is being defined globally
    as a child of the `<schema>` element.
-   `abstract` - If set to true, the complex type cannot be used directly in instance documents and
    must be extended by another complex type. Default is false.
-   `mixed` - If set to true, the complex type can contain a mixture of elements and text content.
    Default is false.

For example:

```xml
<xs:complexType name="personType">
  <xs:sequence>
    <xs:element name="firstName" type="xs:string" />
    <xs:element name="lastName" type="xs:string" />
  </xs:sequence>
  <xs:attribute name="age" type="xs:positiveInteger" />
</xs:complexType>
```

This defines a complex type named `personType` that contains a sequence of `firstName` and
`lastName` elements, and an `age` attribute.

### Content Models - Simple Content, Complex Content, Mixed Content

The content of a complex type can be specified using one of three content models:

1. Simple content - contains only text and attributes, no child elements. Defined using
   `<simpleContent>`.

2. Complex content - contains only child elements and attributes, no text. Defined using
   `<complexContent>` with a nested `<sequence>`, `<choice>`, or `<all>` element.

3. Mixed content - contains a mixture of text and child elements. Enabled by setting the `mixed`
   attribute to true on the `<complexType>`.

For example, a complex type with simple content:

```xml
<xs:complexType name="nameType">
  <xs:simpleContent>
    <xs:extension base="xs:string">
      <xs:attribute name="language" type="xs:string" />
    </xs:extension>
  </xs:simpleContent>
</xs:complexType>
```

And a complex type with mixed content:

```xml
<xs:complexType name="letterType" mixed="true">
  <xs:sequence>
    <xs:element name="name" type="xs:string" />
    <xs:element name="orderid" type="xs:positiveInteger" />
    <xs:element name="shipdate" type="xs:date" />
  </xs:sequence>
</xs:complexType>
```

### Deriving Complex Types by Extension and Restriction

New complex types can be derived from existing complex types using either extension or restriction.
This allows reuse and refinement of type definitions.

Extension adds new elements or attributes to the end of the base type's content model. It's defined
using an `<extension>` element inside `<complexContent>`:

```xml
<xs:complexType name="fullpersoninfo">
  <xs:complexContent>
    <xs:extension base="personinfo">
      <xs:sequence>
        <xs:element name="address" type="xs:string" />
        <xs:element name="city" type="xs:string" />
        <xs:element name="country" type="xs:string" />
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

Restriction limits the content allowed in the base type, e.g. by removing elements or making
optional elements required. It's defined using a `<restriction>` element:

```xml
<xs:complexType name="restrictedpersoninfo">
  <xs:complexContent>
    <xs:restriction base="personinfo">
      <xs:sequence>
        <xs:element name="firstName" type="xs:string" />
        <xs:element name="lastName" type="xs:string" />
      </xs:sequence>
    </xs:restriction>
  </xs:complexContent>
</xs:complexType>
```

### Abstract Types and Final Types

Complex types can be defined as abstract using the `abstract` attribute. An abstract type cannot be
used directly in instance documents, only extended by other types.

The `final` attribute prevents further derivation of the complex type by extension and/or
restriction. It can contain `#all` (blocks all derivation), `extension` (blocks extension), or
`restriction` (blocks restriction).

For example:

```xml
<xs:complexType name="baseType" abstract="true" final="restriction">
  <xs:sequence>
    <xs:element name="id" type="xs:string" />
  </xs:sequence>
</xs:complexType>
```

This defines an abstract base type that cannot be restricted, only extended.

So in summary, the `<complexType>` element is used to define elements that contain other elements
and attributes. The content can be simple, complex or mixed. Complex types support inheritance by
extension and restriction, and can be made abstract or final to control derivation. This provides a
powerful mechanism for defining structured, reusable data models in XML Schema.

## Named Model Groups

### Defining Reusable Content Models with the group Element

The `<group>` element allows defining a named model group that contains a set of element
declarations or references. This enables reusing common content models across multiple complex
types.

A model group is defined by specifying a name and a content model within the `<group>` element:

```xml
<xs:group name="myModelGroup">
  <xs:sequence>
    <xs:element ref="firstName" />
    <xs:element ref="lastName" />
  </xs:sequence>
</xs:group>
```

This defines a model group named "myModelGroup" consisting of a sequence of "firstName" and
"lastName" element references.

### Referencing Model Groups in Complex Types

To reuse a named model group, it is referenced within the content model of a complex type definition
using a `<group>` element with a `ref` attribute pointing to the group name:

```xml
<xs:complexType name="personType">
  <xs:sequence>
    <xs:group ref="myModelGroup" />
    <xs:element name="age" type="xs:integer" />
  </xs:sequence>
</xs:complexType>
```

Here, the "myModelGroup" is incorporated into the content model of the "personType" complex type.
It's as if the content of "myModelGroup" was copied directly into the complex type definition.

Model groups can also be referenced within other named model groups, allowing nested reuse of
content models.

### Deriving Model Groups by Restriction

Although model groups cannot be derived by extension, the XML Schema spec allows deriving a model
group by restriction to a limited degree.

When a `<group>` element with a `name` attribute appears inside a `<redefine>` element, it can
restrict the model group it refers to in its `ref` attribute by removing elements or constraining
their occurrence.

For example:

```xml
<xs:redefine schemaLocation="base.xsd">
  <xs:group name="restrictedGroup">
    <xs:restriction base="originalGroup">
      <xs:sequence>
        <xs:element ref="a" />
        <xs:element ref="b" minOccurs="0" />
      </xs:sequence>
    </xs:restriction>
  </xs:group>
</xs:redefine>
```

This derives a new group "restrictedGroup" by restricting "originalGroup", making the "b" element
optional. The redefined group is only available within the schema that contains the `<redefine>`.

So in summary, named model groups provide a way to define reusable content models that can be
referenced in multiple complex types. While they don't support derivation by extension, a limited
form of restriction is possible when redefining groups. This promotes modular schema design and
avoids duplication of similar content models.

## Named Attribute Groups

### Defining Reusable Attribute Declarations with attributeGroup

The `<attributeGroup>` element allows defining a named group of attribute declarations that can be
referenced and reused in multiple complex type definitions. This promotes modularization and avoids
duplication of common attributes across the schema.

An attribute group is defined by specifying a name and one or more attribute declarations or
references within the `<attributeGroup>` element:

```xml
<xs:attributeGroup name="personAttrGroup">
  <xs:attribute name="firstName" type="xs:string" />
  <xs:attribute name="lastName" type="xs:string" />
  <xs:attribute name="age" type="xs:positiveInteger" />
</xs:attributeGroup>
```

This defines an attribute group named "personAttrGroup" consisting of "firstName", "lastName" and
"age" attribute declarations.

### Referencing Attribute Groups in Complex Types

To reuse a named attribute group, it is referenced within the complex type definition using an
`<attributeGroup>` element with a `ref` attribute pointing to the group name:

```xml
<xs:complexType name="personType">
  <xs:sequence>
    <xs:element name="address" type="addressType" />
  </xs:sequence>
  <xs:attributeGroup ref="personAttrGroup" />
</xs:complexType>
```

Here, the "personAttrGroup" is incorporated into the "personType" complex type. It's as if the
attribute declarations in "personAttrGroup" were copied directly into the complex type.

Attribute groups can be referenced in multiple complex types, enabling consistent and centralized
definitions of common attributes.

### Extending and Restricting Attribute Groups

Unlike named model groups, attribute groups do support derivation by both extension and restriction
to a limited degree.

To extend an attribute group, define a new group that references the base group and adds new
attribute declarations:

```xml
<xs:attributeGroup name="fullPersonAttrGroup">
  <xs:attributeGroup ref="personAttrGroup" />
  <xs:attribute name="gender" type="xs:string" />
</xs:attributeGroup>
```

This creates an extended version of "personAttrGroup" that includes an additional "gender"
attribute.

To restrict an attribute group, the new group definition must be nested inside a `<redefine>`
element that references the schema containing the base group:

```xml
<xs:redefine schemaLocation="base.xsd">
  <xs:attributeGroup name="restrictedPersonAttrGroup">
    <xs:restriction base="personAttrGroup">
      <xs:attribute name="firstName" type="xs:string" />
      <xs:attribute name="lastName" type="xs:string" />
    </xs:restriction>
  </xs:attributeGroup>
</xs:redefine>
```

This restricts "personAttrGroup" to only allow the "firstName" and "lastName" attributes, omitting
"age". The redefined group is only available within the schema that contains the `<redefine>`.

So in summary, the `<attributeGroup>` element enables defining reusable sets of attribute
declarations that can be referenced by name in complex type definitions. Attribute groups support
derivation by extension to add attributes, and restriction to limit attributes, allowing flexible
and modular attribute definitions in an XML Schema.

## Identity Constraints

### Defining Uniqueness and Reference Constraints

XML Schema provides three elements for defining identity constraints:

1. `<unique>` - Specifies that an element or attribute value (or combination of values) must be
   unique within a specified scope.

2. `<key>` - Specifies a uniqueness constraint like `<unique>`, and additionally requires that the
   value(s) must be present (i.e. cannot be null).

3. `<keyref>` - Specifies a reference constraint that requires the value(s) to match those of a
   `<key>` or `<unique>` constraint in the specified scope.

Each of these elements contains a `<selector>` element specifying the elements the constraint
applies to, and one or more `<field>` elements specifying the element/attribute values to be
checked.

For example:

```xml
<xs:element name="library">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="book" maxOccurs="unbounded">
        <xs:complexType>
          <xs:sequence>
            <xs:element name="title" type="xs:string" />
            <xs:element name="author" type="xs:string" />
            <xs:element name="isbn" type="xs:string" />
          </xs:sequence>
        </xs:complexType>
      </xs:element>
    </xs:sequence>
  </xs:complexType>

  <xs:unique name="uniqueISBN">
    <xs:selector xpath="book" />
    <xs:field xpath="isbn" />
  </xs:unique>
</xs:element>
```

This defines a `<unique>` constraint named "uniqueISBN" specifying that the `isbn` element value
must be unique across all `book` elements within the `library` element.

### Using XPath Expressions in selector and field Elements

The `<selector>` and `<field>` elements use XPath expressions to specify the target elements and
values for the constraint:

-   The `<selector>` element's `xpath` attribute contains an XPath expression relative to the
    constraint's parent element, specifying the set of elements the constraint applies to.

-   Each `<field>` element's `xpath` attribute contains an XPath expression relative to elements
    selected by `<selector>`, specifying the element/attribute value(s) to check.

The XPath subset allowed in `<selector>` is:

-   `Path` separated by `|`
-   `Path` is `('.//')? ( Step ('/' Step)* )?`
-   `Step` is `.` or `NameTest`
-   `NameTest` is `QName` or `*` or `NCName:*`

The XPath subset allowed in `<field>` is:

-   `.` or `@` followed by a `NameTest`
-   `NameTest` is `QName` or `*` or `NCName:*`

### Specifying Scope for Identity Constraints

The scope of an identity constraint is determined by its location in the schema:

-   If defined as a child of an element declaration, the constraint applies to all instances of that
    element. This is called "element scope".

-   If defined within a complex type definition, the constraint applies to all elements of that
    type. This is called "type scope".

-   The top-level `<schema>` element can also contain identity constraints that apply globally.

For example:

```xml
<xs:element name="library">
  <xs:unique name="globalBookTitle">
    <xs:selector xpath=".//book" />
    <xs:field xpath="title" />
  </xs:unique>
</xs:element>
```

This constraint with "element scope" specifies that `book/title` values must be unique within the
entire `library` element and its descendants.

So in summary, XML Schema's `<unique>`, `<key>` and `<keyref>` elements allow defining uniqueness
and reference constraints on element/attribute values using XPath expressions. The scope of the
constraints is determined by their location in the schema. This provides a flexible way to enforce
integrity of XML data beyond just single attributes.

## Annotations and Documentation

### Adding Annotations with the annotation Element

The `<annotation>` element allows adding annotations to schema components for documentation or
application-specific information. Annotations do not affect the schema's meaning but provide
additional information for users and applications.

An `<annotation>` can be added as the first child of any schema component, such as `<schema>`,
`<element>`, `<attribute>`, `<simpleType>`, `<complexType>`, etc. It contains one or more
`<documentation>` and/or `<appinfo>` elements.

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

This adds an annotation to the "product" element declaration with both documentation and application
info.

### User Information with the documentation Element

The `<documentation>` element is used to provide human-readable information about the schema
component it annotates. The content of `<documentation>` can be any text or well-formed XML.

Multiple `<documentation>` elements can be included to provide the information in different
languages. The `xml:lang` attribute specifies the language used.

For example:

```xml
<xs:documentation xml:lang="en">English description</xs:documentation>
<xs:documentation xml:lang="fr">Description en français</xs:documentation>
```

The information in `<documentation>` is intended for schema users to better understand the purpose
and usage of the annotated component.

### Application Information with the appinfo Element

The `<appinfo>` element is used to provide information for applications that process the schema or
XML documents based on it. The content of `<appinfo>` can be any well-formed XML.

The `source` attribute of `<appinfo>` specifies a URI reference indicating the source or purpose of
the application information. This allows distinguishing between different types of app info.

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

This includes two `<appinfo>` elements with different `source` URIs to separate display-related and
persistence-related information.

The specific format and meaning of the content inside `<appinfo>` is defined by the applications
that use it. The schema processor does not validate or interpret it.

So in summary, the `<annotation>` element, along with its `<documentation>` and `<appinfo>`
children, allows attaching human-readable documentation and application-specific information to XML
Schema components. This provides a standard way to enrich schemas with additional metadata without
affecting their core meaning and validation behavior.

## Modularizing Schemas

### Strategies for Modularizing Large Schemas

When working with large and complex schemas, it's important to modularize them into smaller, more
manageable pieces. Some strategies for doing this include:

1. Splitting the schema into multiple files based on logical groupings of components. For example,
   having separate files for elements, complex types, simple types, etc.

2. Using the `<include>` element to compose a schema from multiple schema documents addressing the
   same namespace. This allows physically separating components while still treating them as part of
   one logical schema.

3. Using the `<import>` element to reference components from schemas with different target
   namespaces. This enables reuse across schema modules.

4. Defining reusable groups of elements and attributes via named model groups (`<group>`) and
   attribute groups (`<attributeGroup>`). These can be referenced from multiple type definitions.

5. Deriving new types from existing ones using `<extension>` and `<restriction>` rather than always
   defining new types from scratch.

The goal is to break down the schema into smaller, self-contained modules with clear dependencies
that are easier to understand, maintain and reuse.

### Includes, Imports and Redefines

XML Schema provides three main mechanisms for modularizing and combining schemas:

1. `<include>` - Allows combining multiple schema documents that have the same target namespace into
   a single logical schema. The included components become part of the including schema.

2. `<import>` - Allows referencing components from an external schema with a different target
   namespace. The imported components remain in a separate namespace and are used by reference.

3. `<redefine>` - Allows including an external schema document with the ability to redefine certain
   components in it. The redefined components replace the originals within the redefining schema.
   However, `<redefine>` is deprecated in the latest version of XML Schema.

Both `<include>` and `<import>` take a `schemaLocation` attribute that specifies the URI of the
schema document to be included or imported. Cyclic dependencies via `<include>` and `<import>` are
allowed.

### Chameleon Design Pattern for Schema Composition

The chameleon design pattern is a technique for authoring schema documents intended to be included
in other schemas without specifying a target namespace. When such a "chameleon" schema is included
in another schema, it takes on the including schema's target namespace (if any).

This allows writing schema components that can be reused across multiple schemas with different
target namespaces. Any references to unqualified components within the chameleon schema will
automatically resolve to the including schema's namespace.

To use the chameleon pattern:

1. Author a schema document without specifying a `targetNamespace` attribute on the `<schema>`
   element.

2. Include this schema in other schemas using `<include>`.

3. The included components will adopt the enclosing schema's target namespace if it has one, or
   remain unqualified if it does not.

This provides flexibility in authoring reusable schema modules that can be namespace-independent.

So in summary, XML Schema provides several mechanisms for modularizing large schemas and assembling
them from smaller parts. `<include>` and `<import>` allow combining schemas in the same or different
namespaces, while the chameleon pattern enables writing namespace-neutral schema modules. Effective
use of these techniques can make complex schemas much more manageable.

## Namespaces and Schema Composition

Namespaces and Schema Composition in XML schemas involve several key concepts:

### Target Namespaces and Unqualified Locals

**Target Namespace**: The `targetNamespace` attribute in an XML Schema (XSD) specifies the namespace
in which all the elements and types defined by the schema reside. This is crucial for avoiding name
clashes and ensuring that elements and types from different schemas can be used together without
ambiguity. The target namespace is what differentiates elements and types with the same name but
defined in different schemas.

**Unqualified Locals**: Elements and attributes within an XML document can be either qualified or
unqualified. Qualification refers to whether an element or attribute's name includes a namespace
prefix. The `elementFormDefault` attribute in an XSD can be set to "qualified" to require elements
to be namespace-qualified, or "unqualified" to allow them without a namespace. Attributes are
unqualified by default and can be made qualified using the `attributeFormDefault` attribute.

### Assembling a Schema Multiple Documents and Namespaces

XML Schemas can be modular, allowing definitions to be split across multiple documents. This is
achieved using the `include`, `import`, and `redefine` mechanisms. `include` is used for bringing in
definitions from another schema document within the same namespace, while `import` is used for
incorporating definitions from a schema document that declares a different target namespace. This
modularity supports reusability and maintainability of schema definitions.

### Namespace-Related Schema Composition Constraints

When composing schemas from multiple documents and namespaces, it's important to manage namespace
declarations and references correctly. Each schema document must correctly declare its target
namespace and any other namespaces it references. When using elements or types from another
namespace, the correct namespace prefix must be used to qualify these references. This ensures that
the composed schema is correctly interpreted by parsers and validators.

In summary, namespaces and schema composition in XML schemas are essential for defining clear,
unambiguous vocabularies in XML documents. They enable the use of multiple schemas together,
allowing for modular and reusable schema definitions. Proper management of target namespaces,
qualified and unqualified names, and correct referencing of external namespaces are key to effective
schema composition.

## Schema Extensibility

### Extensibility Mechanisms in XML Schema

XML Schema is designed to support complex data structures and to be extensible, allowing schemas to
evolve over time without breaking compatibility with existing XML documents. Extensibility
mechanisms in XML Schema include:

-   **Wildcards (`<xs:any>` and `<xs:anyAttribute>`):** These elements allow for the inclusion of
    elements and attributes not explicitly defined in the schema, providing flexibility in XML
    document structures. The `<xs:any>` element can be used within complex type definitions to allow
    for any elements from a specified namespace, and `<xs:anyAttribute>` allows for any attributes
    from a specified namespace.

-   **Substitution Groups:** Substitution groups allow one element to be substituted for another in
    instance documents, enabling polymorphism. An element declared as abstract serves as a
    placeholder that can be replaced by any element that is a member of its substitution group.

-   **Type Derivation:** XML Schema allows for the derivation of new types from existing types by
    extension or restriction. This enables schema authors to create new types that add additional
    constraints or extend existing types with new elements and attributes.

### Adding Elements and Attributes Not Defined in the Schema

To add elements and attributes not defined in the schema, XML Schema provides:

-   **Element Wildcards (`<xs:any>`):** Used within complex type definitions to specify that
    elements from a certain namespace (or any namespace) can appear at a certain point in the
    document structure. The `processContents` attribute controls how strictly the schema processor
    checks these elements.

-   **Attribute Wildcards (`<xs:anyAttribute>`):** Allow for the inclusion of attributes from
    specified namespaces not explicitly defined in the schema. This is useful for adding metadata or
    other information that may vary between instances or over time.

### Controlling Extensibility with final and block Attributes

XML Schema provides attributes to control the extensibility of types and elements:

-   **The `final` Attribute:** Can be used on complex type definitions to prevent derivation of new
    types from the type. The `final` attribute can specify that no new types can be derived
    (`#all`), or it can prevent derivation by restriction, extension, or both.

-   **The `block` Attribute:** Can be used on element declarations to prevent specific types of
    substitutions or derivations for that element. For example, it can block substitution of the
    element by elements from its substitution group or prevent the use of types derived by
    restriction or extension.

-   **The `finalDefault` and `blockDefault` Attributes:** These attributes on the `<xs:schema>`
    element set default values for the `final` and `block` attributes for all types and elements
    within the schema, providing a way to globally control extensibility and substitution behaviors.

In summary, XML Schema's extensibility mechanisms, such as wildcards, substitution groups, and type
derivation, allow for flexible and evolving XML document structures. At the same time, the `final`
and `block` attributes offer schema authors tools to control and limit this extensibility, ensuring
that extensions and modifications do not compromise the integrity or intended use of the schema.

## Using Schemas for Validation

XML Schemas play a crucial role in ensuring the correctness and validity of XML documents by
defining the structure, content, and semantics that the documents must adhere to. Here's how schemas
are used for validation, including associating schemas with XML documents, handling validation
outcomes and errors, and understanding the validation rules for elements and attributes, as well as
the concept of the Post-Schema-Validation Infoset (PSVI).

### Associating Schemas with XML Documents

To validate an XML document against an XML Schema, the document must be associated with the schema.
This can be done directly within the XML document by specifying the `xsi:schemaLocation` or
`xsi:noNamespaceSchemaLocation` attributes in the root element, which point to the location of the
schema file(s). XML parsers and validators use this information to perform validation against the
specified schema.

### Schema Validation Outcomes and Error Handling

The outcome of schema validation is binary: an XML document is either valid or invalid according to
the schema it is validated against. If the document is valid, it means it conforms to the structure,
content, and semantics defined by the schema. If the document is invalid, the validator typically
reports errors or warnings indicating why the document does not conform to the schema. Handling
these errors involves correcting the XML document to meet the schema's requirements.

### Validation Rules for Elements and Attributes

XML Schema defines validation rules for elements and attributes, including:

-   **Type constraints:** Elements and attributes must conform to the data type specified in the
    schema.
-   **Cardinality constraints:** The occurrence of elements and attributes must comply with the
    minimum and maximum occurrences defined.
-   **Structure constraints:** The organization and nesting of elements must match the sequence,
    choice, or all model defined in the schema.
-   **Uniqueness and key constraints:** Unique values and key references are validated to ensure
    data integrity within the XML document.

### Post-Schema-Validation Infoset (PSVI)

The PSVI is an augmented representation of an XML document that results from schema validation. It
includes the original document's content along with additional information derived from the schema,
such as normalized values, default values, and explicit data types for elements and attributes. The
PSVI provides a richer and more detailed view of the document's structure and content, enabling more
precise querying, transformation, and analysis. Applications can utilize the PSVI for advanced data
manipulation and validation beyond what is possible with the raw XML document alone.

In conclusion, using XML Schemas for validation is a powerful mechanism for ensuring that XML
documents adhere to predefined structures and rules. By associating schemas with documents, handling
validation outcomes, and understanding the validation rules, developers can enforce data integrity
and consistency. The PSVI further enhances the capabilities for processing and analyzing validated
documents, offering significant advantages in various IT domains.

## Advanced Techniques

XML Schema offers a range of advanced techniques that allow for more sophisticated and flexible
schema design. These techniques include conditional type assignment, inheriting and overriding
facets, type alternatives and default types, and assertions. Here's a detailed look at each of these
topics:

### Conditional Type Assignment

Conditional type assignment allows elements to have their type determined based on the value of
another element or attribute. This is achieved using the `xsi:type` attribute in instance documents,
which specifies the type of an element at runtime. This mechanism enables polymorphism and dynamic
type selection, making schemas more adaptable to different data scenarios.

### Inheriting and Overriding Facets

Facets in XML Schema define constraints on the values of elements and attributes. When deriving new
types from existing ones, facets can be inherited from the base type or overridden with new
constraints. This allows for the creation of more specific types that still adhere to the broader
constraints defined by the base type. Overriding facets can be done using the `<restriction>`
element, which allows for the modification or tightening of constraints.

### Type Alternatives and Default Types

XML Schema supports the concept of type alternatives, which allows an element to have one of several
possible types. This is achieved using the `<union>` element, which specifies a list of member types
that the element can have. The `<union>` element is particularly useful for elements that can
contain different kinds of data, such as numbers, strings, or even other complex types.

Default types are also an important aspect of XML Schema. When an element or attribute does not have
a specified type, the schema processor assigns a default type based on the context. For example, if
an element does not have a specified type, it defaults to `xs:anyType`, which allows any content.
Similarly, if an attribute does not have a specified type, it defaults to `xs:untypedAtomic`, which
allows any text content.

### Assertions and Type Alternatives

Assertions are conditions that must be true for an XML document to be valid according to the schema.
They are defined using the `<xs:assert>` element and can be used to enforce complex constraints that
cannot be expressed using the built-in facets. Assertions can be used in conjunction with type
alternatives to provide additional validation rules for elements that can have multiple types.

For example, an assertion can be used to ensure that an element of a union type has a specific value
when it is of a certain type:

```xml
<xs:element name="data">
 <xs:simpleType>
    <xs:union memberTypes="xs:string xs:integer">
      <xs:assert
                test="if (. instance of xs:string) then . = 'specificValue' else true()"
            />
    </xs:union>
 </xs:simpleType>
</xs:element>
```

This schema defines an element `data` that can be either a string or an integer. The assertion
ensures that if `data` is a string, it must have the value "specificValue".

In summary, XML Schema's advanced techniques, including conditional type assignment, inheriting and
overriding facets, type alternatives and default types, and assertions, provide powerful tools for
schema design. These techniques enable more flexible and expressive schema definitions, allowing for
complex validation rules and dynamic type selection.

Citations:

## Schema Design Best Practices

### General Schema Design Principles

-   **Understandability:** XML schemas should be clear, consistent, and unambiguous. They should
    contain human-readable documentation and, where appropriate, links to requirements or design
    documents.
-   **Semantic Completeness:** An XML schema should define every element and attribute that is
    understood by your solution when processing target documents.
-   **Constraining:** An XML schema is a contract that allows both the creator and the recipient of
    an XML document to verify that the instance document obeys the contract. Design your schema to
    constrain values for all elements and attributes that the application uses and relies on.
-   **Non-redundancy:** XML schemas should import and include other XML schema files rather than
    duplicating types and elements locally.
-   **Reusability:** XML schemas should be specified in such a way that types and elements can be
    leveraged by other XML schemas.
-   **Extensibility:** Design schemas to be extensible, allowing new elements and attributes to be
    inserted throughout the document. Use mechanisms like attribute and element wildcards,
    substitution groups, and type substitution to enable extensibility.

### Naming Conventions for Schema Components

-   Use Upper Camel Case (UCC) for all elements and attributes, avoiding hyphens, spaces, or other
    syntax.
-   Favor readability over tag length, but be mindful of the balance between document size and
    readability.
-   Avoid abbreviations and acronyms unless they are well known within your business area (e.g., ID
    for Identifier).
-   Postfix all types with the name 'Type' to distinguish between elements and complex types with
    the same name, which leads to confusion.
-   Enumerations should use names, not numbers, and the values should again be UCC.
-   Names should not include the name of the containing structure (e.g., CustomerName should be Name
    within the parent element Customer).

### Refactoring and Normalizing Schemas

-   Only produce complexTypes or simpleTypes for types that are likely to be re-used. If the
    structure will only exist in one place, define it inline with an anonymous complexType.
-   Avoid the use of mixed content to maintain clarity and structure within your XML documents.
-   Only define root-level elements if the element is capable of being the root element in an XML
    document. For global scope, create a root-level ComplexType or SimpleType instead.

### Versioning Strategies for Schemas

-   Think about versioning early on in your schema design. If backward compatibility is important,
    all additions to the schema should be optional.
-   Consider adding `any` and `anyAttribute` entries to the end of your definitions to accommodate
    future extensions without breaking existing documents.
-   Use a consistent naming or numbering convention to indicate major and minor versions, reflecting
    the extent of changes (e.g., v1.0 to v2.0 for major changes, v1.2 to v1.3 for minor extensions).
-   Change the target namespace for significant changes that alter the interpretation of some
    elements, ensuring that instance documents are explicitly updated to reflect the new schema
    version.

Implementing these best practices in XML schema design can significantly enhance the clarity,
reusability, and maintainability of your schemas, facilitating easier data exchange and validation.

## Schema Languages and Technologies

### Other XML Schema Languages - RELAX NG, Schematron

-   **RELAX NG:** A schema language for XML that is both simple and powerful. It offers a clean and
    straightforward way to define the structure of XML documents. RELAX NG can describe what
    elements can appear in a document, their attributes, and the textual content of elements,
    providing a flexible way to validate XML documents. It supports both an XML syntax and a
    compact, non-XML syntax, making it adaptable to different use cases.

-   **Schematron:** Unlike traditional schema languages that focus on document structure, Schematron
    is rule-based and uses XPath expressions to define constraints on the content of XML documents.
    It is particularly good at expressing conditions that involve relationships between different
    parts of a document. Schematron can be used on its own or in combination with other schema
    languages like RELAX NG or W3C XML Schema to provide additional validation rules.

### Comparison of Features and Limitations

-   **RELAX NG vs. W3C XML Schema:**

    -   RELAX NG is simpler and more flexible, making it easier to learn and use. It allows for the
        definition of patterns in XML documents in a straightforward manner.
    -   W3C XML Schema (XSD) provides a rich type system and allows for the specification of default
        values and fixed values for elements and attributes, which RELAX NG does not. However, XSD
        is more complex and verbose.

-   **Schematron:**
    -   Schematron's strength lies in its ability to specify complex relational constraints using
        XPath, which is not directly possible with RELAX NG or W3C XML Schema. However, specifying
        basic document structure with Schematron can be verbose and cumbersome.

### Combining Schemas from Multiple Languages

-   It is possible to combine schemas from different languages to leverage the strengths of each.
    For example, RELAX NG can be used for defining the basic structure of documents, W3C XML Schema
    for data typing, and Schematron for complex rules and constraints.
-   Some implementations support embedding Schematron rules within RELAX NG schemas, allowing for a
    powerful combination of structure, datatype validation, and complex rules.

### Code Generation and Data Binding

-   Code generation and data binding refer to the process of generating programming language data
    structures based on XML schema definitions, facilitating the easy manipulation of XML data in
    applications.
-   While the article sources do not directly address code generation and data binding, these
    processes are commonly supported by tools that work with W3C XML Schema due to its widespread
    adoption and tooling support. RELAX NG and Schematron, while powerful, may have less direct
    support for code generation and data binding, but tools like Trang can convert RELAX NG schemas
    to W3C XML Schema for use with such tools.

In summary, RELAX NG and Schematron offer powerful alternatives to W3C XML Schema, each with its own
set of features and best use cases. Combining these languages can provide comprehensive validation
capabilities that leverage the strengths of each. While W3C XML Schema is widely used and supported
for code generation and data binding, RELAX NG and Schematron's simplicity and flexibility make them
attractive for many applications.

## Schemas in Practice

### Schemas for Common XML Vocabularies

XML schemas are foundational in defining the structure and validating the content of XML documents
across various domains. Common XML vocabularies, such as RSS for web feeds, Atom for syndication,
SOAP for web services, and XHTML for web pages, rely on well-defined schemas to ensure consistency
and interoperability across different systems and platforms. For instance, RSS feeds use a specific
XML schema to standardize the way articles are published and syndicated online, enabling various
feed readers to interpret and display content correctly. Similarly, SOAP uses an XML schema to
define the structure of messages exchanged between web services, ensuring that requests and
responses are formatted and understood universally.

### Industry-specific Schema Usage - Finance, Healthcare, etc.

In industry-specific contexts, XML schemas play a crucial role in standardizing data exchange and
storage, facilitating compliance with regulations, and enabling seamless interoperability between
disparate systems.

-   **Finance:** Financial Information eXchange (FIX) and eXtensible Business Reporting Language
    (XBRL) are examples of XML-based standards used in the finance sector. FIX is used for real-time
    electronic exchange of securities transactions, while XBRL is used for reporting financial data.
    Both rely on XML schemas to define the structure and semantics of the data they handle, ensuring
    accuracy and consistency in financial communications and reporting.

-   **Healthcare:** Health Level Seven (HL7) is a set of international standards for the exchange,
    integration, sharing, and retrieval of electronic health information. HL7 uses XML schemas to
    define the structure of messages and documents exchanged across healthcare systems, supporting a
    wide range of administrative, clinical, and infrastructural functions in healthcare.

### Case Studies and Real-world Schema Examples

-   **Public Auctions:** A public auction platform might use XML schemas to define the structure of
    auction listings, bids, and user profiles. By adhering to a common schema, the platform ensures
    that auction data is consistent and interoperable across different systems, facilitating a
    seamless auction process from listing to bidding to sale.

-   **E-Government Services:** Government agencies often use XML schemas to standardize the
    structure of data exchanged in e-government services, such as tax filings, license applications,
    and public records requests. For example, the schema for a tax filing service would define the
    required fields, their data types, and constraints, ensuring that submissions are complete and
    valid.

### Combining Schemas from Multiple Languages

In complex systems, it may be necessary to combine schemas from multiple languages, such as XML
Schema, RELAX NG, and Schematron, to leverage the strengths of each. For instance, an XML Schema
might define the basic structure of a document, RELAX NG could be used for pattern-based validation,
and Schematron could enforce business rules through XPath expressions. Tools and libraries that
support multiple schema languages can be used to validate documents against these combined schemas,
ensuring comprehensive validation that covers structure, patterns, and business logic.

### Code Generation and Data Binding

Code generation and data binding refer to the process of automatically generating programming
language constructs from XML schemas, facilitating the manipulation of XML data in software
applications. Tools like JAXB (Java Architecture for XML Binding) allow developers to generate Java
classes from XML schemas, enabling easy access and manipulation of XML data in Java applications.
This approach simplifies the development process, reduces the likelihood of errors in data handling,
and improves maintainability by keeping the XML schema and the code in sync.

## Future of XML Schema

### Limitations and Criticisms of XML Schema 1.0

XML Schema 1.0, while providing a robust mechanism for defining the structure and constraining the
contents of XML documents, has faced several criticisms and limitations:

-   **Complexity:** XML Schema 1.0 is often criticized for its complexity and steep learning curve.
    The verbosity of the language can make schemas difficult to write and understand.
-   **Limited Support for Data Types:** Although XML Schema 1.0 offers a rich type system, it has
    limitations in expressing certain data types and constraints.
-   **Lack of Conditional Constraints:** XML Schema 1.0 lacks mechanisms for defining conditional
    constraints or co-occurrence constraints, making it difficult to express certain logical
    relationships between elements.

### New Features in XML Schema 1.1

XML Schema 1.1 introduced several new features to address the limitations of version 1.0 and to
provide more flexibility and power in schema design:

-   **Assertions:** XML Schema 1.1 allows for the use of XPath expressions to define complex
    constraints on the content of elements and attributes, enabling more sophisticated validation
    scenarios.
-   **Conditional Type Assignment:** It introduces conditional type assignment, allowing elements to
    have their type determined dynamically based on conditions.
-   **Support for Versioning:** XML Schema 1.1 includes features to support versioning of schemas,
    making it easier to evolve XML vocabularies over time without breaking compatibility.
-   **Enhanced Support for Co-occurrence Constraints:** The new version provides mechanisms for
    defining co-occurrence constraints, where the presence or value of one element or attribute can
    depend on the presence or value of another.

### Possible Future Directions for XML Schema

The future development of XML Schema may focus on further simplifying the language, enhancing
usability, and addressing any remaining limitations. Potential directions include:

-   **Improved Modularity and Reusability:** Enhancements to facilitate the modular design of
    schemas and the reuse of schema components across different schemas.
-   **Enhanced Support for Data Modeling:** Further improvements to the type system and validation
    capabilities to better support complex data modeling requirements.
-   **Integration with Other Technologies:** Closer integration with other XML-related standards and
    technologies to provide a more cohesive ecosystem for XML application development.

### Alternative Schema-aware Technologies on the Horizon

As XML technologies evolve, new schema languages and tools may emerge, offering alternative
approaches to defining and validating XML document structures:

-   **Lightweight Schema Languages:** New schema languages that aim for simplicity and ease of use,
    potentially offering a more accessible alternative to XML Schema for certain use cases.
-   **Schema Inference Tools:** Tools that can automatically generate schema definitions from XML
    document samples, simplifying the process of schema creation.
-   **Integrated Validation and Transformation Tools:** Tools that combine schema validation with
    XML transformation capabilities, enabling more powerful and flexible processing of XML
    documents.

In summary, while XML Schema continues to be a foundational technology for XML-based applications,
ongoing development and the emergence of alternative technologies will likely shape the future
landscape of XML schema definition and validation.

## Glossary of Terms

**XML (Extensible Markup Language):** A standard for building markup languages to describe the
structure of information.

**Schema:** A technology-neutral term for the definition of the structure of an XML document.

**Element:** A block of text in an XML document made up of a start and end tag, and the content
between the tags.

**Attribute:** A name and its value included inside an XML tag, specifying additional information
about an element.

**Document Type Definition (DTD):** A collection of markup declarations that describe an XML
document's permissible elements and structure.

**Cascading Style Sheet (CSS):** A style sheet that defines the appearance of an XML or HTML
document directly on the client.

**Content Model:** The expression specifying what elements and data are allowed within an element in
XML.

**Root Element:** The element that contains all other elements in an XML document.

**Well-formed XML:** An XML document is well-formed if there is one root element, and all its child
elements are nested within each other properly.

**Valid XML:** XML that meets the constraints defined by its Document Type Declaration or Schema.

**Namespace:** A collection of names, identified by a URI reference, which are used in XML documents
as element types and attribute names.

**RELAX NG:** A schema language for XML that is simpler and more flexible than XML Schema, offering
a straightforward way to define the structure of XML documents.

**Schematron:** A rule-based schema language for XML that uses XPath expressions to define
constraints on the content of XML documents.

**XPath:** A language for finding information in an XML document, used to navigate through elements
and attributes.

**XSD (XML Schema Definition):** A language used to define the structure, content, and semantics of
XML documents.

**Abstract Data Model:** The conceptual model used by XML Schema to define schemas and their
component parts.

**Simple Type:** A data type in XML Schema that constrains the content of elements and attributes to
contain only text, without any child elements.

**Complex Type:** A data type in XML Schema that can contain elements, attributes, or a mix of both,
allowing for the definition of complex data structures.

**Substitution Group:** A mechanism in XML Schema that allows one element to be substituted for
another in instance documents, enabling polymorphism.

**Assertion:** A condition defined in XML Schema 1.1 that must be true for an XML document to be
valid according to the schema, using XPath expressions for complex constraints.

These terms provide a foundational understanding of XML schemas and their role in defining and
validating the structure and content of XML documents across various applications and industries.

## Frequently Asked Questions

1. **What is an XML Schema?**

    - An XML Schema defines the structure, content, and semantics of XML documents. It specifies
      what elements and attributes are allowed, their data types, and their relationships.

2. **What is the difference between XML Schema (XSD) and XDR schema?**

    - XML Schema (XSD) is the W3C standard for defining XML document structure, while XDR (XML-Data
      Reduced) is an interim schema language developed by Microsoft. XSD is more widely supported
      and offers more features.

3. **What is the purpose of an XML schema?**

    - The purpose is to define the legal building blocks of an XML document, including elements,
      attributes, their data types, and the order in which they appear, to ensure XML documents
      conform to a predefined structure.

4. **How does XML handle data types?**

    - XML supports data types through XML Schema, allowing elements and attributes to contain
      specific types of data like integer, string, date, etc., and validates this data against the
      schema.

5. **How is XML used in web services?**

    - XML is used to encode data for web services, facilitating interoperability between different
      systems by providing a standard format for data exchange.

6. **What is the difference between a well-formed and a valid XML document?**

    - A well-formed XML document follows XML syntax rules, while a valid XML document adheres to the
      structure and constraints defined by its associated XML Schema.

7. **What are XML namespaces?**

    - XML namespaces prevent naming conflicts by distinguishing elements and attributes that may
      have the same name but belong to different vocabularies. They are declared using the `xmlns`
      attribute.

8. **What is XSLT in XML?**

    - XSLT (XSL Transformations) is a language for transforming XML documents into other formats
      like HTML, PDF, or other XML documents, using an XSLT processor.

9. **Why Learn XML Schema?**

    - Learning XML Schema is crucial for defining and validating the structure and content of XML
      documents, especially in environments where data interchange standards are critical.

10. **What is the future of XML?**

    - XML remains vital for data interchange, especially in enterprise and B2B contexts. Its role is
      likely to continue as a specialized tool for certain types of data interchange.

11. **What is an XML parser?**

    - An XML parser is a tool that reads XML documents and provides an interface for programs to
      access their content and structure, ensuring they are well-formed.

12. **How is XML used in databases?**

    - XML is used in databases to store and transport complex data structures, supported as a data
      type in many databases, allowing storage of XML documents in database columns.

13. **What is the difference between XML Schema (XSD) and DTD?**

    - XML Schema (XSD) provides a more powerful and flexible way to define the structure and data
      types of XML documents compared to DTDs, including support for namespaces and data typing.

14. **Can XML Schemas be combined from multiple languages?**

    - Yes, schemas from different languages like XSD, RELAX NG, and Schematron can be combined to
      leverage the strengths of each for comprehensive validation.

15. **How do XML Schemas support data types?**

    - XML Schemas support a wide range of data types, allowing for precise definition of element and
      attribute content types, including numeric types, strings, dates, and custom types.

16. **What is the XML Schema Object Model (SOM)?**

    - SOM is a set of classes in the `System.Xml.Schema` namespace that allows programmatic
      creation, reading, and manipulation of XML Schema definitions.

17. **What is the role of `XmlSchemaSet`?**

    - `XmlSchemaSet` is a class that acts as a cache for storing and validating XSD schemas,
      providing efficient schema compilation and validation.

18. **How can XML Schemas secure data communication?**

    - By defining precise expectations for data content and structure, XML Schemas ensure mutual
      understanding between data sender and receiver, securing data communication.

19. **What is the significance of well-formedness in XML?**

    - Well-formedness ensures that an XML document adheres to the basic syntax rules of XML, which
      is a prerequisite for further validation against a schema.

20. **What advancements does XML Schema 1.1 offer over 1.0?**
    - XML Schema 1.1 introduces features like assertions for complex constraints, conditional type
      assignment, enhanced support for versioning, and co-occurrence constraints.

## Timeline

**Late 1990s:** XML (eXtensible Markup Language) is developed as a simplified subset of SGML
(Standard Generalized Markup Language) to make electronic publishing easier and to solve universal
data interchange issues.

**1999:** The World Wide Web Consortium (W3C) begins work on the XML Schema specification, aiming to
provide a means to define and enforce structured content in XML documents.

**May 2, 2001:** W3C publishes the first version of XML Schema (XML Schema 1.0) as a Recommendation,
addressing primitive data typing and structural constraints.

**2006:** The XML Schema Working Group is chartered by W3C to maintain and revise the XML Schema
specifications, with a focus on publishing version 1.1 of the XML Schema Recommendation.

**August 2006:** XML Schema Working Group holds a face-to-face meeting hosted by Microsoft in
Washington, USA, to discuss the development of XML Schema 1.1.

**November 2006:** XML Schema 1.1 Structures reaches Last Call status, indicating it is nearing
completion.

**April 2007:** XML Schema 1.1 Datatypes and Structures enter the Candidate Recommendation (CR)
phase.

**August 2007:** XML Schema 1.1 Datatypes and Structures progress to the Proposed Recommendation
(PR) phase.

**October 2007:** XML Schema 1.1 Datatypes and Structures are officially published as W3C
Recommendations.

**2008:** The NoSQL wave begins, including big data technologies, marking a shift in database
technologies and indirectly influencing XML and schema technologies.

**2011:** XML Schema 1.1 Parts 1 and 2 (Structures and Datatypes) enter the CR phase again in April,
followed by the PR phase in June, and finally become W3C Recommendations in August.

**2011:** XML Schema: Component Designators moves to Proposed Recommendation in May and becomes a
W3C Recommendation in July.

**2011-2013:** The XML Schema Working Group focuses on moving XML Schema 1.1 toward Recommendation
Status and maintaining older versions of XSD, including XML Schema 1.0.

**2012:** XML continues to evolve and adapt, with ongoing discussions about its future and
applications.

**2013:** The XML Schema Working Group's charter is expected to end in January, marking a
significant milestone in the development and maintenance of XML Schema standards.

**2017:** ECMA Standard 404 for JSON is published, reflecting the growing importance of JSON as an
alternative to XML for data interchange.

**Ongoing:** The XML Schema Working Group continues to address errata, develop interoperability test
suites, and publish primers and notes to support the XML Schema specifications.

**Ongoing:** The evolution of database technologies, including the graph wave and NoSQL wave,
influences the development and application of XML schemas in various domains.

**Ongoing:** The W3C and other organizations continue to explore and develop standards for data
modeling, schema languages, and interoperability to address the needs of modern web and data
applications.

**Ongoing:** The XML Schema Working Group actively cooperates with other W3C Working Groups and
external organizations to ensure XML Schema meets the evolving needs of the industry and remains a
vital technology for data interchange and validation.

This timeline highlights the key milestones in the development and evolution of XML Schema,
reflecting its importance in standardizing and validating the structure and content of XML documents
across various applications and industries.
