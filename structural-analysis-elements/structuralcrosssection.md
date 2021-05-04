# StructuralCrossSection

## Cross-section

A cross-section together with material \([StructuralMaterial](structuralmaterial.md#material)\) is a basic property of a 1D member. Various kinds of shapes can be defined, including steel rolled sections, timber specific cross-sections or general geometric sections. Supported shapes of cross-sections are defined in documents Formcodes and Description ID of the profile, in chapter Annexes in this document.

Specification in excel:

| Name of   the column header   | Type of data | Value example or enum definition         | Required value                                                                                                       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|-------------------------------|--------------|------------------------------------------|----------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              Name             |    String    |                    CS1                   |                                                          yes                                                         | Human readable unique name of the Cross-section                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|            Material           |    String    |                   MAT1                   |                                                          yes                                                         | Name reference to the existing StructuralMaterial object. The   general type of cross-section can have more than one materials. Each material   name is separated by a semicolon.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|       Cross-section type      |     Enum     | Parametric Manufactured Compound General |                                                          yes                                                         | Define type of profile library:  General: Serves to define any general shape of the cross-section consisting   of one or more closed polygons including openings.  Shape of the cross-section   (polygons) is defined on separate sheet "CompositeShapeDef"  Parametric: Cross-sections defined by shape and dimensions (parameters).  Manufactured: This option refers to the industrially manufactured cross-sections.  Compound: prepared for compounded section fom more manufactured profiles e.g. for two I-sections. Example of compound cross-section input:  profile =   IPE200 and parameters=10mm (distance between profiles).  All supported shapes of compound section can be found in Annex |
|             Shape             |     Enum     |                 T Section                |                 yes, if Cross-section type =   Parametricyes,  yes, if Cross-section type = Compound                 | This field defines geometrical   shape of the cross-section, is required only if Cross-section type is not   manufactured. Complete list of supported shapes is attached in Supported   shapes of cross-section.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|        Parameters [mm]        |    String    |             50; 80; 500; 450             |                  yes, if Cross-section type = Parametricyes,  yes, if Cross-section type = Compound                  | The parameters property is required only if Cross-section type   is Parametric and it represents dimensions of the cross-section. The format   of the parameters depends on cross-section shape. Each parameter has to be   divided by a semicolon. Complete list of supported parameters is attached in   Annex.                                                                                                                                                                                                                                                                                                                                                                                         |
|            Profile            |    String    |                  HEB180                  | yes, if Cross-section type = Manufacturedyes, if Cross-section   type = Compoundyes, if Cross-section type = General | This field is required only if Cross-section type is   Manufactured or Compound. Defines name of the industrially manufactured   profile in the globally common format (naming).For Cross-section type =   general, name reference to valid CompositeShapeDef object is required in the   cell "Profile"                                                                                                                                                                                                                                                                                                                                                                                                  |
|           Form code           |     Enum     |                     1                    |                                       yes, if Cross-section type = Manufactured                                      | This field is valid only if profile type is Manufactured. It   helps to define hot rolled or cold formed profiles. The shape of the   cross-section is uniquely identified by a so-called Formcode. The   Formcodedefines the shape and in some cases also additional parameters like   distance between bolt holes, unit warping coordinates etc. Complete list of   supported form codes is attached in Formcodes.                                                                                                                                                                                                                                                                                      |
| Description ID of the profile |     Enum     |                     2                    |                                                          no                                                          | This field is valid only if the cross-section type is   Manufactured. The description of the hot rolled and cold formed cross-section   referring to the source of manufacturer. Complete list  is attached in Description ID of the   profile.                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|             A [m2]            |    Double    |                 0,075484                 |                                                          no                                                          | Section area                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|            Iy [m4]            |    Double    |                 0,000641                 |                                                          no                                                          | Moment of inertia about y-axis                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|            Iz [m4]            |    Double    |                 0,013319                 |                                                          no                                                          | Moment of inertia about z-axis                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|            It [m4]            |    Double    |                 0,0000591                |                                                          no                                                          | Torsion moment of inertia                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|             Iw[m6]            |    Double    |                0,00015548                |                                                          no                                                          | Warping constant                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|           Wply [m3]           |    Double    |                 0,029497                 |                                                          no                                                          | Plastic modulus about the y-axis                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|           Wplz [m3]           |    Double    |                 0,029497                 |                                                          no                                                          | Plastic modulus about the z-axis                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|               Id              |    String    |   6bbd256e-0225-4ee5-91e5-c7ef791a33cb   |                                                          no                                                          | Unique attribute designation                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|               Id              |    String    |   6bbd256e-0225-4ee5-91e5-c7ef791a33cb   |                                                          no                                                          | Unique attribute designation                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

## Notes

{% hint style="info" %}
"**Name**" is recommended to set the same as the "**Quality**" of the defined material.
{% endhint %}
