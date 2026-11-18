- Szczegolowe dane o posle.  

przykladwoe żadanie:  

```
$ curl 'https://api.sejm.gov.pl/sejm/term10/MP/1' -i -X GET \
    -H 'Accept: application/json'
```

Przykladowa odpoweidz 

```
{
  "accusativeName" : "Andrzeja Adamczyka",
  "active" : true,
  "birthDate" : "1959-01-04",
  "birthLocation" : "Krzeszowice",
  "club" : "PiS",
  "districtName" : "Kraków",
  "districtNum" : 13,
  "educationLevel" : "wyższe",
  "email" : "Andrzej.Adamczyk@sejm.pl",
  "firstLastName" : "Andrzej Adamczyk",
  "firstName" : "Andrzej",
  "genitiveName" : "Andrzeja Adamczyka",
  "id" : 1,
  "lastFirstName" : "Adamczyk Andrzej",
  "lastName" : "Adamczyk",
  "numberOfVotes" : 45171,
  "oathDate" : "2023-11-13",
  "profession" : "ekonomista",
  "secondName" : "Mieczysław",
  "voivodeship" : "małopolskie"
}
```

- Statystyki glosowan. 
przykladowe zadanei
```
$ curl 'https://api.sejm.gov.pl/sejm/term10/MP/1/votings/stats' -i -X GET \
    -H 'Accept: application/json'
```
Przykladowa odpowiedz. 

```
[ {
  "absenceExcuse" : false,
  "date" : "2023-11-13",
  "numMissed" : 0,
  "numVoted" : 8,
  "numVotings" : 8,
  "sitting" : 1
}, {
  "absenceExcuse" : false,
  "date" : "2023-11-14",
  "numMissed" : 0,
  "numVoted" : 5,
  "numVotings" : 5,
  "sitting" : 1
}, {
  "absenceExcuse" : false,
  "date" : "2023-11-21",
  "numMissed" : 0,
  "numVoted" : 10,
  "numVotings" : 10,
  "sitting" : 1
} ]
```

- Glosy oddane przez posla. 
przykladowe zadanie. 


```
$ curl 'https://api.sejm.gov.pl/sejm/term10/MP/1/votings/1/2023-11-13' -i -X GET \
    -H 'Accept: application/json'
```

przykladowa odpowiedz

