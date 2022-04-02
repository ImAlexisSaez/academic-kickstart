---
widget: contact # An instance of the Contact widget.
active: false # Activate this widget? true/false
headless: true # This file represents a page section.
weight: 130 # Order that this section appears on the page.
title: Contacto
subtitle:

content:
  autolink: true # Automatically link email and phone or display as text?
  form: # Email form provider
    provider: netlify
    formspree:
      id:
    netlify:
      captcha: false # Enable CAPTCHA challenge to reduce spam?
  email: test@example.org # Contact details (edit or remove options as required)
  phone: 888 888 88 88
  address:
    street: 450 Serra Mall
    city: Stanford
    region: CA
    postcode: '94305'
    country: United States
    country_code: US
  coordinates:
    latitude: '37.4275'
    longitude: '-122.1697'
  directions: Enter Building 1 and take the stairs to Office 200 on Floor 2
  office_hours:
    - 'Monday 10:00 to 13:00'
    - 'Wednesday 09:00 to 10:00'
  appointment_url: 'https://calendly.com'
  contact_links:
    - icon: twitter
      icon_pack: fab
      name: DM Me
      link: 'https://twitter.com/Twitter'
    - icon: video
      icon_pack: fas
      name: Zoom Me
      link: 'https://zoom.com'
design:
  columns: '2'
---
