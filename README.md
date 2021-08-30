# venue-pwa-specs

Specifications for a PWA to let venue owners scan participant tickets / pass and store their contact data.

Users of the application are venue owners, who autenticates using their credentials (see Stack Constraits for more detail on the auth system).

The application will consume a REST API for all operations.

The application must be completeley usable on mobile device and locally installed using PWA technology.

The application will consists in just a simple section so far, here are a simplified workflow for the main feature.

## Events management
* Adding new events (form with 2 fields: name, starts_at)
* Listing existing events (in 3 separate groups for past, incoming and future events)
* Managing existing events (updating event's data or deleting an event)
* Viewing event's attendand list (with a button to print the list if authorized)
* Scanning attendants for an event
### Attendands ticket/pass qr code scanner for an event
* The event page will contain the list of current attendands (fetched from API)
* Pressing a "SCAN" button the app triggers the phone camera in code scanning mode (using any web rtc based solution like [react-qr-scanner](kybarg/react-qr-scanner))
* Once the QR Code content is received must be passed to the API
* The API parse the code and return the response (attendant accepted or attendand rejected)
* After the scan, if the attendand was accepted, the app will prompt another form to insert attendand's contact details (phone number only so far)
* When attendant's contact details are validated (on frontend side), are passed to the API that will record the attendand at return back the updated list
* The app can then fetch the list and update the page.
* Code scans can be done only for incoming events

## Stack constraits

Application should be developed following this directives

* Must use react
* Must be a PWA
* Must be written using TDD or contains 100% coverage tests
* The API authentication system is based on a cookie, since the API domain is the same of the PWA, a boilerplate template will be available to start with authentication already implemented in.
* API specs will be available using OpenApi .yml standard file.
