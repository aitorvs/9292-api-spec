# Journeys

	GET https://api.9292.nl/0.1/journeys

## Abstract
Met de `journeys`-resource kun je een reis plannen.

## Parameters

| Naam | Omschrijving |
|-----:|:-------------|
| **before** | Bevat `1`. |
| **sequence** | Bevat `1`. |
| **byBus** | Bevat een `boolean` die aangeeft of in de reis gebruik gemaakt mag worden van een bus. |
| **byFerry** | Bevat een `boolean` die aangeeft of in de reis gebruik gemaakt mag worden van een veerboot. |
| **bySubway** | Bevat een `boolean` die aangeeft of in de reis gebruik gemaakt mag worden van een metro. |
| **byTram** | Bevat een `boolean` die aangeeft of in de reis gebruik gemaakt mag worden van een tram. |
| **byTrain** | Bevat een `boolean` die aangeeft of in de reis gebruik gemaakt mag worden van een trein. |
| **lang** | Bevat "nl-NL" in alle gevallen. Zelfs als de telefoon eigenlijk op Engels is ingesteld. |
| **from** | Bevat het `location id` van het vertrekpunt. |
| **dateTime** | Bevat de vertrek/aankomst-datum (incl. tijd) in het formaat: `yyyy-MM-ddTHHmm`. |
| **searchType** | Bevat een `searchType` (zie `objects.md`) die aangeeft of `dateTime` een vertrek- of een aankomst-datum bevat. |
| **interchangeTime** | Bevat `standard`. |
| **after** | Bevat `5`. |
| **to** | Bevat het `location id` van de bestemming. |
| **realtime** | `boolean` to receive real-time info about delays, cancelations and whatnot |

## Response

| Naam | Omschrijving |
|-----:|:-------------|
| **journeys** | Bevat een array van `journey` objecten. |
| **earlier** | Bevat een pad naar de `journeys`-resource die eerdere reismogelijkheden retourneert. |
| **later** | Bevat een pad naar de `journeys`-resource die latere reismogelijkheden retourneert. |
| **disturbances** | Bevat een array van `disturbance` objecten. |
| **serviceMessages** | Onbekend. |
| **nearbyAddresses** | Onbekend. |

## Voorbeeld

### Request

	GET /0.1/journeys?before=1&sequence=1&byFerry=true&bySubway=true&byBus=true&byTram=true&byTrain=true&lang=nl-NL&from=station-amsterdam-centraal&dateTime=2013-01-21T1754&searchType=departure&interchangeTime=standard&after=5&to=station-eindhoven HTTP/1.1
	Host: api.9292.nl

### Response

	{
	  "journeys": [
		{
		  "id": "fromRef=station-amsterdam-centraal&toRef=station-eindhoven&searchType=departure&dateTime=2013-01-21T17:53&interchangeTime=standard&sequence=1&modes=train:true,bus:true,subway:true,tram:true,ferry:true",
		  "ludMessages": [
			{
			  "text": " Deze reis kan via een ongebruikelijke route verlopen door tijdelijke wijzigingen in verband met bijzondere omstandigheden.",
			  "url": null
			}
		  ],
		  "fasterJourneyId": null,
		  "departure": "2013-01-21T17:53",
		  "arrival": "2013-01-21T19:14",
		  "numberOfChanges": 1,
		  "legs": [
			{
			  "type": "scheduled",
			  "mode": {
				"type": "train",
				"name": "Intercity"
			  },
			  "destination": "Nijmegen",
			  "operator": {
				"type": "ns",
				"name": "NS"
			  },
			  "service": "3065",
			  "attributes": [],
			  "disturbancePlannerIds": [],
			  "serviceMessageIds": [],
			  "stops": [
				{
				  "arrival": "2013-01-21T17:48",
				  "departure": "2013-01-21T17:53",
				  "platform": "5",
				  "location": {
					"id": "station-amsterdam-centraal",
					"type": "station",
					"stationId": "asd",
					"stationType": "Station",
					"name": "Amsterdam Centraal",
					"place": {
					  "name": "Amsterdam",
					  "regionCode": "NH",
					  "regionName": "Noord-Holland",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 52.378706,
					  "long": 4.900489
					},
					"urls": {
					  "nl-NL": "/station-amsterdam-centraal",
					  "en-GB": "/en/station-amsterdam-centraal"
					}
				  },
				  "fallbackName": null
				},
				{
				  "arrival": "2013-01-21T18:00",
				  "departure": "2013-01-21T18:00",
				  "platform": "4",
				  "location": {
					"id": "station-amsterdam-amstel",
					"type": "station",
					"stationId": "asa",
					"stationType": "Station",
					"name": "Amsterdam Amstel",
					"place": {
					  "name": "Amsterdam",
					  "regionCode": "NH",
					  "regionName": "Noord-Holland",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 52.346689,
					  "long": 4.917453
					},
					"urls": {
					  "nl-NL": "/station-amsterdam-amstel",
					  "en-GB": "/en/station-amsterdam-amstel"
					}
				  },
				  "fallbackName": null
				},
				{
				  "arrival": "2013-01-21T18:20",
				  "departure": "2013-01-21T18:23",
				  "platform": "14",
				  "location": {
					"id": "station-utrecht-centraal",
					"type": "station",
					"stationId": "ut",
					"stationType": "Station",
					"name": "Utrecht Centraal",
					"place": {
					  "name": "Utrecht",
					  "regionCode": "UT",
					  "regionName": "Utrecht",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 52.089597,
					  "long": 5.110411
					},
					"urls": {
					  "nl-NL": "/station-utrecht-centraal",
					  "en-GB": "/en/station-utrecht-centraal"
					}
				  },
				  "fallbackName": null
				}
			  ]
			},
			{
			  "type": "scheduled",
			  "mode": {
				"type": "train",
				"name": "Intercity"
			  },
			  "destination": "Heerlen",
			  "operator": {
				"type": "ns",
				"name": "NS"
			  },
			  "service": "3565",
			  "attributes": [],
			  "disturbancePlannerIds": [],
			  "serviceMessageIds": [],
			  "stops": [
				{
				  "arrival": "2013-01-21T18:17",
				  "departure": "2013-01-21T18:23",
				  "platform": "15",
				  "location": {
					"id": "station-utrecht-centraal",
					"type": "station",
					"stationId": "ut",
					"stationType": "Station",
					"name": "Utrecht Centraal",
					"place": {
					  "name": "Utrecht",
					  "regionCode": "UT",
					  "regionName": "Utrecht",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 52.089597,
					  "long": 5.110411
					},
					"urls": {
					  "nl-NL": "/station-utrecht-centraal",
					  "en-GB": "/en/station-utrecht-centraal"
					}
				  },
				  "fallbackName": null
				},
				{
				  "arrival": "2013-01-21T18:53",
				  "departure": "2013-01-21T18:54",
				  "platform": "4b",
				  "location": {
					"id": "station-s-hertogenbosch",
					"type": "station",
					"stationId": "ht",
					"stationType": "Station",
					"name": "s-Hertogenbosch",
					"place": {
					  "name": "s Hertogenbosch",
					  "regionCode": "NB",
					  "regionName": "Noord-Brabant",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 51.690625,
					  "long": 5.293648
					},
					"urls": {
					  "nl-NL": "/station-s-hertogenbosch",
					  "en-GB": "/en/station-s-hertogenbosch"
					}
				  },
				  "fallbackName": null
				},
				{
				  "arrival": "2013-01-21T19:14",
				  "departure": "2013-01-21T19:16",
				  "platform": "1",
				  "location": {
					"id": "station-eindhoven",
					"type": "station",
					"stationId": "ehv",
					"stationType": "Station",
					"name": "Eindhoven",
					"place": {
					  "name": "Eindhoven",
					  "regionCode": "NB",
					  "regionName": "Noord-Brabant",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 51.442882,
					  "long": 5.479704
					},
					"urls": {
					  "nl-NL": "/station-eindhoven",
					  "en-GB": "/en/station-eindhoven"
					}
				  },
				  "fallbackName": null
				}
			  ]
			}
		  ],
		  "fareInfo": {
			"complete": true,
			"fullPriceCents": 1790,
			"reducedPriceCents": 1070,
			"legs": [
			  {
				"from": {
				  "id": "station-amsterdam-centraal",
				  "type": "station",
				  "stationId": "asd",
				  "stationType": "Station",
				  "name": "Amsterdam Centraal",
				  "place": {
					"name": "Amsterdam",
					"regionCode": "NH",
					"regionName": "Noord-Holland",
					"showRegion": false,
					"countryCode": "NL",
					"countryName": "Nederland",
					"showCountry": false
				  },
				  "latLong": {
					"lat": 52.378706,
					"long": 4.900489
				  },
				  "urls": {
					"nl-NL": "/station-amsterdam-centraal",
					"en-GB": "/en/station-amsterdam-centraal"
				  }
				},
				"to": {
				  "id": "station-eindhoven",
				  "type": "station",
				  "stationId": "ehv",
				  "stationType": "Station",
				  "name": "Eindhoven",
				  "place": {
					"name": "Eindhoven",
					"regionCode": "NB",
					"regionName": "Noord-Brabant",
					"showRegion": false,
					"countryCode": "NL",
					"countryName": "Nederland",
					"showCountry": false
				  },
				  "latLong": {
					"lat": 51.442882,
					"long": 5.479704
				  },
				  "urls": {
					"nl-NL": "/station-eindhoven",
					"en-GB": "/en/station-eindhoven"
				  }
				},
				"locationsString": "Amsterdam - Eindhoven",
				"modeTypeString": "Trein",
				"operatorString": "NS",
				"fares": [
				  {
					"class": "second",
					"reduced": false,
					"eurocents": 1790
				  },
				  {
					"class": "second",
					"reduced": true,
					"eurocents": 1070
				  },
				  {
					"class": "first",
					"reduced": false,
					"eurocents": 3040
				  },
				  {
					"class": "first",
					"reduced": true,
					"eurocents": 1820
				  }
				]
			  }
			]
		  }
		},
		{
		  "id": "fromRef=station-amsterdam-centraal&toRef=station-eindhoven&searchType=departure&dateTime=2013-01-21T18:08&interchangeTime=standard&sequence=1&modes=train:true,bus:true,subway:true,tram:true,ferry:true",
		  "ludMessages": [],
		  "fasterJourneyId": null,
		  "departure": "2013-01-21T18:08",
		  "arrival": "2013-01-21T19:29",
		  "numberOfChanges": 0,
		  "legs": [
			{
			  "type": "scheduled",
			  "mode": {
				"type": "train",
				"name": "Intercity"
			  },
			  "destination": "Maastricht",
			  "operator": {
				"type": "ns",
				"name": "NS"
			  },
			  "service": "867",
			  "attributes": [],
			  "disturbancePlannerIds": [],
			  "serviceMessageIds": [],
			  "stops": [
				{
				  "arrival": "2013-01-21T18:04",
				  "departure": "2013-01-21T18:08",
				  "platform": "5",
				  "location": {
					"id": "station-amsterdam-centraal",
					"type": "station",
					"stationId": "asd",
					"stationType": "Station",
					"name": "Amsterdam Centraal",
					"place": {
					  "name": "Amsterdam",
					  "regionCode": "NH",
					  "regionName": "Noord-Holland",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 52.378706,
					  "long": 4.900489
					},
					"urls": {
					  "nl-NL": "/station-amsterdam-centraal",
					  "en-GB": "/en/station-amsterdam-centraal"
					}
				  },
				  "fallbackName": null
				},
				{
				  "arrival": "2013-01-21T18:15",
				  "departure": "2013-01-21T18:15",
				  "platform": "4",
				  "location": {
					"id": "station-amsterdam-amstel",
					"type": "station",
					"stationId": "asa",
					"stationType": "Station",
					"name": "Amsterdam Amstel",
					"place": {
					  "name": "Amsterdam",
					  "regionCode": "NH",
					  "regionName": "Noord-Holland",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 52.346689,
					  "long": 4.917453
					},
					"urls": {
					  "nl-NL": "/station-amsterdam-amstel",
					  "en-GB": "/en/station-amsterdam-amstel"
					}
				  },
				  "fallbackName": null
				},
				{
				  "arrival": "2013-01-21T18:35",
				  "departure": "2013-01-21T18:38",
				  "platform": "15",
				  "location": {
					"id": "station-utrecht-centraal",
					"type": "station",
					"stationId": "ut",
					"stationType": "Station",
					"name": "Utrecht Centraal",
					"place": {
					  "name": "Utrecht",
					  "regionCode": "UT",
					  "regionName": "Utrecht",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 52.089597,
					  "long": 5.110411
					},
					"urls": {
					  "nl-NL": "/station-utrecht-centraal",
					  "en-GB": "/en/station-utrecht-centraal"
					}
				  },
				  "fallbackName": null
				},
				{
				  "arrival": "2013-01-21T19:07",
				  "departure": "2013-01-21T19:09",
				  "platform": "4b",
				  "location": {
					"id": "station-s-hertogenbosch",
					"type": "station",
					"stationId": "ht",
					"stationType": "Station",
					"name": "s-Hertogenbosch",
					"place": {
					  "name": "s Hertogenbosch",
					  "regionCode": "NB",
					  "regionName": "Noord-Brabant",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 51.690625,
					  "long": 5.293648
					},
					"urls": {
					  "nl-NL": "/station-s-hertogenbosch",
					  "en-GB": "/en/station-s-hertogenbosch"
					}
				  },
				  "fallbackName": null
				},
				{
				  "arrival": "2013-01-21T19:29",
				  "departure": "2013-01-21T19:32",
				  "platform": "1",
				  "location": {
					"id": "station-eindhoven",
					"type": "station",
					"stationId": "ehv",
					"stationType": "Station",
					"name": "Eindhoven",
					"place": {
					  "name": "Eindhoven",
					  "regionCode": "NB",
					  "regionName": "Noord-Brabant",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 51.442882,
					  "long": 5.479704
					},
					"urls": {
					  "nl-NL": "/station-eindhoven",
					  "en-GB": "/en/station-eindhoven"
					}
				  },
				  "fallbackName": null
				}
			  ]
			}
		  ],
		  "fareInfo": {
			"complete": true,
			"fullPriceCents": 1790,
			"reducedPriceCents": 1070,
			"legs": [
			  {
				"from": {
				  "id": "station-amsterdam-centraal",
				  "type": "station",
				  "stationId": "asd",
				  "stationType": "Station",
				  "name": "Amsterdam Centraal",
				  "place": {
					"name": "Amsterdam",
					"regionCode": "NH",
					"regionName": "Noord-Holland",
					"showRegion": false,
					"countryCode": "NL",
					"countryName": "Nederland",
					"showCountry": false
				  },
				  "latLong": {
					"lat": 52.378706,
					"long": 4.900489
				  },
				  "urls": {
					"nl-NL": "/station-amsterdam-centraal",
					"en-GB": "/en/station-amsterdam-centraal"
				  }
				},
				"to": {
				  "id": "station-eindhoven",
				  "type": "station",
				  "stationId": "ehv",
				  "stationType": "Station",
				  "name": "Eindhoven",
				  "place": {
					"name": "Eindhoven",
					"regionCode": "NB",
					"regionName": "Noord-Brabant",
					"showRegion": false,
					"countryCode": "NL",
					"countryName": "Nederland",
					"showCountry": false
				  },
				  "latLong": {
					"lat": 51.442882,
					"long": 5.479704
				  },
				  "urls": {
					"nl-NL": "/station-eindhoven",
					"en-GB": "/en/station-eindhoven"
				  }
				},
				"locationsString": "Amsterdam - Eindhoven",
				"modeTypeString": "Trein",
				"operatorString": "NS",
				"fares": [
				  {
					"class": "second",
					"reduced": false,
					"eurocents": 1790
				  },
				  {
					"class": "second",
					"reduced": true,
					"eurocents": 1070
				  },
				  {
					"class": "first",
					"reduced": false,
					"eurocents": 3040
				  },
				  {
					"class": "first",
					"reduced": true,
					"eurocents": 1820
				  }
				]
			  }
			]
		  }
		},
		{
		  "id": "fromRef=station-amsterdam-centraal&toRef=station-eindhoven&searchType=departure&dateTime=2013-01-21T18:23&interchangeTime=standard&sequence=1&modes=train:true,bus:true,subway:true,tram:true,ferry:true",
		  "ludMessages": [],
		  "fasterJourneyId": null,
		  "departure": "2013-01-21T18:23",
		  "arrival": "2013-01-21T19:44",
		  "numberOfChanges": 1,
		  "legs": [
			{
			  "type": "scheduled",
			  "mode": {
				"type": "train",
				"name": "Intercity"
			  },
			  "destination": "Nijmegen",
			  "operator": {
				"type": "ns",
				"name": "NS"
			  },
			  "service": "3067",
			  "attributes": [],
			  "disturbancePlannerIds": [],
			  "serviceMessageIds": [],
			  "stops": [
				{
				  "arrival": "2013-01-21T18:18",
				  "departure": "2013-01-21T18:23",
				  "platform": "5",
				  "location": {
					"id": "station-amsterdam-centraal",
					"type": "station",
					"stationId": "asd",
					"stationType": "Station",
					"name": "Amsterdam Centraal",
					"place": {
					  "name": "Amsterdam",
					  "regionCode": "NH",
					  "regionName": "Noord-Holland",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 52.378706,
					  "long": 4.900489
					},
					"urls": {
					  "nl-NL": "/station-amsterdam-centraal",
					  "en-GB": "/en/station-amsterdam-centraal"
					}
				  },
				  "fallbackName": null
				},
				{
				  "arrival": "2013-01-21T18:30",
				  "departure": "2013-01-21T18:30",
				  "platform": "4",
				  "location": {
					"id": "station-amsterdam-amstel",
					"type": "station",
					"stationId": "asa",
					"stationType": "Station",
					"name": "Amsterdam Amstel",
					"place": {
					  "name": "Amsterdam",
					  "regionCode": "NH",
					  "regionName": "Noord-Holland",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 52.346689,
					  "long": 4.917453
					},
					"urls": {
					  "nl-NL": "/station-amsterdam-amstel",
					  "en-GB": "/en/station-amsterdam-amstel"
					}
				  },
				  "fallbackName": null
				},
				{
				  "arrival": "2013-01-21T18:50",
				  "departure": "2013-01-21T18:53",
				  "platform": "14",
				  "location": {
					"id": "station-utrecht-centraal",
					"type": "station",
					"stationId": "ut",
					"stationType": "Station",
					"name": "Utrecht Centraal",
					"place": {
					  "name": "Utrecht",
					  "regionCode": "UT",
					  "regionName": "Utrecht",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 52.089597,
					  "long": 5.110411
					},
					"urls": {
					  "nl-NL": "/station-utrecht-centraal",
					  "en-GB": "/en/station-utrecht-centraal"
					}
				  },
				  "fallbackName": null
				}
			  ]
			},
			{
			  "type": "scheduled",
			  "mode": {
				"type": "train",
				"name": "Intercity"
			  },
			  "destination": "Eindhoven",
			  "operator": {
				"type": "ns",
				"name": "NS"
			  },
			  "service": "3567",
			  "attributes": [],
			  "disturbancePlannerIds": [],
			  "serviceMessageIds": [],
			  "stops": [
				{
				  "arrival": "2013-01-21T18:47",
				  "departure": "2013-01-21T18:53",
				  "platform": "15",
				  "location": {
					"id": "station-utrecht-centraal",
					"type": "station",
					"stationId": "ut",
					"stationType": "Station",
					"name": "Utrecht Centraal",
					"place": {
					  "name": "Utrecht",
					  "regionCode": "UT",
					  "regionName": "Utrecht",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 52.089597,
					  "long": 5.110411
					},
					"urls": {
					  "nl-NL": "/station-utrecht-centraal",
					  "en-GB": "/en/station-utrecht-centraal"
					}
				  },
				  "fallbackName": null
				},
				{
				  "arrival": "2013-01-21T19:23",
				  "departure": "2013-01-21T19:24",
				  "platform": "4b",
				  "location": {
					"id": "station-s-hertogenbosch",
					"type": "station",
					"stationId": "ht",
					"stationType": "Station",
					"name": "s-Hertogenbosch",
					"place": {
					  "name": "s Hertogenbosch",
					  "regionCode": "NB",
					  "regionName": "Noord-Brabant",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 51.690625,
					  "long": 5.293648
					},
					"urls": {
					  "nl-NL": "/station-s-hertogenbosch",
					  "en-GB": "/en/station-s-hertogenbosch"
					}
				  },
				  "fallbackName": null
				},
				{
				  "arrival": "2013-01-21T19:44",
				  "departure": null,
				  "platform": "1",
				  "location": {
					"id": "station-eindhoven",
					"type": "station",
					"stationId": "ehv",
					"stationType": "Station",
					"name": "Eindhoven",
					"place": {
					  "name": "Eindhoven",
					  "regionCode": "NB",
					  "regionName": "Noord-Brabant",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 51.442882,
					  "long": 5.479704
					},
					"urls": {
					  "nl-NL": "/station-eindhoven",
					  "en-GB": "/en/station-eindhoven"
					}
				  },
				  "fallbackName": null
				}
			  ]
			}
		  ],
		  "fareInfo": {
			"complete": true,
			"fullPriceCents": 1790,
			"reducedPriceCents": 1070,
			"legs": [
			  {
				"from": {
				  "id": "station-amsterdam-centraal",
				  "type": "station",
				  "stationId": "asd",
				  "stationType": "Station",
				  "name": "Amsterdam Centraal",
				  "place": {
					"name": "Amsterdam",
					"regionCode": "NH",
					"regionName": "Noord-Holland",
					"showRegion": false,
					"countryCode": "NL",
					"countryName": "Nederland",
					"showCountry": false
				  },
				  "latLong": {
					"lat": 52.378706,
					"long": 4.900489
				  },
				  "urls": {
					"nl-NL": "/station-amsterdam-centraal",
					"en-GB": "/en/station-amsterdam-centraal"
				  }
				},
				"to": {
				  "id": "station-eindhoven",
				  "type": "station",
				  "stationId": "ehv",
				  "stationType": "Station",
				  "name": "Eindhoven",
				  "place": {
					"name": "Eindhoven",
					"regionCode": "NB",
					"regionName": "Noord-Brabant",
					"showRegion": false,
					"countryCode": "NL",
					"countryName": "Nederland",
					"showCountry": false
				  },
				  "latLong": {
					"lat": 51.442882,
					"long": 5.479704
				  },
				  "urls": {
					"nl-NL": "/station-eindhoven",
					"en-GB": "/en/station-eindhoven"
				  }
				},
				"locationsString": "Amsterdam - Eindhoven",
				"modeTypeString": "Trein",
				"operatorString": "NS",
				"fares": [
				  {
					"class": "second",
					"reduced": false,
					"eurocents": 1790
				  },
				  {
					"class": "second",
					"reduced": true,
					"eurocents": 1070
				  },
				  {
					"class": "first",
					"reduced": false,
					"eurocents": 3040
				  },
				  {
					"class": "first",
					"reduced": true,
					"eurocents": 1820
				  }
				]
			  }
			]
		  }
		},
		{
		  "id": "fromRef=station-amsterdam-centraal&toRef=station-eindhoven&searchType=departure&dateTime=2013-01-21T18:53&interchangeTime=standard&sequence=1&modes=train:true,bus:true,subway:true,tram:true,ferry:true",
		  "ludMessages": [
			{
			  "text": " Deze reis kan via een ongebruikelijke route verlopen door tijdelijke wijzigingen in verband met bijzondere omstandigheden.",
			  "url": null
			}
		  ],
		  "fasterJourneyId": null,
		  "departure": "2013-01-21T18:53",
		  "arrival": "2013-01-21T20:14",
		  "numberOfChanges": 1,
		  "legs": [
			{
			  "type": "scheduled",
			  "mode": {
				"type": "train",
				"name": "Intercity"
			  },
			  "destination": "Nijmegen",
			  "operator": {
				"type": "ns",
				"name": "NS"
			  },
			  "service": "3069",
			  "attributes": [],
			  "disturbancePlannerIds": [],
			  "serviceMessageIds": [],
			  "stops": [
				{
				  "arrival": "2013-01-21T18:48",
				  "departure": "2013-01-21T18:53",
				  "platform": "4a",
				  "location": {
					"id": "station-amsterdam-centraal",
					"type": "station",
					"stationId": "asd",
					"stationType": "Station",
					"name": "Amsterdam Centraal",
					"place": {
					  "name": "Amsterdam",
					  "regionCode": "NH",
					  "regionName": "Noord-Holland",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 52.378706,
					  "long": 4.900489
					},
					"urls": {
					  "nl-NL": "/station-amsterdam-centraal",
					  "en-GB": "/en/station-amsterdam-centraal"
					}
				  },
				  "fallbackName": null
				},
				{
				  "arrival": "2013-01-21T19:00",
				  "departure": "2013-01-21T19:00",
				  "platform": "4",
				  "location": {
					"id": "station-amsterdam-amstel",
					"type": "station",
					"stationId": "asa",
					"stationType": "Station",
					"name": "Amsterdam Amstel",
					"place": {
					  "name": "Amsterdam",
					  "regionCode": "NH",
					  "regionName": "Noord-Holland",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 52.346689,
					  "long": 4.917453
					},
					"urls": {
					  "nl-NL": "/station-amsterdam-amstel",
					  "en-GB": "/en/station-amsterdam-amstel"
					}
				  },
				  "fallbackName": null
				},
				{
				  "arrival": "2013-01-21T19:20",
				  "departure": "2013-01-21T19:23",
				  "platform": "14b",
				  "location": {
					"id": "station-utrecht-centraal",
					"type": "station",
					"stationId": "ut",
					"stationType": "Station",
					"name": "Utrecht Centraal",
					"place": {
					  "name": "Utrecht",
					  "regionCode": "UT",
					  "regionName": "Utrecht",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 52.089597,
					  "long": 5.110411
					},
					"urls": {
					  "nl-NL": "/station-utrecht-centraal",
					  "en-GB": "/en/station-utrecht-centraal"
					}
				  },
				  "fallbackName": null
				}
			  ]
			},
			{
			  "type": "scheduled",
			  "mode": {
				"type": "train",
				"name": "Intercity"
			  },
			  "destination": "Eindhoven",
			  "operator": {
				"type": "ns",
				"name": "NS"
			  },
			  "service": "3569",
			  "attributes": [],
			  "disturbancePlannerIds": [],
			  "serviceMessageIds": [],
			  "stops": [
				{
				  "arrival": "2013-01-21T19:17",
				  "departure": "2013-01-21T19:23",
				  "platform": "15",
				  "location": {
					"id": "station-utrecht-centraal",
					"type": "station",
					"stationId": "ut",
					"stationType": "Station",
					"name": "Utrecht Centraal",
					"place": {
					  "name": "Utrecht",
					  "regionCode": "UT",
					  "regionName": "Utrecht",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 52.089597,
					  "long": 5.110411
					},
					"urls": {
					  "nl-NL": "/station-utrecht-centraal",
					  "en-GB": "/en/station-utrecht-centraal"
					}
				  },
				  "fallbackName": null
				},
				{
				  "arrival": "2013-01-21T19:53",
				  "departure": "2013-01-21T19:54",
				  "platform": "4b",
				  "location": {
					"id": "station-s-hertogenbosch",
					"type": "station",
					"stationId": "ht",
					"stationType": "Station",
					"name": "s-Hertogenbosch",
					"place": {
					  "name": "s Hertogenbosch",
					  "regionCode": "NB",
					  "regionName": "Noord-Brabant",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 51.690625,
					  "long": 5.293648
					},
					"urls": {
					  "nl-NL": "/station-s-hertogenbosch",
					  "en-GB": "/en/station-s-hertogenbosch"
					}
				  },
				  "fallbackName": null
				},
				{
				  "arrival": "2013-01-21T20:14",
				  "departure": null,
				  "platform": "1",
				  "location": {
					"id": "station-eindhoven",
					"type": "station",
					"stationId": "ehv",
					"stationType": "Station",
					"name": "Eindhoven",
					"place": {
					  "name": "Eindhoven",
					  "regionCode": "NB",
					  "regionName": "Noord-Brabant",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 51.442882,
					  "long": 5.479704
					},
					"urls": {
					  "nl-NL": "/station-eindhoven",
					  "en-GB": "/en/station-eindhoven"
					}
				  },
				  "fallbackName": null
				}
			  ]
			}
		  ],
		  "fareInfo": {
			"complete": true,
			"fullPriceCents": 1790,
			"reducedPriceCents": 1070,
			"legs": [
			  {
				"from": {
				  "id": "station-amsterdam-centraal",
				  "type": "station",
				  "stationId": "asd",
				  "stationType": "Station",
				  "name": "Amsterdam Centraal",
				  "place": {
					"name": "Amsterdam",
					"regionCode": "NH",
					"regionName": "Noord-Holland",
					"showRegion": false,
					"countryCode": "NL",
					"countryName": "Nederland",
					"showCountry": false
				  },
				  "latLong": {
					"lat": 52.378706,
					"long": 4.900489
				  },
				  "urls": {
					"nl-NL": "/station-amsterdam-centraal",
					"en-GB": "/en/station-amsterdam-centraal"
				  }
				},
				"to": {
				  "id": "station-eindhoven",
				  "type": "station",
				  "stationId": "ehv",
				  "stationType": "Station",
				  "name": "Eindhoven",
				  "place": {
					"name": "Eindhoven",
					"regionCode": "NB",
					"regionName": "Noord-Brabant",
					"showRegion": false,
					"countryCode": "NL",
					"countryName": "Nederland",
					"showCountry": false
				  },
				  "latLong": {
					"lat": 51.442882,
					"long": 5.479704
				  },
				  "urls": {
					"nl-NL": "/station-eindhoven",
					"en-GB": "/en/station-eindhoven"
				  }
				},
				"locationsString": "Amsterdam - Eindhoven",
				"modeTypeString": "Trein",
				"operatorString": "NS",
				"fares": [
				  {
					"class": "second",
					"reduced": false,
					"eurocents": 1790
				  },
				  {
					"class": "second",
					"reduced": true,
					"eurocents": 1070
				  },
				  {
					"class": "first",
					"reduced": false,
					"eurocents": 3040
				  },
				  {
					"class": "first",
					"reduced": true,
					"eurocents": 1820
				  }
				]
			  }
			]
		  }
		},
		{
		  "id": "fromRef=station-amsterdam-centraal&toRef=station-eindhoven&searchType=departure&dateTime=2013-01-21T19:23&interchangeTime=standard&sequence=1&modes=train:true,bus:true,subway:true,tram:true,ferry:true",
		  "ludMessages": [
			{
			  "text": " Deze reis kan via een ongebruikelijke route verlopen door tijdelijke wijzigingen in verband met bijzondere omstandigheden.",
			  "url": null
			}
		  ],
		  "fasterJourneyId": null,
		  "departure": "2013-01-21T19:23",
		  "arrival": "2013-01-21T20:44",
		  "numberOfChanges": 1,
		  "legs": [
			{
			  "type": "scheduled",
			  "mode": {
				"type": "train",
				"name": "Intercity"
			  },
			  "destination": "Nijmegen",
			  "operator": {
				"type": "ns",
				"name": "NS"
			  },
			  "service": "3071",
			  "attributes": [],
			  "disturbancePlannerIds": [],
			  "serviceMessageIds": [],
			  "stops": [
				{
				  "arrival": "2013-01-21T19:18",
				  "departure": "2013-01-21T19:23",
				  "platform": "5b",
				  "location": {
					"id": "station-amsterdam-centraal",
					"type": "station",
					"stationId": "asd",
					"stationType": "Station",
					"name": "Amsterdam Centraal",
					"place": {
					  "name": "Amsterdam",
					  "regionCode": "NH",
					  "regionName": "Noord-Holland",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 52.378706,
					  "long": 4.900489
					},
					"urls": {
					  "nl-NL": "/station-amsterdam-centraal",
					  "en-GB": "/en/station-amsterdam-centraal"
					}
				  },
				  "fallbackName": null
				},
				{
				  "arrival": "2013-01-21T19:30",
				  "departure": "2013-01-21T19:30",
				  "platform": "4",
				  "location": {
					"id": "station-amsterdam-amstel",
					"type": "station",
					"stationId": "asa",
					"stationType": "Station",
					"name": "Amsterdam Amstel",
					"place": {
					  "name": "Amsterdam",
					  "regionCode": "NH",
					  "regionName": "Noord-Holland",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 52.346689,
					  "long": 4.917453
					},
					"urls": {
					  "nl-NL": "/station-amsterdam-amstel",
					  "en-GB": "/en/station-amsterdam-amstel"
					}
				  },
				  "fallbackName": null
				},
				{
				  "arrival": "2013-01-21T19:50",
				  "departure": "2013-01-21T19:53",
				  "platform": "14",
				  "location": {
					"id": "station-utrecht-centraal",
					"type": "station",
					"stationId": "ut",
					"stationType": "Station",
					"name": "Utrecht Centraal",
					"place": {
					  "name": "Utrecht",
					  "regionCode": "UT",
					  "regionName": "Utrecht",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 52.089597,
					  "long": 5.110411
					},
					"urls": {
					  "nl-NL": "/station-utrecht-centraal",
					  "en-GB": "/en/station-utrecht-centraal"
					}
				  },
				  "fallbackName": null
				}
			  ]
			},
			{
			  "type": "scheduled",
			  "mode": {
				"type": "train",
				"name": "Intercity"
			  },
			  "destination": "Eindhoven",
			  "operator": {
				"type": "ns",
				"name": "NS"
			  },
			  "service": "3571",
			  "attributes": [],
			  "disturbancePlannerIds": [],
			  "serviceMessageIds": [],
			  "stops": [
				{
				  "arrival": "2013-01-21T19:47",
				  "departure": "2013-01-21T19:53",
				  "platform": "15",
				  "location": {
					"id": "station-utrecht-centraal",
					"type": "station",
					"stationId": "ut",
					"stationType": "Station",
					"name": "Utrecht Centraal",
					"place": {
					  "name": "Utrecht",
					  "regionCode": "UT",
					  "regionName": "Utrecht",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 52.089597,
					  "long": 5.110411
					},
					"urls": {
					  "nl-NL": "/station-utrecht-centraal",
					  "en-GB": "/en/station-utrecht-centraal"
					}
				  },
				  "fallbackName": null
				},
				{
				  "arrival": "2013-01-21T20:23",
				  "departure": "2013-01-21T20:24",
				  "platform": "4b",
				  "location": {
					"id": "station-s-hertogenbosch",
					"type": "station",
					"stationId": "ht",
					"stationType": "Station",
					"name": "s-Hertogenbosch",
					"place": {
					  "name": "s Hertogenbosch",
					  "regionCode": "NB",
					  "regionName": "Noord-Brabant",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 51.690625,
					  "long": 5.293648
					},
					"urls": {
					  "nl-NL": "/station-s-hertogenbosch",
					  "en-GB": "/en/station-s-hertogenbosch"
					}
				  },
				  "fallbackName": null
				},
				{
				  "arrival": "2013-01-21T20:44",
				  "departure": null,
				  "platform": "1",
				  "location": {
					"id": "station-eindhoven",
					"type": "station",
					"stationId": "ehv",
					"stationType": "Station",
					"name": "Eindhoven",
					"place": {
					  "name": "Eindhoven",
					  "regionCode": "NB",
					  "regionName": "Noord-Brabant",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 51.442882,
					  "long": 5.479704
					},
					"urls": {
					  "nl-NL": "/station-eindhoven",
					  "en-GB": "/en/station-eindhoven"
					}
				  },
				  "fallbackName": null
				}
			  ]
			}
		  ],
		  "fareInfo": {
			"complete": true,
			"fullPriceCents": 1790,
			"reducedPriceCents": 1070,
			"legs": [
			  {
				"from": {
				  "id": "station-amsterdam-centraal",
				  "type": "station",
				  "stationId": "asd",
				  "stationType": "Station",
				  "name": "Amsterdam Centraal",
				  "place": {
					"name": "Amsterdam",
					"regionCode": "NH",
					"regionName": "Noord-Holland",
					"showRegion": false,
					"countryCode": "NL",
					"countryName": "Nederland",
					"showCountry": false
				  },
				  "latLong": {
					"lat": 52.378706,
					"long": 4.900489
				  },
				  "urls": {
					"nl-NL": "/station-amsterdam-centraal",
					"en-GB": "/en/station-amsterdam-centraal"
				  }
				},
				"to": {
				  "id": "station-eindhoven",
				  "type": "station",
				  "stationId": "ehv",
				  "stationType": "Station",
				  "name": "Eindhoven",
				  "place": {
					"name": "Eindhoven",
					"regionCode": "NB",
					"regionName": "Noord-Brabant",
					"showRegion": false,
					"countryCode": "NL",
					"countryName": "Nederland",
					"showCountry": false
				  },
				  "latLong": {
					"lat": 51.442882,
					"long": 5.479704
				  },
				  "urls": {
					"nl-NL": "/station-eindhoven",
					"en-GB": "/en/station-eindhoven"
				  }
				},
				"locationsString": "Amsterdam - Eindhoven",
				"modeTypeString": "Trein",
				"operatorString": "NS",
				"fares": [
				  {
					"class": "second",
					"reduced": false,
					"eurocents": 1790
				  },
				  {
					"class": "second",
					"reduced": true,
					"eurocents": 1070
				  },
				  {
					"class": "first",
					"reduced": false,
					"eurocents": 3040
				  },
				  {
					"class": "first",
					"reduced": true,
					"eurocents": 1820
				  }
				]
			  }
			]
		  }
		},
		{
		  "id": "fromRef=station-amsterdam-centraal&toRef=station-eindhoven&searchType=departure&dateTime=2013-01-21T19:53&interchangeTime=standard&sequence=1&modes=train:true,bus:true,subway:true,tram:true,ferry:true",
		  "ludMessages": [
			{
			  "text": " Deze reis kan via een ongebruikelijke route verlopen door tijdelijke wijzigingen in verband met bijzondere omstandigheden.",
			  "url": null
			}
		  ],
		  "fasterJourneyId": null,
		  "departure": "2013-01-21T19:53",
		  "arrival": "2013-01-21T21:14",
		  "numberOfChanges": 1,
		  "legs": [
			{
			  "type": "scheduled",
			  "mode": {
				"type": "train",
				"name": "Intercity"
			  },
			  "destination": "Nijmegen",
			  "operator": {
				"type": "ns",
				"name": "NS"
			  },
			  "service": "3073",
			  "attributes": [],
			  "disturbancePlannerIds": [],
			  "serviceMessageIds": [],
			  "stops": [
				{
				  "arrival": "2013-01-21T19:48",
				  "departure": "2013-01-21T19:53",
				  "platform": "5b",
				  "location": {
					"id": "station-amsterdam-centraal",
					"type": "station",
					"stationId": "asd",
					"stationType": "Station",
					"name": "Amsterdam Centraal",
					"place": {
					  "name": "Amsterdam",
					  "regionCode": "NH",
					  "regionName": "Noord-Holland",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 52.378706,
					  "long": 4.900489
					},
					"urls": {
					  "nl-NL": "/station-amsterdam-centraal",
					  "en-GB": "/en/station-amsterdam-centraal"
					}
				  },
				  "fallbackName": null
				},
				{
				  "arrival": "2013-01-21T20:00",
				  "departure": "2013-01-21T20:00",
				  "platform": "4",
				  "location": {
					"id": "station-amsterdam-amstel",
					"type": "station",
					"stationId": "asa",
					"stationType": "Station",
					"name": "Amsterdam Amstel",
					"place": {
					  "name": "Amsterdam",
					  "regionCode": "NH",
					  "regionName": "Noord-Holland",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 52.346689,
					  "long": 4.917453
					},
					"urls": {
					  "nl-NL": "/station-amsterdam-amstel",
					  "en-GB": "/en/station-amsterdam-amstel"
					}
				  },
				  "fallbackName": null
				},
				{
				  "arrival": "2013-01-21T20:20",
				  "departure": "2013-01-21T20:23",
				  "platform": "14b",
				  "location": {
					"id": "station-utrecht-centraal",
					"type": "station",
					"stationId": "ut",
					"stationType": "Station",
					"name": "Utrecht Centraal",
					"place": {
					  "name": "Utrecht",
					  "regionCode": "UT",
					  "regionName": "Utrecht",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 52.089597,
					  "long": 5.110411
					},
					"urls": {
					  "nl-NL": "/station-utrecht-centraal",
					  "en-GB": "/en/station-utrecht-centraal"
					}
				  },
				  "fallbackName": null
				}
			  ]
			},
			{
			  "type": "scheduled",
			  "mode": {
				"type": "train",
				"name": "Intercity"
			  },
			  "destination": "Eindhoven",
			  "operator": {
				"type": "ns",
				"name": "NS"
			  },
			  "service": "3573",
			  "attributes": [],
			  "disturbancePlannerIds": [],
			  "serviceMessageIds": [],
			  "stops": [
				{
				  "arrival": "2013-01-21T20:17",
				  "departure": "2013-01-21T20:23",
				  "platform": "15",
				  "location": {
					"id": "station-utrecht-centraal",
					"type": "station",
					"stationId": "ut",
					"stationType": "Station",
					"name": "Utrecht Centraal",
					"place": {
					  "name": "Utrecht",
					  "regionCode": "UT",
					  "regionName": "Utrecht",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 52.089597,
					  "long": 5.110411
					},
					"urls": {
					  "nl-NL": "/station-utrecht-centraal",
					  "en-GB": "/en/station-utrecht-centraal"
					}
				  },
				  "fallbackName": null
				},
				{
				  "arrival": "2013-01-21T20:53",
				  "departure": "2013-01-21T20:54",
				  "platform": "4b",
				  "location": {
					"id": "station-s-hertogenbosch",
					"type": "station",
					"stationId": "ht",
					"stationType": "Station",
					"name": "s-Hertogenbosch",
					"place": {
					  "name": "s Hertogenbosch",
					  "regionCode": "NB",
					  "regionName": "Noord-Brabant",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 51.690625,
					  "long": 5.293648
					},
					"urls": {
					  "nl-NL": "/station-s-hertogenbosch",
					  "en-GB": "/en/station-s-hertogenbosch"
					}
				  },
				  "fallbackName": null
				},
				{
				  "arrival": "2013-01-21T21:14",
				  "departure": null,
				  "platform": "1",
				  "location": {
					"id": "station-eindhoven",
					"type": "station",
					"stationId": "ehv",
					"stationType": "Station",
					"name": "Eindhoven",
					"place": {
					  "name": "Eindhoven",
					  "regionCode": "NB",
					  "regionName": "Noord-Brabant",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 51.442882,
					  "long": 5.479704
					},
					"urls": {
					  "nl-NL": "/station-eindhoven",
					  "en-GB": "/en/station-eindhoven"
					}
				  },
				  "fallbackName": null
				}
			  ]
			}
		  ],
		  "fareInfo": {
			"complete": true,
			"fullPriceCents": 1790,
			"reducedPriceCents": 1070,
			"legs": [
			  {
				"from": {
				  "id": "station-amsterdam-centraal",
				  "type": "station",
				  "stationId": "asd",
				  "stationType": "Station",
				  "name": "Amsterdam Centraal",
				  "place": {
					"name": "Amsterdam",
					"regionCode": "NH",
					"regionName": "Noord-Holland",
					"showRegion": false,
					"countryCode": "NL",
					"countryName": "Nederland",
					"showCountry": false
				  },
				  "latLong": {
					"lat": 52.378706,
					"long": 4.900489
				  },
				  "urls": {
					"nl-NL": "/station-amsterdam-centraal",
					"en-GB": "/en/station-amsterdam-centraal"
				  }
				},
				"to": {
				  "id": "station-eindhoven",
				  "type": "station",
				  "stationId": "ehv",
				  "stationType": "Station",
				  "name": "Eindhoven",
				  "place": {
					"name": "Eindhoven",
					"regionCode": "NB",
					"regionName": "Noord-Brabant",
					"showRegion": false,
					"countryCode": "NL",
					"countryName": "Nederland",
					"showCountry": false
				  },
				  "latLong": {
					"lat": 51.442882,
					"long": 5.479704
				  },
				  "urls": {
					"nl-NL": "/station-eindhoven",
					"en-GB": "/en/station-eindhoven"
				  }
				},
				"locationsString": "Amsterdam - Eindhoven",
				"modeTypeString": "Trein",
				"operatorString": "NS",
				"fares": [
				  {
					"class": "second",
					"reduced": false,
					"eurocents": 1790
				  },
				  {
					"class": "second",
					"reduced": true,
					"eurocents": 1070
				  },
				  {
					"class": "first",
					"reduced": false,
					"eurocents": 3040
				  },
				  {
					"class": "first",
					"reduced": true,
					"eurocents": 1820
				  }
				]
			  }
			]
		  }
		},
		{
		  "id": "fromRef=station-amsterdam-centraal&toRef=station-eindhoven&searchType=departure&dateTime=2013-01-21T20:08&interchangeTime=standard&sequence=1&modes=train:true,bus:true,subway:true,tram:true,ferry:true",
		  "ludMessages": [
			{
			  "text": " Deze reis kan via een ongebruikelijke route verlopen door tijdelijke wijzigingen in verband met bijzondere omstandigheden.",
			  "url": null
			}
		  ],
		  "fasterJourneyId": null,
		  "departure": "2013-01-21T20:08",
		  "arrival": "2013-01-21T21:29",
		  "numberOfChanges": 0,
		  "legs": [
			{
			  "type": "scheduled",
			  "mode": {
				"type": "train",
				"name": "Intercity"
			  },
			  "destination": "Maastricht",
			  "operator": {
				"type": "ns",
				"name": "NS"
			  },
			  "service": "875",
			  "attributes": [],
			  "disturbancePlannerIds": [],
			  "serviceMessageIds": [],
			  "stops": [
				{
				  "arrival": null,
				  "departure": "2013-01-21T20:08",
				  "platform": "4b",
				  "location": {
					"id": "station-amsterdam-centraal",
					"type": "station",
					"stationId": "asd",
					"stationType": "Station",
					"name": "Amsterdam Centraal",
					"place": {
					  "name": "Amsterdam",
					  "regionCode": "NH",
					  "regionName": "Noord-Holland",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 52.378706,
					  "long": 4.900489
					},
					"urls": {
					  "nl-NL": "/station-amsterdam-centraal",
					  "en-GB": "/en/station-amsterdam-centraal"
					}
				  },
				  "fallbackName": null
				},
				{
				  "arrival": "2013-01-21T20:15",
				  "departure": "2013-01-21T20:15",
				  "platform": "4",
				  "location": {
					"id": "station-amsterdam-amstel",
					"type": "station",
					"stationId": "asa",
					"stationType": "Station",
					"name": "Amsterdam Amstel",
					"place": {
					  "name": "Amsterdam",
					  "regionCode": "NH",
					  "regionName": "Noord-Holland",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 52.346689,
					  "long": 4.917453
					},
					"urls": {
					  "nl-NL": "/station-amsterdam-amstel",
					  "en-GB": "/en/station-amsterdam-amstel"
					}
				  },
				  "fallbackName": null
				},
				{
				  "arrival": "2013-01-21T20:35",
				  "departure": "2013-01-21T20:38",
				  "platform": "15",
				  "location": {
					"id": "station-utrecht-centraal",
					"type": "station",
					"stationId": "ut",
					"stationType": "Station",
					"name": "Utrecht Centraal",
					"place": {
					  "name": "Utrecht",
					  "regionCode": "UT",
					  "regionName": "Utrecht",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 52.089597,
					  "long": 5.110411
					},
					"urls": {
					  "nl-NL": "/station-utrecht-centraal",
					  "en-GB": "/en/station-utrecht-centraal"
					}
				  },
				  "fallbackName": null
				},
				{
				  "arrival": "2013-01-21T21:07",
				  "departure": "2013-01-21T21:09",
				  "platform": "4b",
				  "location": {
					"id": "station-s-hertogenbosch",
					"type": "station",
					"stationId": "ht",
					"stationType": "Station",
					"name": "s-Hertogenbosch",
					"place": {
					  "name": "s Hertogenbosch",
					  "regionCode": "NB",
					  "regionName": "Noord-Brabant",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 51.690625,
					  "long": 5.293648
					},
					"urls": {
					  "nl-NL": "/station-s-hertogenbosch",
					  "en-GB": "/en/station-s-hertogenbosch"
					}
				  },
				  "fallbackName": null
				},
				{
				  "arrival": "2013-01-21T21:29",
				  "departure": "2013-01-21T21:32",
				  "platform": "1",
				  "location": {
					"id": "station-eindhoven",
					"type": "station",
					"stationId": "ehv",
					"stationType": "Station",
					"name": "Eindhoven",
					"place": {
					  "name": "Eindhoven",
					  "regionCode": "NB",
					  "regionName": "Noord-Brabant",
					  "showRegion": false,
					  "countryCode": "NL",
					  "countryName": "Nederland",
					  "showCountry": false
					},
					"latLong": {
					  "lat": 51.442882,
					  "long": 5.479704
					},
					"urls": {
					  "nl-NL": "/station-eindhoven",
					  "en-GB": "/en/station-eindhoven"
					}
				  },
				  "fallbackName": null
				}
			  ]
			}
		  ],
		  "fareInfo": {
			"complete": true,
			"fullPriceCents": 1790,
			"reducedPriceCents": 1070,
			"legs": [
			  {
				"from": {
				  "id": "station-amsterdam-centraal",
				  "type": "station",
				  "stationId": "asd",
				  "stationType": "Station",
				  "name": "Amsterdam Centraal",
				  "place": {
					"name": "Amsterdam",
					"regionCode": "NH",
					"regionName": "Noord-Holland",
					"showRegion": false,
					"countryCode": "NL",
					"countryName": "Nederland",
					"showCountry": false
				  },
				  "latLong": {
					"lat": 52.378706,
					"long": 4.900489
				  },
				  "urls": {
					"nl-NL": "/station-amsterdam-centraal",
					"en-GB": "/en/station-amsterdam-centraal"
				  }
				},
				"to": {
				  "id": "station-eindhoven",
				  "type": "station",
				  "stationId": "ehv",
				  "stationType": "Station",
				  "name": "Eindhoven",
				  "place": {
					"name": "Eindhoven",
					"regionCode": "NB",
					"regionName": "Noord-Brabant",
					"showRegion": false,
					"countryCode": "NL",
					"countryName": "Nederland",
					"showCountry": false
				  },
				  "latLong": {
					"lat": 51.442882,
					"long": 5.479704
				  },
				  "urls": {
					"nl-NL": "/station-eindhoven",
					"en-GB": "/en/station-eindhoven"
				  }
				},
				"locationsString": "Amsterdam - Eindhoven",
				"modeTypeString": "Trein",
				"operatorString": "NS",
				"fares": [
				  {
					"class": "second",
					"reduced": false,
					"eurocents": 1790
				  },
				  {
					"class": "second",
					"reduced": true,
					"eurocents": 1070
				  },
				  {
					"class": "first",
					"reduced": false,
					"eurocents": 3040
				  },
				  {
					"class": "first",
					"reduced": true,
					"eurocents": 1820
				  }
				]
			  }
			]
		  }
		}
	  ],
	  "earlier": "/0.1/journeys?lang=nl-NL&from=station-amsterdam-centraal&to=station-eindhoven&searchType=departure&dateTime=2013-01-21T1753&sequence=1&byTrain=true&byBus=true&bySubway=true&byTram=true&byFerry=true&interchangeTime=standard&after=-1",
	  "later": "/0.1/journeys?lang=nl-NL&from=station-amsterdam-centraal&to=station-eindhoven&searchType=departure&dateTime=2013-01-21T2008&sequence=1&byTrain=true&byBus=true&bySubway=true&byTram=true&byFerry=true&interchangeTime=standard&before=-1",
	  "disturbances": [],
	  "serviceMessages": [],
	  "nearbyAddresses": []
	}
