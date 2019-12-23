# Azonmedia Database conventions

## Introduction

This document describes the various conventions when creating new tables and columns.

## Conventions
- Tables naming conventions
  - The names of the tables should always be with the project prefix (which is usually guzaba_) and then the table name separated by underscore. All table names are in small letters
  - the names are in English
  - the name has to be meaningful and when there are tables related to each other they should be with the same prefix even if the name sounds wrong in English. This way a person looking at the main table guzaba_notifications will immediately see the guzaba_notifications_sent and will know all related tables. Here is an example:
      - guzaba_notifications
      - guzaba_notifications_sent **(not guzaba_sent_notifications which sounds correct)**

  - the main table shards must be named with _X (number of the shard) like guzaba_charters, guzaba_charters_2, guzaba_charters_3
  - the array tables and associative array tables must be named guzaba_maintablename_arr & guzaba_maintablename_assoc_arr
  - the language tables must be named guzaba_maintablename_lang

- Columns naming conventions
  - the names of the columns are always lower case separated with underscore
  - the names are in English
  - the columns always have a prefix like **notification**_id.
  - the primary key is always formed by prefix, _, id - prefix_id.
  - usually the prefix matches the table name but it can be shorter if the table name is too long
  - if the table contains a foreign key then the name of this key must match the name of the column in the table to which the FK points to. For example the guzaba_notifications table may look like:
    - notifications_id //primary key
    - notification_to
    - notification_content
    - subject_id //FK to guzaba_subjects->subject_id
  - the exceptions to the above rule are when the FK is to the table itself (think of category_id, category_parent_id) or when there are two or more FKs to the same table (like charter_sales_id, charter_pm_id). It is recommended though even in this case if possible to include the full name of the FK as found in the other column so charter_sales_subject_id & charter_pm_subject_id sounds better.

