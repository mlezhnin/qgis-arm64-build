# Build for QGIS on ARM64 docker container

Note: Make sure you provide enough RAM (12gb min.) to Docker while it's compiling QGIS. SIP is a memory hog and you will run into OOM errors if you don't otherwise change compiler flags.

IF you attempt building the image and have an OOM error, do not use that image. You will have to recompile QGIS for every container, which can take a long time (2hrs on M4 MacBook air).

Steps to build QGIS:

1. Clone QGIS
2. Replace the qgis.dockerfile and qgis3-ubuntu-qt6-build-deps.dockerfile in QGIS/.docker with the ones from this repo
3. CD QGIS/
4. docker build -f .docker/qgis3-ubuntu-qt6-build-deps.dockerfile -t my-qgis-deps:latest .
5. docker build -f .docker/qgis.dockerfile -t qgis-arm64 .
6. Then run with: docker run -it qgis-arm64 /bin/bash
