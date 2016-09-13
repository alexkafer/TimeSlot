# TimeSlot
Provides the backend and interface for a simple timeslot manager and queue system. Allows people to regsiter for timeslots and if they do not check in by their time, the server will automatically provide access to the next on the waitlist

## How it works
Starting from zero data on a clean install, a user will navigate to the server's root file using a browser. 
This is done with a `HTTP GET` request to the root path `/`.
The server will present an interface with two sections. 
* Check in / Waitlist
* Request a time slot

### Request a time slot
This section will allow users to select a time, put their name and a way of reminding them (email, text, etc). 
In order to ensure the person who signed up for a timeslot is able to authenticate, each user will be given a unique 6 digit code in this format: TW###-###, with # being replaced with a random number or upper case letter. Users will use this code to check in later.

### Checking in
In this section, a user will be prompted with two options. Enter a code if they have one (see `Request a time slot`) or be added to the waitlist. If they enter a code, they will be given control access during their time.

Users must check in at least a minute before their scheduled time.

#### Waitlist
The waitlist works with first in-first out. Before granted, the user will see their position on the list. If someone reserves a timeslot and doesn't show up (check in a minute before their selected time), that timeslot will be filled with the person on the waitlist the longest (highest up).

## Dependencies
Express.js
Moment.js
voucher-code-generator
