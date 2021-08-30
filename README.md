# venue-pwa-specs

Specifications for a PWA to let venue owners scan participant green pass and store their contact 

Users of the application are venue owners, who autenticates using their credentials against an OAUTH api service.
The application will consume a REST API for all operations (specs will be available soon).

The application must be completeley usable on mobile device and locally installed using PWA technology.

The application will consists in just a simple page so far, here are a simplified workflow for the main feature.

## Events management
* Adding new events (form with 2 fields: name, starts_at)
* Managing existing events (updating event's data or deleting an event)
* Start scanning attendants for the event
### Attendands ticket/pass qr code scanner
* The page will contain the list of current attendands (fetched from API)
* Pressing a "SCAN" button the app triggers the phone camera in code scanning mode (using any web rtc based solution like [react-qr-scanner](kybarg/react-qr-scanner))
* Once the QR Code content is received must be passed to the API
* The API parse the code and return the response (attendant accepted or attendand rejected)
* After the scan, if the attendand was accepted, the app will prompt another form to insert further attendand details (phone number so far)
* When the further details are validated (on frontend side), is passed to the API that will record the attendand at return back the updated list
* The app can then fetch the list and update the page.

## Stack constraits

Application should be developed following this directives

* Must use react
* Must be a PWA
* Must be written using TDD or contains 100% coverage tests
* The API authentication system is based on a cookie, since the API domain is the same of the PWA, a boilerplate template will be available to start with authentication already implemented in.
* API specs will be available using OpenApi .yml standard file.
