# Spatial-Reference-System
A spatial reference system (SRS) or coordinate reference system (CRS) is a coordinate-based local, regional or global system used to locate geographical entities. A spatial reference system defines a specific map projection, as well as transformations between different spatial reference systems. Spatial reference systems are defined by the OGC's Simple Feature Access using well-known text representation of coordinate reference systems, and support has been implemented by several standards-based geographic information systems. Spatial reference systems can be referred to using a SRID integer, including EPSG codes defined by the International Association of Oil and Gas Producers. It is specified in ISO 19111:2007 Geographic information—Spatial referencing by coordinates, prepared by ISO/TC 211, also published as OGC Abstract Specification, Topic 2: Spatial referencing by coordinate



#Components

In this Abstract Specification, a coordinate reference system shall be composed of one coordinate system and one datum.

A coordinate system is a set of mathematical rules for specifying how coordinates are to be assigned to points, such as: affine, cylindrical, Cartesian, ellipsoidal, linear, polar, spherical, vertical, etc.

A datum is a set of parameters that define the position of the origin, the scale, and the orientation of a coordinate system.
The main subtypes of coordinate reference system are: geodetic, vertical, engineering, and image; additional subtypes are: derived, projected, and compound. 



==Identifiers{{anchor|Identifier}}==
A '''Spatial Reference System Identifier''' ('''SRID''') is a unique value used to unambiguously identify projected, unprojected, and local spatial coordinate system definitions. These coordinate systems form the heart of all [[Geographic information system|GIS]] applications.

Virtually all major spatial vendors have created their own SRID implementation or refer to those of an authority, such as the [[EPSG Geodetic Parameter Dataset]].

SRIDs are the primary key for the [[Open Geospatial Consortium|Open Geospatial Consortium (OGC)]] '''spatial_ref_sys''' metadata table for the [[Simple Features|Simple Features for SQL Specification, Versions 1.1 and 1.2]],  which is defined as follows:
<syntaxhighlight lang=sql>
CREATE TABLE SPATIAL_REF_SYS
(
    SRID      INTEGER   NOT NULL PRIMARY KEY,
    AUTH_NAME CHARACTER VARYING(256),
    AUTH_SRID INTEGER,
    SRTEXT    CHARACTER VARYING(2048)
)
</syntaxhighlight>
In spatially enabled databases (such as [[IBM DB2]], [[IBM Informix]], [[Ingres (database)|Ingres]], [[Microsoft SQL Server]], [[MySQL]], [[Oracle RDBMS]], [[Teradata]], [[PostGIS]], [[SQL Anywhere]] and [[Vertica]]), SRIDs are used to uniquely identify the coordinate systems used to define columns of spatial data or individual spatial objects in a spatial column (depending on the spatial implementation).  SRIDs are typically associated with a [[Well-known text representation of coordinate reference systems|well-known text]] (WKT) string definition of the coordinate system (SRTEXT, above).
Here are two common coordinate systems with their EPSG SRID value followed by their WKT:

UTM, Zone 17N, NAD27 — SRID 2029:
<syntaxhighlight lang="javascript">
PROJCS["NAD27(76) / UTM zone 17N",
    GEOGCS["NAD27(76)",
        DATUM["North_American_Datum_1927_1976",
            SPHEROID["Clarke 1866",6378206.4,294.9786982138982,
                AUTHORITY["EPSG","7008"]],
            AUTHORITY["EPSG","6608"]],
        PRIMEM["Greenwich",0,
            AUTHORITY["EPSG","8901"]],
        UNIT["degree",0.01745329251994328,
            AUTHORITY["EPSG","9122"]],
        AUTHORITY["EPSG","4608"]],
    UNIT["metre",1,
        AUTHORITY["EPSG","9001"]],
    PROJECTION["Transverse_Mercator"],
    PARAMETER["latitude_of_origin",0],
    PARAMETER["central_meridian",-81],
    PARAMETER["scale_factor",0.9996],
    PARAMETER["false_easting",500000],
    PARAMETER["false_northing",0],
    AUTHORITY["EPSG","2029"],
    AXIS["Easting",EAST],
    AXIS["Northing",NORTH]]
</syntaxhighlight>

[[WGS84]] — SRID 4326  
<syntaxhighlight lang=javascript>
GEOGCS["WGS 84",
    DATUM["WGS_1984",
        SPHEROID["WGS 84",6378137,298.257223563,
            AUTHORITY["EPSG","7030"]],
        AUTHORITY["EPSG","6326"]],
    PRIMEM["Greenwich",0,
        AUTHORITY["EPSG","8901"]],
    UNIT["degree",0.01745329251994328,
        AUTHORITY["EPSG","9122"]],
    AUTHORITY["EPSG","4326"]]
</syntaxhighlight>

SRID values associated with spatial data can be used to constrain spatial operations — for instance, spatial operations cannot be performed between spatial objects with differing SRIDs in some systems, or trigger coordinate system transformations between spatial objects in others.

==See also==
*[[Engineering datum]]
*[[Geodesy]]
*[[Georeferencing]]
*[[Geographic coordinate systems]]
*[[Geographic information system]] ([[Geographic information system|GIS]]).
*[[Grid reference]]
*[[List of National Coordinate Reference Systems]]

==References==
{{Reflist}}

==External links==
{{Wikidata property|P3037}}

* [http://spatialreference.org/ spatialreference.org] – A website that defines spatial reference systems, in a variety of formats.
* [http://www.opengeospatial.org/specs/?page=specs OpenGIS Specifications (Standards)]
* [http://www.opengeospatial.org/standards/sfc OpenGIS Simple Features Specification for CORBA (99-054)]
* [http://www.opengeospatial.org/standards/sfo OpenGIS Simple Features Specification for OLE/COM (99-050)]
* [http://www.opengeospatial.org/standards/sfs OpenGIS Simple Features Specification for SQL (99-054, 05-134, 06-104r3)]
* [http://www.gdal.org/ogr/ OGR] — library implementing relevant OGC standards
* [http://www.epsg-registry.org/ EPSG Geodetic Parameter Registry] - search engine for EPSG defined reference systems
* [http://www.epsg.io/ EPSG.io/] - Full text search indexing over 6000 coordinate systems
* [http://www.galdosinc.com/products/indicio-crs-registry Galdos Systems INdicio CRS Registry]

{{OGC}}
{{ISO standards}}

{{DEFAULTSORT:Spatial Referencing System}}
[[Category:Geographic coordinate systems]]
[[Category:Geographic information systems]]
[[Category:Geodesy]]
[[Category:ISO/TC 211]]
[[Category:Open Geospatial Consortium]]
[[Category:GIS file formats]]
