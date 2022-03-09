# RESET-RESTORE-NF

HSS Restoration indication from diameter to SBI.
-----------------------------------------------------------------------------
With eIMS introduction to leverage the Service Based Architecture,
the HSS handling EPC+IMS can under go upgrade or maintenence for patch updates
in that case thre needs a indication to the IMS peers of HSS like CFX or TAS
for restoration.
The old HSS indicates to the diameter peer via new AVP telling that it no more avaialable
to serve the requests and provides a SBI based HSS end point to send the subsequent request on SBI interface
Since HSS has already learnt the CFX and its capabilities, it knows which similar SBI based HSS
can best serve the subsequent IMS N70/N71 API calls.
The old HSS can also indicate the topology of available HSS pools using topoplogyURI
the topology resource can be stored in UDSF or (N)UDR.
HSS can explictly generate Cx-PPR and Sh-PNR to provide this restoration indication to CSCF and TAS.
This provides smooth transition from diamter based HSS to SBI based HSS for eIMS at real time.

**Explicit trigger of data sync by CSCF based on indication of HSS Reset**
--------------------------------------------------------------------------------

HSS will indicate to CSCF that data between HSS and CSCF needs to be resynchronized due to network failures
In that case HSS sends explicit PPR to CFX or on SBI interface it sends a notification via NRF triggering RESET operation
Now the CFX can user Cx-SAR with NO_ASSIGNEMNT but asking user data to HSS or
On N70 interface reload the subscriptions with GET request
This helps to spread the traffic uniformly across many HSS  to sync data for millions of subscribers.
This ideas is specifically for Cx and N70 interface of IMS .This can also be applicable for N71 and Sh interface of IMS or indication to use which interface for this is totally new 
