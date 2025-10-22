# comics-lab — Organization Overview

This README describes the overall directory structure of the organization workspace.

## Appendix: Overall Organization Directory Structure

<!-- BEGIN DIR TREE -->
```
comics-lab
├── cbz-doctor
│   ├── cbz_doctor
│   │   ├── __init__.py
│   │   └── cli.py
│   ├── LICENSE
│   ├── Makefile
│   ├── README.md
│   └── requirements.txt
├── comic-file-organizer
│   ├── comic_file_organizer
│   │   ├── __init__.py
│   │   └── cli.py
│   ├── LICENSE
│   ├── Makefile
│   ├── README.md
│   └── requirements.txt
├── comicbook-core
│   ├── comicbook_core
│   │   ├── __init__.py
│   │   ├── config_naming.py
│   │   ├── logging_utils.py
│   │   ├── models.py
│   │   └── report.py
│   ├── LICENSE
│   ├── Makefile
│   ├── README.md
│   └── requirements.txt
├── comicmeta-comicvine
│   ├── comicmeta_comicvine
│   │   ├── __init__.py
│   │   └── cli.py
│   ├── LICENSE
│   ├── Makefile
│   ├── README.md
│   └── requirements.txt
├── comicmeta-gcd
│   ├── comicmeta_gcd
│   │   ├── __init__.py
│   │   └── cli.py
│   ├── LICENSE
│   ├── Makefile
│   ├── README.md
│   └── requirements.txt
├── comicmeta-metron
│   ├── comicmeta_metron
│   │   ├── __init__.py
│   │   └── cli.py
│   ├── LICENSE
│   ├── Makefile
│   ├── README.md
│   └── requirements.txt
├── comics-suite
│   ├── archive
│   │   └── comics-suite-meta-kit.zip
│   ├── docs
│   │   ├── Action-Log.md
│   │   ├── Architecture.md
│   │   ├── forking-other-projects.md
│   │   ├── PROJECT-INDEX.md
│   │   ├── Repo-Standards.md
│   │   └── Security-Checklist.md
│   ├── scripts
│   │   ├── apply_all.sh
│   │   ├── enable_security.sh
│   │   ├── lockdown_actions.sh
│   │   ├── protect_branches.sh
│   │   ├── seed_repos.sh
│   │   ├── setup_org.sh
│   │   ├── update-readmes-kit.zip
│   │   ├── update_readmes.py
│   │   └── verify.sh
│   ├── LICENSE
│   ├── README.md
│   └── README_part2.md
├── comictagger
│   ├── build-tools
│   │   ├── mac
│   │   │   ├── app.icns
│   │   │   ├── make_thin.sh
│   │   │   ├── Makefile
│   │   │   └── volume.icns
│   │   ├── windows
│   │   │   └── app.ico
│   │   ├── ComicTagger.desktop
│   │   ├── comictagger.spec
│   │   ├── dmgbuild.conf
│   │   ├── generate_settngs.py
│   │   ├── get_appimage.py
│   │   ├── oidc-exchange.py
│   │   └── zip_artifacts.py
│   ├── comicapi
│   │   ├── __pyinstaller
│   │   │   ├── __init__.py
│   │   │   └── hook-comicapi.py
│   │   ├── archivers
│   │   │   ├── __init__.py
│   │   │   ├── archiver.py
│   │   │   ├── folder.py
│   │   │   ├── rar.py
│   │   │   ├── sevenzip.py
│   │   │   └── zip.py
│   │   ├── data
│   │   │   ├── __init__.py
│   │   │   └── publishers.json
│   │   ├── tags
│   │   │   ├── __init__.py
│   │   │   ├── comicrack.py
│   │   │   └── tag.py
│   │   ├── __init__.py
│   │   ├── _url.py
│   │   ├── comicarchive.py
│   │   ├── filenamelexer.py
│   │   ├── filenameparser.py
│   │   ├── genericmetadata.py
│   │   ├── issuestring.py
│   │   ├── merge.py
│   │   └── utils.py
│   ├── comictaggerlib
│   │   ├── __pyinstaller
│   │   │   ├── __init__.py
│   │   │   ├── hook-comictaggerlib.py
│   │   │   └── hook-wordninja.py
│   │   ├── ctsettings
│   │   │   ├── __init__.py
│   │   │   ├── commandline.py
│   │   │   ├── file.py
│   │   │   ├── plugin.py
│   │   │   ├── plugin_finder.py
│   │   │   ├── settngs_namespace.py
│   │   │   └── types.py
│   │   ├── graphics
│   │   │   ├── __init__.py
│   │   │   ├── about.png
│   │   │   ├── app.png
│   │   │   ├── auto.png
│   │   │   ├── autotag.png
│   │   │   ├── browse.png
│   │   │   ├── clear.png
│   │   │   ├── down.png
│   │   │   ├── eye.svg
│   │   │   ├── graphics.qrc
│   │   │   ├── hidden.svg
│   │   │   ├── left.png
│   │   │   ├── longbox.png
│   │   │   ├── nocover.png
│   │   │   ├── open.png
│   │   │   ├── parse.png
│   │   │   ├── popup_bg.png
│   │   │   ├── resources.py
│   │   │   ├── right.png
│   │   │   ├── save.png
│   │   │   ├── search.png
│   │   │   ├── tags.png
│   │   │   └── up.png
│   │   ├── ui
│   │   │   ├── pyqttoast
│   │   │   │   ├── css
│   │   │   │   │   ├── __init__.py
│   │   │   │   │   ├── drop_shadow.css
│   │   │   │   │   └── toast.css
│   │   │   │   ├── hooks
│   │   │   │   │   ├── __init__.py
│   │   │   │   │   └── hook-pyqttoast.py
│   │   │   │   ├── icons
│   │   │   │   │   ├── __init__.py
│   │   │   │   │   ├── close.png
│   │   │   │   │   ├── error.png
│   │   │   │   │   ├── information.png
│   │   │   │   │   ├── success.png
│   │   │   │   │   └── warning.png
│   │   │   │   ├── .DS_Store
│   │   │   │   ├── __init__.py
│   │   │   │   ├── constants.py
│   │   │   │   ├── drop_shadow.py
│   │   │   │   ├── icon_utils.py
│   │   │   │   ├── LICENSE
│   │   │   │   ├── README.md
│   │   │   │   ├── toast.py
│   │   │   │   └── toast_enums.py
│   │   │   ├── __init__.py
│   │   │   ├── applicationlogwindow.ui
│   │   │   ├── autotagmatchwindow.ui
│   │   │   ├── autotagprogresswindow.ui
│   │   │   ├── autotagstartwindow.ui
│   │   │   ├── coverimagewidget.ui
│   │   │   ├── crediteditorwindow.ui
│   │   │   ├── customwidgets.py
│   │   │   ├── exportwindow.ui
│   │   │   ├── fileselectionlist.ui
│   │   │   ├── imagepopup.ui
│   │   │   ├── issueselectionwindow.ui
│   │   │   ├── logwindow.ui
│   │   │   ├── matchselectionwindow.ui
│   │   │   ├── pagebrowser.ui
│   │   │   ├── pagelisteditor.ui
│   │   │   ├── progresswindow.ui
│   │   │   ├── qtutils.py
│   │   │   ├── renamewindow.ui
│   │   │   ├── seriesselectionwindow.ui
│   │   │   ├── settingswindow.ui
│   │   │   ├── taggerwindow.ui
│   │   │   ├── talkeruigenerator.py
│   │   │   └── TemplateHelp.ui
│   │   ├── __init__.py
│   │   ├── __main__.py
│   │   ├── applicationlogwindow.py
│   │   ├── autotagmatchwindow.py
│   │   ├── autotagprogresswindow.py
│   │   ├── autotagstartwindow.py
│   │   ├── cbltransformer.py
│   │   ├── cli.py
│   │   ├── coverimagewidget.py
│   │   ├── crediteditorwindow.py
│   │   ├── defaults.py
│   │   ├── exportwindow.py
│   │   ├── filerenamer.py
│   │   ├── fileselectionlist.py
│   │   ├── gtinvalidator.py
│   │   ├── gui.py
│   │   ├── imagefetcher.py
│   │   ├── imagehasher.py
│   │   ├── imagepopup.py
│   │   ├── issueidentifier.py
│   │   ├── issueselectionwindow.py
│   │   ├── log.py
│   │   ├── logwindow.py
│   │   ├── main.py
│   │   ├── matchselectionwindow.py
│   │   ├── md.py
│   │   ├── optionalmsgdialog.py
│   │   ├── pagebrowser.py
│   │   ├── pagelisteditor.py
│   │   ├── pageloader.py
│   │   ├── pillow_plugins.py
│   │   ├── progresswindow.py
│   │   ├── quick_tag.py
│   │   ├── renamewindow.py
│   │   ├── resulttypes.py
│   │   ├── seriesselectionwindow.py
│   │   ├── settingswindow.py
│   │   ├── tag.py
│   │   ├── taggerwindow.py
│   │   └── versionchecker.py
│   ├── comictalker
│   │   ├── talkers
│   │   │   ├── __init__.py
│   │   │   └── comicvine.py
│   │   ├── vendor
│   │   │   ├── pyrate_limiter
│   │   │   │   ├── __init__.py
│   │   │   │   ├── bucket.py
│   │   │   │   ├── constants.py
│   │   │   │   ├── exceptions.py
│   │   │   │   ├── LICENSE
│   │   │   │   ├── limit_context_decorator.py
│   │   │   │   ├── limiter.py
│   │   │   │   ├── py.typed
│   │   │   │   ├── README.md
│   │   │   │   └── request_rate.py
│   │   │   └── __init__.py
│   │   ├── __init__.py
│   │   ├── comiccacher.py
│   │   ├── comictalker.py
│   │   └── talker_utils.py
│   ├── scripts
│   │   ├── find_dupes.py
│   │   ├── inventory.py
│   │   ├── make_links.py
│   │   ├── move2folder.py
│   │   ├── name_fixer.py
│   │   ├── README.txt
│   │   ├── remove_ads.py
│   │   ├── shrink.py
│   │   ├── validate_cover.py
│   │   └── xforms
│   ├── testing
│   │   ├── data
│   │   │   ├── Cory Doctorow's Futuristic Tales of the Here and Now #001 - Anda's Game (2007).cbz
│   │   │   └── fake_cbr.cbr
│   │   ├── __init__.py
│   │   ├── comicdata.py
│   │   ├── comicvine.py
│   │   └── filenames.py
│   ├── tests
│   │   ├── __init__.py
│   │   ├── autoimprint_test.py
│   │   ├── comicarchive_test.py
│   │   ├── comiccacher_test.py
│   │   ├── comicvinetalker_test.py
│   │   ├── conftest.py
│   │   ├── ctsettings_test.py
│   │   ├── filenameparser_test.py
│   │   ├── genericmetadata_test.py
│   │   ├── imagehasher_test.py
│   │   ├── integration_test.py
│   │   ├── issueidentifier_test.py
│   │   ├── issuestring_test.py
│   │   ├── pyqttoast_test.py
│   │   ├── rename_test.py
│   │   ├── tags_test.py
│   │   └── utils_test.py
│   ├── .mailmap
│   ├── .pre-commit-config.yaml
│   ├── AUTHORS
│   ├── CONTRIBUTING.md
│   ├── LICENSE
│   ├── pyproject.toml
│   ├── README.md
│   ├── README2.md
│   ├── release_notes.txt
│   ├── setup.cfg
│   ├── setup.py
│   └── todo.txt
└── mylar3-sanity
    ├── mylar3_sanity
    │   ├── __init__.py
    │   └── cli.py
    ├── LICENSE
    ├── Makefile
    ├── README.md
    └── requirements.txt
```
<!-- END DIR TREE -->
