=====================
django_localflavor_se
=====================

Country-specific Django helpers for Sweden.

What's in the Sweden localflavor?
=================================

* forms.SECountySelect: A Select form widget that uses a list of the Swedish
  counties (län) as its choices. The cleaned value is the official county code
  -- see http://en.wikipedia.org/wiki/Counties_of_Sweden for a list.

* forms.SEOrganisationNumber: A form field that validates input as a Swedish
  organisation number (organisationsnummer).

  It accepts the same input as SEPersonalIdentityField (for sole
  proprietorships (enskild firma). However, co-ordination numbers are not
  accepted.

  It also accepts ordinary Swedish organisation numbers with the format
  NNNNNNNNNN.

  The return value will be YYYYMMDDXXXX for sole proprietors, and NNNNNNNNNN
  for other organisations.

* forms.SEPersonalIdentityNumber: A form field that validates input as a
  Swedish personal identity number (personnummer).

  The correct formats are YYYYMMDD-XXXX, YYYYMMDDXXXX, YYMMDD-XXXX,
  YYMMDDXXXX and YYMMDD+XXXX.

  A \+ indicates that the person is older than 100 years, which will be taken
  into consideration when the date is validated.

  The checksum will be calculated and checked. The birth date is checked
  to be a valid date.

  By default, co-ordination numbers (samordningsnummer) will be accepted. To
  only allow real personal identity numbers, pass the keyword argument
  coordination_number=False to the constructor.

  The cleaned value will always have the format YYYYMMDDXXXX.

* forms.SEPostalCodeField: A form field that validates input as a Swedish
  postal code (postnummer). Valid codes consist of five digits (XXXXX). The
  number can optionally be formatted with a space after the third digit (XXX
  XX). The cleaned value will never contain the space.

See the source code for full details.

About localflavors
==================

Django's "localflavor" packages offer additional functionality for particular
countries or cultures.

For example, these might include form fields for your country's postal codes,
phone number formats or government ID numbers.

This code used to live in Django proper -- in django.contrib.localflavor -- but
was separated into standalone packages in Django 1.5 to keep the framework's
core clean.

For a full list of available localflavors, see https://github.com/django/
