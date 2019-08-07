# Notes

## Dataset

### SDSS website

#### Help
[DR15 Overview](https://www.sdss.org/dr15/data_access/)

[API Reference](http://skyserver.sdss.org/dr15/en/help/docs/api.aspx#imgcutout)

[SQL Documentation](http://skyserver.sdss.org/dr15/en/help/browser/browser.aspx#&&history=description+Frame+U): see view-PhotoObj

#### Get data
[SQL Search](http://skyserver.sdss.org/dr15/en/tools/search/sql.aspx)

[Image Cutout (API Reference)](http://skyserver.sdss.org/dr15/en/help/docs/api.aspx#imgcutout): see Image Cutout examples

[Image List Tool](http://skyserver.sdss.org/dr15/en/tools/chart/sqltoform.aspx): see sample images

### SQL

#### Sample query
* Get detail data `.csv`: [SQL Search](http://skyserver.sdss.org/dr15/en/tools/search/sql.aspx)
```SQL
SELECT TOP 10
   p.objid, p.ra, p.dec,
   p.u, p.g, p.r, p.i, p.z,
   p.run, p.rerun, p.camcol, p.field,
   p.score, p.type, s.class, s.subclass,
   -- p.petroRad_u, p.petroR50_u, p.expRad_u
FROM PhotoObj AS p
JOIN SpecObj AS s ON s.bestobjid = p.objid
WHERE
   p.score > 0.75
   AND p.CLEAN = 1
   AND p.u BETWEEN 16 AND 20
   AND p.g BETWEEN 16 AND 20
ORDER BY p.field
```

* Get sample images: [Image List Tool](http://skyserver.sdss.org/dr15/en/tools/chart/sqltoform.aspx)
```SQL
SELECT TOP 10
   p.objid as "name", p.ra, p.dec
FROM PhotoObj AS p
JOIN SpecObj AS s ON s.bestobjid = p.objid
WHERE
   p.score > 0.75
   AND p.CLEAN = 1
   AND p.u BETWEEN 16 AND 20
   AND p.g BETWEEN 16 AND 20
ORDER BY p.field
```

### Image Cutout

#### Sample query
http://skyserver.sdss.org/dr15/SkyServerWS/ImgCutout/getjpeg?ra=159.81542&dec=-0.65470&width=64&height=64&scale=0.4

*minimum of `width` and `height` is 64px*

#### `HTTP POST` Guide



## Papers
