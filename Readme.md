CPIX Test Vectors
=================

Generated 2016-08-11 using Axinom.Cpix v1.0.0

Included test certificates generated as follows: `makecert.exe -pe -n "CN=CPIX Example Entity 1" -sky exchange -a sha512 -len 4096 -r -ss My`. The password for any included PFX files is the filename, without extension, case-sensitive.

Test vector descriptions follow below.

ClearContentKeysOnly
====================

Content keys with values in the clear (without encryption).

Complex
=======

All types of entities, with many data fields filled, with encryption of content keys and with signatures on everything. The document as a whole is signed using Cert4 and each collection is signed using both Cert3 and Cert4.

EvenMoreComplex
===============

A more complex version of the "Complex" test vector! All types of entities, with many data fields filled, with encryption of content keys and with signatures on everything. The document as a whole is signed using Cert4 and each collection is signed using both Cert3 and Cert4.

In addition, nonstandard namespace prefixes are used everywhere, the XML is pretty-printed before signing, the elements to be signed are given unusual id values and various XML comments are added after signing. Finally, the whole thing is encoded using UTF-16.

The resulting output is still valid and all the signatures should successfully pass verification on a conforming implementation!

EmptyDocument
=============

An empty document. Valid, though rather useless.

EncryptedContentKeys
====================

Content keys encrypted for delivery to a specific recipient (Cert1).

The decrypted values of the content keys (base64-encoded here) are: 

* 3rWoHYasQubO6HbJGrGtLw== with ID bd5adf51-cf04-410f-aac3-ec63a69e929e.
* O5w9FdZiwmQK4uIXzAziaQ== with ID d2920429-87ab-41e6-a4c5-a8c836b6312e.
* Cwu/3hSBBRQ7SurBdZD5ow== with ID e17ba4b8-faff-4d30-bcba-7485e3f2e884.
* FB6/Eck9Y9SXy6bY8UU/Mw== with ID 0ae6b9ad-92d2-4ebe-882b-1d07dee70715.


EncryptedContentKeysWithMultipleRecipients
==========================================

Content keys encrypted for delivery to four recipients (Cert1 through Cert4).

Invalid_BadContentKeysSignature
===============================

NB! This test vector intentionally contains invalid data!

The signature on the content key collection should fail validation because one of the content key elements was removed after applying the signature.

Invalid_BadDocumentSignature
============================

NB! This test vector intentionally contains invalid data!

The document signature should fail validation because an extra namespace declaration attribute has been added to the document root element.

Invalid_WrongMac
================

NB! This test vector intentionally contains invalid data!

The MAC on the encrypted content key is invalid! Expected implementation behavior:

* Loading should fail when the recipient (Cert1) tries to decrypt the content key.
* Loading should be successful if no attempt is made to decrypt the content key, as the error can only be discovered during decryption.

RecipientsWithoutContentKeys
============================

Defines a few authorized recipients (Cert3 and Cert4) and delivery data but no actual content keys to deliver.

UsageRulesBasedOnLabels
=======================

Usage rules that map content keys using sets of labels.

