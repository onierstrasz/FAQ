# Pier FAQ (Obsolete)

NB: The server has been migrated to Pico.

---

* How do I restart the scg pier?
- sudo service scgpier restart

-> http://scg.unibe.ch/wiki/faq/pierfaq

* How do I connect to the scgpier image?
- Open vnc://scg.unibe.ch
  server scg.unibe.ch; pwd (see pwd file)

* How can I run the pier image locally?
- Use the Squeak 4.2.1beta1U.app VM

* How to configure apache?
- ???

* How do I enable halos?

[I can login to http://scg.unibe.ch:8080/seaside/config but I cannot access the scg pier in devt mode (links are all broken) -- need to reconfigure apache?]

* How do I delete a broken news item?

This often happens if an scgbib entry contains a noin ascii character. Fix the bib entry, check the abstract display, then delete the new entry, amd touch the pdf to recreate the new entry.

To delete the entry, login as scg. Open the "browse" command in the home page, navigate to the news browse view, and delete the last entry. 

---
