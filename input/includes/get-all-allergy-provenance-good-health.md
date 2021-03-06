
**Request:**

Get “all allergies” for a patient and all corresponding Provenance records.


    GET [base]/AllergyIntolerance?patient=12345&_revinclude=Provenance:target

**Response:**

A Server returns a search Bundle resource containing all the Allergies for the patient and corresponding Provenance records.


    HTTP/1.1 200 OK
    [other headers]

    {
    "resourceType": "Bundle",
    "id": "c887e62f-6166-419f-8268-b5ecd6c7b901",
    "meta": {
        "lastUpdated": "2019-07-09T18:49:01.235+00:00"
    },
    "type": "searchset",
    "total": 1,
    "link": [
        {
            "relation": "self",
            "url": "http://hapi.fhir.org/baseR4/AllergyIntolerance?patient=Examples&_revinclude=Provenance:target"
        }
    ],
    "entry": [
        {
            "fullUrl": "http://hapi.fhir.org/baseR4/AllergyIntolerance/79613",
            "resource": {
                "resourceType": "AllergyIntolerance",
                "id": "79613",
                "meta": {
                    "versionId": "1",
                    "lastUpdated": "2019-07-09T15:26:23.217+00:00",
                    "profile": [
                       "http://hl7.org/fhir/us/core/StructureDefinition/us-core-allergyintolerance"
                    ]
                },
                "clinicalStatus": {
                    "coding": [
                        {
                            "system": "http://terminology.hl7.org/CodeSystem/allergyintolerance-clinical",
                            "code": "active",
                            "display": "Active"
                        }
                    ]
                },
                "verificationStatus": {
                    "coding": [
                        {
                            "system": "http://terminology.hl7.org/CodeSystem/allergyintolerance-verification",
                            "code": "confirmed",
                            "display": "Confirmed"
                        }
                    ]
                },
                "code": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "762952008",
                            "display": "Peanuts"
                        }
                    ],
                    "text": "Peanuts"
                },
                "category": [
                    "medication"
                ],
                "criticality": "high",
                "patient": {
                    "reference": "Patient/example"
                },
                "onsetDateTime": "2018-01",
                "reaction": [
                    {
                        "manifestation": [
                            {
                                "coding": [
                                    {
                                        "system": "http://snomed.info/sct",
                                        "code": "247472004",
                                        "display": "Hives"
                                    }
                                ]
                            }
                        ],
                        "onset": "2018-01"
                    }
                ]
            },
            "search": {
                "mode": "match"
            }
        },
        {
            "fullUrl": "http://hapi.fhir.org/baseR4/Provenance/79614",
            "resource": {
                "resourceType": "Provenance",
                "id": "79614",
                "meta": {
                    "versionId": "1",
                    "lastUpdated": "2019-07-09T15:26:23.217+00:00",
                    "profile": [
                       "http://hl7.org/fhir/us/core/StructureDefinition/us-core-provenance"
                    ]
                },
                "target": [
                     {
                        "reference": "AllergyIntolerance/79613"
                    }
                ],
             "recorded": "2018-02T15:26:23.217+00:00",
             "agent": [
                    {
                        "type": [
                            {
                                "coding": [
                                    {
                                        "system": "http://terminology.hl7.org/CodeSystem/provenance-participant-type",
                                        "code": "author",
                                        "display": "Author"
                                    }
                                ]
                            }
                        ],
                        "who": {
                                "reference": "Practitioner/Dr-Jones-12345"
                        },
                        "onBehalfOf": {
                                "reference": "Organization/good-health-54321"
                        }
                    }
                ]},
            "search": {
                "mode": "include"
            }
        }
    ]
}
