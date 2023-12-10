# fhirserver-profile-based-validation
A sample of calls (Postman Collection) to demonstrate FHIR Profile-based Validation Requests

The Postman Collection includes the following requests:

- No Profile Validation
      /$validate is called on a Patient Resource in the Body, without a profile provided in the URL
  - US Patient without Identifier --> even though this Resource is not a valid US Patient (according to US Core) this will pass validation because we are not applying profile-based validation
- Profile in Query Parameter
      /$validate is called on a Patient Resource in the Body, *with* a profile provided in the URL
  - Valid US Patient              --> wiil pass validation, indeed valid
  - US Patient without Identifier --> will fail validation, profile-based validation is applied (against US Patient) and this patient does not have any identifiers
- Profile in Query Body
      /$validate is called on a Parameters Resource in the Body, with a profile provided as a parameter (side by side to the Resource itself)
  - Valid US Patient              --> wiil pass validation, indeed valid
  - US Patient without Identifier --> will fail validation, profile-based validation is applied (against US Patient) and this patient does not have any identifiers
   
To use the Collection against your FHIR server, adapt the 'newValidatorURL' variable to your FHIR endpoint, and adapt the Authentication to the one you use.

