# Call webservice soap with curl

* Install curl - sudo apt-get install curl 
* Install xmllint - sudo apt-get install libxml2-utils

```bash
curl -s --header "Content-Type: text/xml;charset=UTF-8" --header "SOAPAction=\"ACTION\"" --data @FILE SERVICE_URL | xmllint --format -
```

**ACTION:** The name of the operation (soapAction). In this case, *GetCurrentTime*

**FILE:** The name of the file the soap request. In this case, *request-soap.xml*

**SERVICE_URL:** The url of the service. In this case, *http://secure.smartbearsoftware.com/samples/testcomplete10/webservices/Service.asmx?WSDL*

# Request soap xml sample

```xml
<?xml version="1.0" encoding="utf-8"?>
<soap12:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap12="http://www.w3.org/2003/05/soap-envelope">
  <soap12:Body>
    <GetCurrentTime xmlns="http://smartbear.com" />
  </soap12:Body>
</soap12:Envelope>
```

# Example

```bash
curl -s --header "Content-Type: text/xml;charset=UTF-8" --header "SOAPAction=\"GetCurrentTime\"" --data @request-soap.xml http://secure.smartbearsoftware.com/samples/testcomplete10/webservices/Service.asmx?WSDL | xmllint --format -
```

# Formated output (xmllint --format)

```xml
<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
  <soap:Body>
    <GetCurrentTimeResponse xmlns="http://smartbear.com">
      <GetCurrentTimeResult>2017-11-27T19:06:34.92975-05:00</GetCurrentTimeResult>
    </GetCurrentTimeResponse>
  </soap:Body>
</soap:Envelope>
```