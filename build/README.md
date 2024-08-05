Execute `debuild -us -uc` in top level and move the resulting files from one level above to build/ : `mv ../fsed_* build/`
Sign the package with `debsigs --sign=origin -k KEY build/fsed_VERSION_all.deb`.
