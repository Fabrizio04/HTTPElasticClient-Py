# HTTPElasticClient-Py

## HTTPElasticClient è una classe Python basata sulle Elastic REST APIs, per la gestione di base (inserimento, aggiornamento, cancellazione e ricerca) dei documenti di un Server Elasticsearch

### Requisiti

- requests
- json
- urllib3

### Esempio

```python
from HTTPElasticClient import HTTPElasticClient
import json

elastic = HTTPElasticClient("https://192.168.1.64:9200")
elastic.verify_connect = False
elastic.auth_cred = ("elastic", "Fabrizio123")
elastic.response = True
elastic.index = "persone"

nuovaPersona = {
    "id": "001",
    "nome": "Fabrizio",
    "cognome": "Amorelli"
}

try:
    
    elastic.CreateDocument(nuovaPersona, nuovaPersona["id"])
    #elastic.DeleteDocument("002")
    #persona = elastic.GetDocumentById("003")
    persona = elastic.GetDocumentByField("cognome","Amorelli")

    print(json.dumps(persona, indent=4, sort_keys=True))

except Exception as e:
    print(e.args)
```
