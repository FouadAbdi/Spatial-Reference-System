
# Spatial-Reference-System
A spatial reference system (SRS) or coordinate reference system (CRS) is a coordinate-based local, regional or global system used to locate geographical entities. A spatial reference system defines a specific map projection, as well as transformations between different spatial reference systems. Spatial reference systems are defined by the OGC's Simple Feature Access using well-known text representation of coordinate reference systems, and support has been implemented by several standards-based geographic information systems. Spatial reference systems can be referred to using a SRID integer, including EPSG codes defined by the International Association of Oil and Gas Producers. It is specified in ISO 19111:2007 Geographic information—Spatial referencing by coordinates, prepared by ISO/TC 211, also published as OGC Abstract Specification, Topic 2: Spatial referencing by coordinate



## Components

In this Abstract Specification, a coordinate reference system shall be composed of one coordinate system and one datum.

A coordinate system is a set of mathematical rules for specifying how coordinates are to be assigned to points, such as: affine, cylindrical, Cartesian, ellipsoidal, linear, polar, spherical, vertical, etc.

A datum is a set of parameters that define the position of the origin, the scale, and the orientation of a coordinate system.
The main subtypes of coordinate reference system are: geodetic, vertical, engineering, and image; additional subtypes are: derived, projected, and compound. 



## Identifiers{{anchor|Identifier}}==
A '''Spatial Reference System Identifier''' ('''SRID''') is a unique value used to unambiguously identify projected, unprojected, and local spatial coordinate system definitions. These coordinate systems form the heart of all [[Geographic information system|GIS]] applications.

Virtually all major spatial vendors have created their own SRID implementation or refer to those of an authority, such as the [[EPSG Geodetic Parameter Dataset]].

SRIDs are the primary key for the [Open Geospatial Consortium (OGC)](https://en.wikipedia.org/wiki/Open_Geospatial_Consortium) '''spatial_ref_sys''' metadata table for the [[Simple Features|Simple Features for SQL Specification, Versions 1.1 and 1.2]],  which is defined as follows:

```
CREATE TABLE SPATIAL_REF_SYS
(
    SRID      INTEGER   NOT NULL PRIMARY KEY,
    AUTH_NAME CHARACTER VARYING(256),
    AUTH_SRID INTEGER,
    SRTEXT    CHARACTER VARYING(2048)
)
```
In spatially enabled databases (such as [[IBM DB2]], [[IBM Informix]], [[Ingres (database)|Ingres]], [[Microsoft SQL Server]], [[MySQL]], [[Oracle RDBMS]], [[Teradata]], [[PostGIS]], [[SQL Anywhere]] and [[Vertica]]), SRIDs are used to uniquely identify the coordinate systems used to define columns of spatial data or individual spatial objects in a spatial column (depending on the spatial implementation).  SRIDs are typically associated with a [[Well-known text representation of coordinate reference systems|well-known text]] (WKT) string definition of the coordinate system (SRTEXT, above).
Here are two common coordinate systems with their EPSG SRID value followed by their WKT:

