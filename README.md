## Build Scrips

```bash
-DUSE_Z3=OFF -DUSE_CVC4=OFF -DSOLC_LINK_STATIC=ON -DSOLC_STATIC_STDLIBS=ON
```
```sh
-DCMAKE_OSX_ARCHITECTURES=x86_64;arm64
```

```bash
echo "Genearting Prelrelease touchpoint for release tag..."
TZ=UTC git show --quiet --date="format-local:%Y.%-m.%-d" --format="ci.%cd" >prerelease.txt

mkdir -p build
cd build
echo "Starting source build...."

cmake .. -DCMAKE_BUILD_TYPE="${CMAKE_BUILD_TYPE:-Release}" $CMAKE_OPTIONS -G "Unix Makefiles"

make