```
[ {
  "date" : "2023-11-13T15:17:22",
  "description" : "wybór Marszałka Sejmu",
  "kind" : "ON_LIST",
  "listVotes" : {
    "2" : "WITEK ELŻBIETA"
  },
  "title" : "Wybór Marszałka Sejmu RP",
  "topic" : "Wybór Marszałka Sejmu RP",
  "vote" : "VOTE_VALID",
  "votingNumber" : 1
}, {
  "date" : "2023-11-13T18:02:12",
  "description" : "w sprawie ustalenia liczby wicemarszałków Sejmu",
  "kind" : "ELECTRONIC",
  "title" : "Pkt. 2 Poselskie projekty uchwał w sprawie ustalenia liczby Wicemarszałków Sejmu RP (druki nr 1 i 2)",
  "vote" : "YES",
  "votingNumber" : 2
}, {
  "date" : "2023-11-13T19:41:22",
  "description" : "w sprawie wyboru Krzysztofa Bosaka na wicemarszałka Sejmu",
  "kind" : "ELECTRONIC",
  "title" : "Pkt. 3 Wybór Wicemarszałków Sejmu RP (druki nr 3, 4, 5, 6, 7 i 8)",
  "topic" : "Głosowanie nad kandydaturą Posła Krzysztofa Bosaka na stanowisko Wicemarszałka Sejmu",
  "vote" : "YES",
  "votingNumber" : 3
}, {
  "date" : "2023-11-13T19:42:14",
  "description" : "w sprawie wyboru Włodzimierza Czarzastego na wicemarszałka Sejmu",
  "kind" : "ELECTRONIC",
  "title" : "Pkt. 3 Wybór Wicemarszałków Sejmu RP (druki nr 3, 4, 5, 6, 7 i 8)",
  "topic" : "Głosowanie nad kandydaturą Posła Włodzimierza Czarzastego na stanowisko Wicemarszałka Sejmu",
  "vote" : "NO",
  "votingNumber" : 4
}, {
  "date" : "2023-11-13T19:43:07",
  "description" : "w sprawie wyboru Doroty Niedzieli na wicemarszałka Sejmu",
  "kind" : "ELECTRONIC",
  "title" : "Pkt. 3 Wybór Wicemarszałków Sejmu RP (druki nr 3, 4, 5, 6, 7 i 8)",
  "topic" : "Głosowanie nad kandydaturą Poseł Doroty Niedzieli na stanowisko Wicemarszałka Sejmu",
  "vote" : "NO",
  "votingNumber" : 5
}, {
  "date" : "2023-11-13T19:43:53",
  "description" : "w sprawie wyboru Moniki Wielichowskiej na wicemarszałka Sejmu",
  "kind" : "ELECTRONIC",
  "title" : "Pkt. 3 Wybór Wicemarszałków Sejmu RP (druki nr 3, 4, 5, 6, 7 i 8)",
  "topic" : "Głosowanie nad kandydaturą Poseł Moniki Wielichowskiej na stanowisko Wicemarszałka Sejmu",
  "vote" : "NO",
  "votingNumber" : 6
}, {
  "date" : "2023-11-13T19:44:45",
  "description" : "w sprawie wyboru Elżbiety Witek na wicemarszałka Sejmu",
  "kind" : "ELECTRONIC",
  "title" : "Pkt. 3 Wybór Wicemarszałków Sejmu RP (druki nr 3, 4, 5, 6, 7 i 8)",
  "topic" : "Głosowanie nad kandydaturą Poseł Elżbiety Witek na stanowisko Wicemarszałka Sejmu",
  "vote" : "YES",
  "votingNumber" : 7
}, {
  "date" : "2023-11-13T19:45:35",
  "description" : "w sprawie wyboru Piotra Zgorzelskiego na wicemarszałka Sejmu",
  "kind" : "ELECTRONIC",
  "title" : "Pkt. 3 Wybór Wicemarszałków Sejmu RP (druki nr 3, 4, 5, 6, 7 i 8)",
  "topic" : "Głosowanie nad kandydaturą Posła Piotra Zgorzelskiego na stanowisko Wicemarszałka Sejmu",
  "vote" : "NO",
  "votingNumber" : 8
} ]
```

- Lista glosowan:  
przykladowe zadanie. 

```
$ curl 'https://api.sejm.gov.pl/sejm/term10/votings/4' -i -X GET \
    -H 'Accept: application/json'
```

przykladowa odpoweidz

```
[ {
  "abstain" : 3,
  "date" : "2024-01-25T10:12:10",
  "kind" : "ELECTRONIC",
  "links" : [ {
    "href" : "https://api.sejm.gov.pl/sejm/term10/votings/4/1/pdf",
    "rel" : "pdf"
  } ],
  "majorityType" : "SIMPLE_MAJORITY",
  "majorityVotes" : 239,
  "no" : 238,
  "notParticipating" : 31,
  "present" : 0,
  "sitting" : 4,
  "sittingDay" : 1,
  "term" : 10,
  "title" : "4. posiedzenie Sejmu RP w dniach 25 i 26 stycznia 2024 r.",
  "topic" : "Wniosek o przerwę",
  "totalVoted" : 426,
  "votingNumber" : 1,
  "yes" : 185
}, {
  "abstain" : 8,
  "date" : "2024-01-25T10:37:40",
  "description" : "wniosek z druku nr 174",
  "kind" : "ELECTRONIC",
  "links" : [ {
    "href" : "https://api.sejm.gov.pl/sejm/term10/votings/4/2/pdf",
    "rel" : "pdf"
  } ],
  "majorityType" : "SIMPLE_MAJORITY",
  "majorityVotes" : 3,
  "no" : 2,
  "notParticipating" : 27,
  "present" : 0,
  "sitting" : 4,
  "sittingDay" : 1,
  "term" : 10,
  "title" : "Pkt. 1 Zmiany w składach osobowych komisji sejmowych (druk nr 174)",
  "topic" : "głosowanie nad przyjęciem wniosku z druku.",
  "totalVoted" : 430,
  "votingNumber" : 2,
  "yes" : 420
}, {
  "abstain" : 0,
  "date" : "2024-01-26T09:14:49",
  "kind" : "ELECTRONIC",
  "links" : [ {
    "href" : "https://api.sejm.gov.pl/sejm/term10/votings/4/3/pdf",
    "rel" : "pdf"
  } ],
  "majorityType" : "SIMPLE_MAJORITY",
  "majorityVotes" : 238,
  "no" : 237,
  "notParticipating" : 31,
  "present" : 0,
  "sitting" : 4,
  "sittingDay" : 2,
  "term" : 10,
  "title" : "4. posiedzenie Sejmu RP w dniach 25 i 26 stycznia 2024 r.",
  "topic" : "Wniosek o przerwę",
  "totalVoted" : 427,
  "votingNumber" : 3,
  "yes" : 190
} ]
```


- Szczegoly glosowania:  

Przykladow zadanie:

```
$ curl 'https://api.sejm.gov.pl/sejm/term10/votings/1/2' -i -X GET \
    -H 'Accept: application/json'
```

przykladodwa odpowiedz
```
{
  "abstain" : 0,
  "date" : "2023-11-13T18:02:12",
  "description" : "w sprawie ustalenia liczby wicemarszałków Sejmu",
  "kind" : "ELECTRONIC",
  "links" : [ {
    "href" : "https://api.sejm.gov.pl/sejm/term10/votings/1/2/pdf",
    "rel" : "pdf"
  } ],
  "majorityType" : "SIMPLE_MAJORITY",
  "majorityVotes" : 1,
  "no" : 0,
  "notParticipating" : 2,
  "present" : 0,
  "sitting" : 1,
  "sittingDay" : 1,
  "term" : 10,
  "title" : "Pkt. 2 Poselskie projekty uchwał w sprawie ustalenia liczby Wicemarszałków Sejmu RP (druki nr 1 i 2)",
  "totalVoted" : 458,
  "votes" : [ {
    "MP" : 1,
    "club" : "PiS",
    "firstName" : "Andrzej",
    "lastName" : "Adamczyk",
    "secondName" : "Mieczysław",
    "vote" : "YES"
  }, {
    "MP" : 2,
    "club" : "KO",
    "firstName" : "Piotr",
    "lastName" : "Adamowicz",
    "vote" : "YES"
  }, {
    "MP" : 3,
    "club" : "PiS",
    "firstName" : "Adam",
    "lastName" : "Andruszkiewicz",
    "vote" : "YES"
  } ],
  "votingNumber" : 2,
  "yes" : 458
}
```

- Glosowanie na liste

przykladowe zadanie 

```
$ curl 'https://api.sejm.gov.pl/sejm/term10/votings/1/1' -i -X GET \
    -H 'Accept: application/json'
```

przykladowa odpowiedz

```
{
  "abstain" : 0,
  "againstAll" : 1,
  "date" : "2023-11-13T15:17:22",
  "description" : "wybór Marszałka Sejmu",
  "kind" : "ON_LIST",
  "links" : [ {
    "href" : "https://api.sejm.gov.pl/sejm/term10/votings/1/1/pdf",
    "rel" : "pdf"
  } ],
  "majorityType" : "ABSOLUTE_MAJORITY",
  "majorityVotes" : 230,
  "no" : 0,
  "notParticipating" : 1,
  "present" : 0,
  "sitting" : 1,
  "sittingDay" : 1,
  "term" : 10,
  "title" : "Wybór Marszałka Sejmu RP",
  "topic" : "Wybór Marszałka Sejmu RP",
  "totalVoted" : 459,
  "votes" : [ {
    "MP" : 1,
    "club" : "PiS",
    "firstName" : "Andrzej",
    "lastName" : "Adamczyk",
    "listVotes" : {
      "1" : "NO",
      "2" : "YES"
    },
    "secondName" : "Mieczysław",
    "vote" : "VOTE_VALID"
  }, {
    "MP" : 2,
    "club" : "KO",
    "firstName" : "Piotr",
    "lastName" : "Adamowicz",
    "listVotes" : {
      "1" : "YES",
      "2" : "NO"
    },
    "vote" : "VOTE_VALID"
  }, {
    "MP" : 3,
    "club" : "PiS",
    "firstName" : "Adam",
    "lastName" : "Andruszkiewicz",
    "listVotes" : {
      "1" : "NO",
      "2" : "YES"
    },
    "vote" : "VOTE_VALID"
  } ],
  "votingNumber" : 1,
  "votingOptions" : [ {
    "option" : "HOŁOWNIA SZYMON",
    "optionIndex" : 1,
    "votes" : 265
  }, {
    "option" : "WITEK ELŻBIETA",
    "optionIndex" : 2,
    "votes" : 193
  } ],
  "yes" : 0
}
```

