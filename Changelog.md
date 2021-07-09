# Changelog

## 1.13.4 (backported to 1.10.7) (2021-07-09)

- tenancy query can be used with client_credentials authentication

## 1.13.3 (2021-07-06)

- Condominium#location returns german text of corresponding unit-location-code or free text in case unit data in REM has not been migrated to unit-location-code yet
- managementTeam added to condominiumCommunity

## 1.13.2 (2021-06-28)

- salutation added to tenancyApplicantInput

## v1.13.1 (2021-06-15), requires GARAIO REM v1.13.x or later

- createDamageCase mutation implemented
- updateDamageCase mutation implemented
- subscriptions for newDamageCase and updateDamageCase implemented
- damageCaseDrafts query implemented
- Unit#location returns german text of corresponding unit-location-code or free text in case unit data in REM has not been migrated to unit-location-code yet

## 1.10.6 (2021-04-14)

- accounting#accounts has an optional account group numbers filter
- Fallback for email and phone number to the first in list if no appropriate type (private, professional) was added to the person

## 1.10.5 (2021-04-09)

- tenancy#noticePer implemented
- condominiumCommunities query implemented
- condominiumCommunity type implemented
- condominiumBuilding type implemented
- condominium type implemented
- condominiumOwnership type implemented
- condominiumOwner type implemented

## 1.10.4 (2021-02-15)

- internal stuff

## 1.10.3 (2020-12-05)

- Tenancy.isPrimaryTenant added
- Units with a validFrom date in the future are returned again (regression fixed)
- startOfAdministration and endOfAdministration on Building return the the dates of the building
- startOfAdministration, endOfAdministration fields deprecated on Unit
- zipCode and city on Building deprecated

## 1.10.2 (2020-11-04)

- unit query implemented
- startOfAdministration and endOfAdministration on a building are aligned with startOfAdministration and endOfAdministration of the property, regardless  of the actual stored dates
- the queries ```authenticate``` and ```authenticateService``` are deprecated and will be removed in a future release. To authenticate, send a post request to /external/graphql/authenticate/token instead (see README for details)
- optional ```withHistory``` query paramater added for the properties query and the tenancies field
- fixed wrong tenancy start- / endDates in a assumption of contract scenario (Vertragsumschreibung)
- properties query returns properties that are managed in the future, not only properties that managed as of today
- fields validFrom, validUntil added to Unit

## 1.10.1 (2020-10-08)

- scope authorization added on owner, supplier, accountig and concierge data

## 1.10.0 (2020-08-25)

- type, fullName, postalAddress fields added to Person
- owner field added to Property
- tenancyAgreementTypes code table query added
- tenancyAgreementTypeCode added to Tenancy
- supplierRatings code table query added
- Supplier and suppliers query added
- preferredSuppliers fields added to Property
- Accounting, AccountingAccount  added
- accounting, accountings queries added
- properties query filters non active mandates
- accounting field added to Property
- SupplierOrder added
- supplierOrders query added
- VatRate and vatRates query added
- userId field added to TeamMember
- ConciergeContact added
- conciergeRoles code table query added
- conciergeContracts field added to Property and Building
- surface, cubature fields added to Unit
- startOfAdministration, endOfAdministration fields added to Property and Building
- Complexity limiter implemented (see schema docs for details)

## 1.9.2 (2020-07-30)

- tenancy query added
- determine email and phone number of a Person depending on its type
- ECh0010Address added
- Organisation added
- phoneNumber, email, postalAddress and organisation fields added to User
- admWhgNrBfs field added to unit

## 1.9.1 (2020-05-30)

- internal stuff to enable automated service provisioning

## 1.9.0 (2020-05-14)

- internal refactorings and enhancements

## 1.3.4 (2020-05-01)

- tags code table query added

## 1.3.3 (2020-03-14)

- authenticateService query implemented

## 1.3.2 (2020-01-16)

- better namings in TenancyApplicationDossierInput
- tenancies field for a unti has to deliver tenancies that are valid in the future

## 1.3.1 (2019-08-31)

- tenantName field resolver on Unit handles edge cases

## 1.3.0 (2019-08-30)

- tenantName field on Unit got scope protection
- unitCategoryCode added to Unit
- unitCategories code table query added
- units field on Building got optional unitCategoryCodes filter argument

## 1.2.0 (2019-07-07)

- internal refactorings

## 1.1.0 (2019-07-07)

First public release
