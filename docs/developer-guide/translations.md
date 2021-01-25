# Translations

PhotoPrism uses [gettext](https://en.wikipedia.org/wiki/Gettext) for localizing frontend and backend.
It's one of the most widely adopted standards for translating user interfaces.
 
Human readable messages like `File not found` are used as ids for finding matching translations, 
and used as defaults whenever there is no translation available.

Messages may optionally contain placeholders, like `Found %{n} files`, for numbers and 
other variables.

We strongly recommend [Poedit](https://poedit.net/download) for creating and updating translations.
Download is free for Mac, Windows and Linux.
Its source code can be obtained on [GitHub](https://github.com/vslavik/poedit).

## Frontend ##

Localizations can be found in `/frontend/src/locales`. The POT file, only containing message ids, 
is `translations.pot`.

`*.po` files contain localized messages for each 
[language](https://www.gnu.org/software/gettext/manual/html_node/Usual-Language-Codes.html#Usual-Language-Codes),
identified by their [two-letter locale](https://www.gnu.org/software/gettext/manual/html_node/Locale-Names.html), 
like `de.po` for German or `pt_BR` for Brazilian Portuguese.
You can open, edit and save them with Poedit to update existing translations.

### Add new translation ###
- In /frontend run `npm run gettext-extract`
- Install a translation tool e.g. Poedit
- Open the `/frontend/src/locales/translations.pot` file with Poedit
- In Poedit click on "Create New Translation" at the bottom, select the language, and start translating
- When done, save your translation as `*.po` file using the two-letter language locale (e.g. `de.po`) as name
- Add the new language to the `Languages` function in  `/frontend/src/options/options.js`
- To test your translations you need to build the frontend again using `npm run build` or `npm run watch`


### Update existing translation ###
- Install a translation tool e.g. Poedit
- Open the `*.po` file of your language e.g. `/frontend/src/locales/fr.po` file with Poedit
- In the Poedit menu click "Catalogue" --> "Update from POT File" --> select the `translations.pot` file from `/frontend/src/locales`
- Now you can start proofreading and adding the missing translations
- Once your done save the changes in the `*.po` file
- To test your translations you need to build the frontend again using `npm run build` or `npm run watch`

!!! note
    A binary `*.mo` (machine object) file will be automatically saved along with every `*.po` file. 
    You won't be able to open those in a text editor, but please include them in git commits or when sending
    translations via email.
    
## Backend ##

Only asynchronous notifications and certain API responses need translation to provide a 
consistent user experience.
Technical log messages should be in English to avoid ambiguities and (even slightly) wrong translations. 

Localizations are kept in `/assets/locales`. The POT file, only containing message ids, is `messages.pot`.

`default.po` files in sub directories contain localized messages for each 
[language](https://www.gnu.org/software/gettext/manual/html_node/Usual-Language-Codes.html#Usual-Language-Codes),
identified by their [two-letter locale](https://www.gnu.org/software/gettext/manual/html_node/Locale-Names.html), 
like `de/default.po` for German. You can open, edit and save them with Poedit. Please
also add and commit binary `*.mo` files, which will be automatically created by Poedit.


### Add new translation ###
- Run `make generate` to update `/assets/locales/messages.pot`
- Open the `/assets/locales/messages.pot` file with Poedit
- In Poedit click on "Create New Translation" at the bottom, select the language, and start translating
- When done, create a new directory (using the locale as name) and save your translation there as `default.po`

### Update existing translation ###
- Run `make generate` to update `/assets/locales/messages.pot`
- Open the `/assets/locales/fr/default.po` file with Poedit
- In the Poedit menu click "Catalogue" --> "Update from POT File" --> select the messages.pot file from /assets/locales/
- Now you can start proofreading and adding the missing translations
- Once your done, save the changes in the default.po file

!!! info
    Note that this will only work when you have gettext installed on your system.
    We recommend using our latest development image as described in the Developer Guide.


