# WAM_XMLExport_AAC_Constituents_V3.xml

## Add Column

## Add Node/Literal

## PyTransforms
#### _ConstituentURI_
From column: _Root / ObjRecord / Constituents / ObjectRelatedConstituent / ConstituentID_
``` python
if getValue("ConstituentType")=="Individual":
    return "constituent/"+getValue("ConstituentID")
else:
    return ""
```

#### _NotInUse1_
From column: _Root / ObjRecord / Constituents / ObjectRelatedConstituent / ConstituentType_
``` python
if getValue("ThesGeographyTerm"):
    return getValue("ConstituentURI")+"/birth"
else:
    return ""
```

#### _NotInUse_
From column: _Root / ObjRecord / Constituents / ObjectRelatedConstituent / ConstituentType_
``` python
if getValue("ThesGeographyTerm"):
    return getValue("BirthURI")+"/location"
else:
    return ""
```

#### _BirthURI_
From column: _Root / ObjRecord / Constituents / ObjectRelatedConstituent / ConstituentGeography / ConstituentGeography / ThesGeographyTerm_
``` python
if getValue("ThesGeographyTerm"):
    return getValue("ConstituentURI")+"/birth"
else:
    return ""
```

#### _BirthLocationURI_
From column: _Root / ObjRecord / Constituents / ObjectRelatedConstituent / ConstituentGeography / ConstituentGeography / ThesGeographyTerm_
``` python
if getValue("ThesGeographyTerm"):
    return getValue("BirthURI")+"/location"
else:
    return ""
```


## Selections
#### _DEFAULT_TEST_
From column: _Root / ObjRecord / Constituents / ObjectRelatedConstituent / ConstituentGeography / ConstituentGeography / ThesGeographyTerm_
<br>Operation: `Union`
``` python
return getValue("ThesGeoType")!='Birth Location'
```


## Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| _BirthLocationURI_ | `uri` | `crm:E53_Place1`|
| _BirthURI_ | `uri` | `crm:E63_Beginning_of_Existence1`|
| _ConstituentURI_ | `uri` | `crm:E39_Actor1`|
| _ThesGeographyTerm_ | `rdfs:label` | `crm:E53_Place1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `crm:E39_Actor1` | `crm:P92i_was_brought_into_existence_by` | `crm:E63_Beginning_of_Existence1`|
| `crm:E63_Beginning_of_Existence1` | `crm:P7_took_place_at` | `crm:E53_Place1`|
