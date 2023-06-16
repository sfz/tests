# SFZ Regression Test Suite

Created by René Ceballos at rgc:audio, initially distributed through the
[Cakewalk forum], updated by Plogue.
Shared as public domain documentation and software test suite
with authors permissions.

[Cakewalk forum]: http://forum.cakewalk.com/Dimension-Pro-sfz-v2-test-suite-1-m645298.aspx


## Generate xml and json versions

Automatically generate `.xml` versions of each `.sfz` file using the sfizz preprocessor tool:

    curl -LO https://github.com/studiorack/sfizz/releases/download/v1.1.1/sfizz-preprocessor-mac.zip
    unzip sfizz-preprocessor-mac.zip && rm sfizz-preprocessor-mac.zip
    IFS=$'\n'
    for file in $(find . -type f -name '*.sfz'); do ./sfizz_preprocessor "$file" --mode=xml > "${file%.*}.xml"; done

Automatically convert `.xml` files to `.json` using the yq tool:

    pip install yq
    for file in $(find . -type f -name '*.xml'); do cat "$file" | xq . > "${file%.*}.json"; done
