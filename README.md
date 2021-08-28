# venue-pwa-specs

Specifications for a PWA to let venue owners scan participant green pass and store their contact 

Users of the application are venue owners, who autenticates using their credentials against an OAUTH api service.
The application will consume a REST API for all operations (specs will be available soon).

The application must be completeley usable on mobile device and installed using PWA technology.

The application will consists in two simple pages so far.

## Page #1 Events management
* Adding new events (form with 3 fields: name, date, max_attendants)
* Managing existing events (changing event's data)
* Start scanning attendants for the event
# Page #2 Attendands scanner
* The page will contain the list of current attendands (fetched from API)
* Pressing a "SCAN" button the app triggers the phone camera in code scanning mode (or maybe can just trigger a photo upload with camera)
* Once the QR Code content is received must be passed to the API
* The API parse the code and return the response (attendant accepted or attendand rejected)
* After the scan, if the attendand was accepted, the app will prompt another form to insert attendand phone number
* When the phone number is validated (on frontend side), is passed to the API that will record the attendand at return back the updated list
* The app can fetch the list and update the page.