- Wyszukiwanie glosowan 

przykladow zadanie
```
$ curl 'https://api.sejm.gov.pl/sejm/term10/votings/search?proceeding=1&dateFrom=2023-11-01&dateTo=2024-01-01&title=marsza%C5%82ka' -i -X GET \
    -H 'Accept: application/json'
```

przykladowa odpowiedz

```
[ {
  "abstain" : 0,
  "againstAll" : 1,
  "date" : "2023-11-13T15:17:22",
  "description" : "wybór Marszałka Sejmu",
  "kind" : "ON_LIST",
  "links" : [ {
    "href" : "https://api.sejm.gov.pl/sejm/term10/votings/1/1/pdf",
    "rel" : "pdf"
  } ],
  "majorityType" : "ABSOLUTE_MAJORITY",
  "majorityVotes" : 230,
  "no" : 0,
  "notParticipating" : 1,
  "present" : 0,
  "sitting" : 1,
  "sittingDay" : 1,
  "term" : 10,
  "title" : "Wybór Marszałka Sejmu RP",
  "topic" : "Wybór Marszałka Sejmu RP",
  "totalVoted" : 459,
  "votingNumber" : 1,
  "votingOptions" : [ {
    "option" : "HOŁOWNIA SZYMON",
    "optionIndex" : 1,
    "votes" : 265
  }, {
    "option" : "WITEK ELŻBIETA",
    "optionIndex" : 2,
    "votes" : 193
  } ],
  "yes" : 0
}, {
  "abstain" : 153,
  "date" : "2023-11-13T19:41:22",
  "description" : "w sprawie wyboru Krzysztofa Bosaka na wicemarszałka Sejmu",
  "kind" : "ELECTRONIC",
  "links" : [ {
    "href" : "https://api.sejm.gov.pl/sejm/term10/votings/1/3/pdf",
    "rel" : "pdf"
  } ],
  "majorityType" : "ABSOLUTE_MAJORITY",
  "majorityVotes" : 227,
  "no" : 27,
  "notParticipating" : 8,
  "present" : 0,
  "sitting" : 1,
  "sittingDay" : 1,
  "term" : 10,
  "title" : "Pkt. 3 Wybór Wicemarszałków Sejmu RP (druki nr 3, 4, 5, 6, 7 i 8)",
  "topic" : "Głosowanie nad kandydaturą Posła Krzysztofa Bosaka na stanowisko Wicemarszałka Sejmu",
  "totalVoted" : 452,
  "votingNumber" : 3,
  "yes" : 272
}, {
  "abstain" : 12,
  "date" : "2023-11-13T19:42:14",
  "description" : "w sprawie wyboru Włodzimierza Czarzastego na wicemarszałka Sejmu",
  "kind" : "ELECTRONIC",
  "links" : [ {
    "href" : "https://api.sejm.gov.pl/sejm/term10/votings/1/4/pdf",
    "rel" : "pdf"
  } ],
  "majorityType" : "ABSOLUTE_MAJORITY",
  "majorityVotes" : 230,
  "no" : 196,
  "notParticipating" : 2,
  "present" : 0,
  "sitting" : 1,
  "sittingDay" : 1,
  "term" : 10,
  "title" : "Pkt. 3 Wybór Wicemarszałków Sejmu RP (druki nr 3, 4, 5, 6, 7 i 8)",
  "topic" : "Głosowanie nad kandydaturą Posła Włodzimierza Czarzastego na stanowisko Wicemarszałka Sejmu",
  "totalVoted" : 458,
  "votingNumber" : 4,
  "yes" : 250
} ]
```