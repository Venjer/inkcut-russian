### Translate
Inkcut currently supports English, French, German and Russian. You can easily translate it into another language.

Once the `.qm` file exists, add the language name (a member of `QtCore.QLocale`, for example `Russian` for `ru_RU`) to `ALL_TRANSLATIONS` in `inkcut/core/plugin.py`.

#### Generate language file
To generate language 'ts' file, you need to run this lupdate-qt5 command replacing fr_FR by the language you want to add.
```bash
lupdate-qt5 inkcut/*/*.enaml -I inkcut/*/*/*.enaml -ts inkcut/res/translations/fr_FR.ts
```

Note that the command above only scans `.enaml` files. A few strings are in `.py` files
(for example `inkcut/job/ordering.py`), so pass those files to `lupdate` as well.

#### Translate
The generated ts file can be translated using Qt5 linguistic application

#### Prepare files for release
Before release a new version, or in order to test your translation you need to execute the following command :

```bash
lrelease-qt5 inkcut/res/translations/*.ts
```

This will generate the necessary qm file that will be used by Inkcut
